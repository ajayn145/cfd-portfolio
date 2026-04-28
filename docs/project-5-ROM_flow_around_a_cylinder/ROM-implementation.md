# ROM Implementation

## Introduction

The main objective of this project is not only to perform a CFD simulation of flow around a circular cylinder, but also to develop a Reduced Order Model (ROM) using Proper Orthogonal Decomposition (POD).

A full CFD simulation contains thousands of spatial degrees of freedom and requires significant computational cost. ROM helps reduce this complexity by identifying the dominant coherent structures of the flow and representing the system using only a few energetic modes.

The complete workflow followed in this project is:

CFD Simulation → Snapshot Generation → POD → Mode Extraction → Temporal Analysis → Physical Interpretation

This creates a full CFD-to-ROM pipeline.

---

## Step 1 — Full Order Model (FOM)

The first step is solving the full incompressible Navier–Stokes equations using Basilisk.

The following Basilisk modules were used:

- navier-stokes/centered.h
- embed.h

The centered solver was used for pressure–velocity coupling and the embedded boundary method was used to represent the circular cylinder inside a Cartesian mesh.

The simulation was performed for:

- Reynolds number: Re = 100
- 2D incompressible laminar flow
- Uniform inlet velocity
- Circular cylinder with no-slip wall boundary

This full CFD simulation is called the:

Full Order Model (FOM)

because it contains the complete physical system.

---

## Step 2 — Domain and Geometry Setup

The computational domain was created using:

		size (L0);
		origin (-2.0, -4.0);

This creates:
 - sufficiently large wake region
 - upstream inlet region
 - downstream outlet development zone

The cylinder geometry was created using:

		solid(cs, fs, sq(x) + sq(y) - sq(RADIUS));

where:
		cs = cell fraction
		fs = face fraction

This avoids complex body-fitted meshing and uses Basilisk’s embedded boundary method.

---

## Step 3 — Boundary Conditions

The following boundary conditions were applied:

		Inlet
		u.n[left] = dirichlet(U0);
		u.t[left] = dirichlet(0);

This creates a uniform incoming free-stream velocity.

		Cylinder Surface
		u.n[embed] = dirichlet(0);
		u.t[embed] = dirichlet(0);

This imposes the no-slip condition and generates:
 - boundary layer formation
 - flow separation
 - wake development

Outlet:-
		p[right] = dirichlet(0);

This provides the pressure reference and allows flow to leave the domain naturally.


---

## Step 4 — Symmetry Breaking Perturbation

Initially, the flow remained too symmetric and POD showed only one dominant steady mode.

To trigger wake instability and vortex shedding, a small perturbation was introduced:

		u.y[] = 0.02*sin(2*pi*y/L0);

This creates a small vertical disturbance and helps break perfect symmetry.

This step is extremely important because POD cannot detect oscillatory modes if the CFD simulation itself remains perfectly steady. This was one of the most important engineering lessons of the project.

---


## Step 5 — Snapshot Generation

The most important step for POD is generating transient velocity snapshots.

Snapshots were saved using:

		event snapshot (t += 0.3)

and only after initial transient development:

		if (t >= 2)

This avoids collecting startup noise and focuses on meaningful wake behavior.

Each snapshot file stored:

		x coordinate
		y coordinate
		x-velocity component (ux)
		y-velocity component (uy)

A total of 73 snapshot files were generated for POD analysis. This created the dataset for Reduced Order Modeling.

---


## Step 6 — Python POD Preprocessing

The snapshot files were processed using Python with:

		NumPy
		Matplotlib
		SciPy

Each file was read using:

		data = np.loadtxt(file)

The velocity field was extracted as:

		ux = data[:, 2]
		uy = data[:, 3]

and combined as:

		snapshot = np.concatenate([ux, uy])

This creates one full-state vector for each time step.

---


## Step 7 — Handling Variable Snapshot Size

Because embedded boundary simulations may produce slightly different active cell counts, snapshot sizes were not always identical. This caused:

		ValueError: setting an array element with a sequence

To fix this, all snapshots were trimmed to the minimum common size:

		min_points = min(len(data))
		data = data[:min_points, :]

This is a practical ROM preprocessing step and reflects real engineering workflow rather than ideal textbook examples.

Final POD matrix size became (32768, 73)
where:
		rows = spatial degrees of freedom
		columns = number of snapshots


---


## Step 8 — POD Using Singular Value Decomposition

The snapshot matrix was written as:

		X = [x1 x2 x3 ... xn]

where each column is one velocity field snapshot.

Singular Value Decomposition was then applied:

		U, S, VT = np.linalg.svd(X, full_matrices=False)

which gives:

		X = UΣVᵀ

where:
		U = spatial POD modes
		Σ = singular values
		Vᵀ = temporal coefficients

This is the mathematical core of the ROM process.

---

## Step 9 — Modal Energy Analysis

The energy contribution of each mode was computed using:

		energy = S**2 / np.sum(S**2)

This helps answer: "Which flow structures are most important?"

The final result showed:

		Mode 1 captured more than 99% of total energy
		higher modes were very weak

This indicates that Mean flow dominated over oscillatory vortex shedding. This is a physically meaningful ROM conclusion.


---


## Step 10 — Temporal Coefficient Analysis

The temporal coefficients were computed using:

		A = np.diag(S) @ VT

These coefficients show how each POD mode evolves with time.

For classical vortex shedding cases, one expects:
		 - sinusoidal temporal behavior
		 - paired POD modes
		 - oscillatory wake structures

In this project:
		Mode 1 remained strongly dominant
		higher modes showed weak fluctuations

This confirmed that the flow was largely steady-dominant.

---


## Step 11 — Frequency Analysis (FFT)

To identify dominant oscillation frequency, Fast Fourier Transform (FFT) was applied:

		fft_vals = np.abs(fft(signal))

This helps estimate:
 - dominant shedding frequency
 - Strouhal number

Although strong oscillatory shedding was not dominant in this setup, the workflow for frequency extraction was successfully established. This is important for future higher-Reynolds-number studies.

---

## Final ROM Interpretation

The complete workflow proved:

			CFD → Data → Physics Compression

Instead of repeatedly solving the full Navier–Stokes equations, the system can now be represented using:
		
		    Few dominant modes + temporal coefficients

This is the core philosophy of Reduced Order Modeling. The most important learning was that ROM quality depends directly on CFD quality. If the CFD simulation does not contain strong transient physics, POD will naturally produce dominant steady modes. This project successfully established a practical and industry-relevant ROM workflow using Basilisk and Python.










init_grid (1 << 7);
