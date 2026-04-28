# Simulation Logic

## Introduction

The purpose of this project is not only to run a CFD simulation, but to create a complete Reduced Order Modeling (ROM) workflow for flow around a circular cylinder.

To achieve this, the simulation follows a logical sequence where:

CFD Solution → Snapshot Generation → POD → Reduced Order Interpretation

Each stage depends on the previous one.

This document explains the complete simulation logic behind the Basilisk code (`cylinder.c`) and the POD post-processing script (`pod_cylinder.py`).

Understanding this logic is important because ROM is not just a Python script—it starts from how the CFD simulation itself is designed.

---

## High-Level Workflow

					The overall project logic follows:

					
					Define Physical Problem
						↓
					Create Computational Domain
						↓
					Apply Boundary Conditions
						↓
					Represent Cylinder Geometry
						↓
					Solve Navier–Stokes Equations
						↓
					Generate Time Snapshots
						↓
					Store Velocity Fields
						↓
					Build Snapshot Matrix
						↓
					Apply POD (SVD)
						↓
					Extract Dominant Modes
						↓
					Analyze Temporal Behavior
						↓
					Interpret Physics

This is the complete ROM pipeline.

---


## Step 1 — Define the Physical Problem

The first step is selecting the engineering problem:

2D incompressible laminar flow around a circular cylinder at:

			Re = 100

This case is chosen because it contains:
		 - boundary layer development
		 - flow separation
		 - wake formation
		 - transient flow structures
		 - vortex shedding tendency

It is simple enough to solve and complex enough for meaningful POD analysis.

--- 

## Step 2 — Create the Computational Domain

The simulation domain must be large enough so that:

		 - inlet flow develops naturally
		 - wake forms properly
		 - outlet does not artificially affect the solution

The domain is created using:
			
			size (L0);
			origin (-2.0, -4.0);
			init_grid (1 << 7);

This gives:
		 - upstream inlet region
		 - downstream wake region
		 - vertical spacing for wake development

A poor domain size would destroy the ROM quality later.

---


## Step 3 — Create Cylinder Geometry

Instead of using body-fitted mesh generation, Basilisk uses:

				embed.h

with:
		solid(cs, fs, sq(x) + sq(y) - sq(RADIUS));

This creates:
			 - circular embedded cylinder
			 - no complex meshing
			 - Cartesian adaptive mesh

This simplifies geometry handling significantly.

The cylinder becomes the source of:
			 - flow blockage
			 - pressure buildup
			 - boundary layer separation
			 - wake generation

which creates the physics POD will later analyze.

## Step 4 — Apply Boundary Conditions

Boundary conditions define how the fluid enters, interacts, and exits.

# Inlet

Uniform velocity enters:

		u.n[left] = dirichlet(U0);
		u.t[left] = dirichlet(0);

This creates the free-stream flow.

# Cylinder Wall

No-slip condition:
		u.n[embed] = dirichlet(0);
		u.t[embed] = dirichlet(0);

This creates:
		 - wall friction
		 - separation
		 - wake

This is the most important physical source of the project.

# Outlet

Pressure reference:
		p[right] = dirichlet(0);

This prevents pressure singularity and allows stable outflow. Without this, the solver may not advance.


---

## Step 5 — Break Perfect Symmetry

Initially, the simulation produced:

		 - almost steady flow
		 - one dominant POD mode

because the flow remained too symmetric.

To trigger unsteady wake behavior, manual perturbations were introduced as shown below

		u.y[] = 0.02*sin(2*pi*y/L0);
This creates small controlled perturbation, which helps trigger wake instability, vortex formation, oscillatory structures
Without perturbation, POD cannot extract vortex shedding because the CFD itself contains no strong oscillation. This is a major engineering lesson.


---

## Step 6 — Solve the Full Order Model (FOM)

Basilisk solves Incompressible Navier–Stokes Equations using:

		#include "navier-stokes/centered.h"

The solver advances in ime step by time step while enforcing:

			∇ · u = 0
			
through pressure correction. This is where pressure solver convergence, CFL stability, transient evolution
become important. This full simulation is called the Full Order Model (FOM) because it contains the complete physics.


---


## Step 7 — Generate Snapshots

ROM requires time-resolved velocity data. This is done using:

		event snapshot (t += 0.3)

which saves the velocity field periodically. To avoid startup noise:

			if (t >= 2)
			
is used.This means only physically meaningful flow is saved instead of unstable initial transients.

Each file stores:
		 - x
		 - y
		 - ux
		 - uy

These files become the input for POD. Without good snapshots, ROM becomes useless. No matter how good the Python script is.

---

## Step 8 — Build POD Matrix

The Python script reads all snapshot files:

		data = np.loadtxt(file)

and extracts:

		 - ux = data[:, 2]
		 - uy = data[:, 3]

Then combines them:

	snapshot = np.concatenate([ux, uy])

Each snapshot becomes one full-state vector These are stacked into:

		X = [x1 x2 x3 ... xn]

called the Snapshot Matrix. This is the mathematical input for POD.


---

## Step 9 — Handle Variable Snapshot Size

Because embedded boundaries create varying active cells. Not all snapshots had equal length. This caused:

		ValueError: setting an array element with a sequence

To fix this all files were trimmed to the minimum common size. This is a very practical ROM preprocessing step and reflects real engineering work.


---


## Step 10 — Apply POD Using SVD

POD is performed using:

		U, S, VT = np.linalg.svd(X, full_matrices=False)

This gives:

		X = UΣVᵀ

where:

		U = spatial modes
		Σ = singular values
		Vᵀ = temporal coefficients

This step answers:"What structures dominate the flow?". Instead of just visualizing velocity contours. This is where CFD becomes data-driven engineering.

---


## Step 11 — Analyze Modal Energy

Using:

		energy = S**2 / np.sum(S**2)

we compute:"how much energy each mode carries". This tells us whether the flow is steady dominated or oscillation dominated. In this project Mode 1 captured almost all energy which means mean wake structure dominated. This is a physically meaningful result.


---

## Step 12 — Analyze Temporal Behavior

Temporal coefficients are computed using:

		A = np.diag(S) @ VT

These show how each mode evolves with time Expected for vortex shedding:

		 - sine wave behavior
		 - mode pairing
		 - periodic oscillation

Observed:
		 - dominant steady mode
		 - weak higher modes

This showed that strong periodic shedding was weak for the selected computational setup.

---

## Step 13 — Frequency Analysis

FFT was added using:

		fft_vals = np.abs(fft(signal))

to estimate:
		 - dominant frequency
		 - Strouhal number

Although the final setup remained steady-dominant, the frequency extraction pipeline was successfully established for future higher-Re studies.


---

## Final Logic Summary

The project logic is:

			Good CFD → Good Snapshots → Good POD → Meaningful ROM

not

				Bad CFD → Magic Python → Good ROM

This is the most important lesson. ROM quality always depends on CFD quality. POD does not create physics. It only compresses the physics already present in the simulation. This project successfully established the full logic from Running CFD to Understanding and Compressing CFD Physics

























