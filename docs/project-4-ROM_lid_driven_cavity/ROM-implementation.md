# Theoretical Insights — Reduced Order Modeling (ROM)

## What is Reduced Order Modeling?

Reduced Order Modeling (ROM) is a technique used to simplify high-dimensional systems (like CFD simulations) into a much lower-dimensional representation while preserving the dominant physical behavior.

Instead of solving the governing equations at every grid point, ROM approximates the system using a small number of basis functions (modes).

---

## Full Order Model vs Reduced Order Model

### Full Order Model (FOM)
- Solves Navier–Stokes equations on all grid points
- High accuracy
- Very expensive computationally
- Degrees of freedom (DOF): ~10³–10⁷+

### Reduced Order Model (ROM)
- Represents solution using a few modes
- Much faster computation
- Slight loss of accuracy (controlled)
- Degrees of freedom: ~2–50

---

## Core Idea of ROM

A flow field:

u(x, y, t)

is approximated as:

u(x, y, t) ≈ Σ [ a_i(t) · φ_i(x, y) ]

Where:
- φ_i(x, y) → spatial modes (basis functions)
- a_i(t) → temporal coefficients
- i = 1 to r, where r << N

---

## Proper Orthogonal Decomposition (POD)

POD is the most widely used method for ROM in fluid mechanics.

### Objective:
Find an optimal set of orthogonal basis functions that capture maximum energy (variance) of the system.

---

## Snapshot Method

Instead of solving eigenvalue problems directly, POD uses simulation data:

1. Run CFD simulation  
2. Collect snapshots at different time steps  
3. Construct snapshot matrix:

X = [x₁ x₂ x₃ ... xₙ]

Where each column is a flow field

---

## Singular Value Decomposition (SVD)

The snapshot matrix is decomposed as:

X = U Σ Vᵀ

Where:
- U → spatial modes
- Σ → singular values (energy content)
- Vᵀ → temporal coefficients

---

## Energy Content of Modes

Energy captured by each mode:

E_i = σ_i² / Σ(σ_j²)

Modes are ranked:

Mode 1 > Mode 2 > Mode 3 > ...

---

## Mode Truncation

Instead of using all modes:

- Keep only first r modes
- Discard low-energy modes

This gives:

X ≈ U_r Σ_r V_rᵀ

---

## Physical Meaning of POD Modes

- Mode 1 → dominant flow structure (e.g., main vortex)
- Mode 2+ → corrections / secondary features
- Higher modes → noise or fine-scale structures

---

## Temporal Coefficients

a_i(t) represent how each mode evolves over time.

- Steady flow → coefficients become constant
- Unsteady flow → coefficients oscillate

---

## Types of ROM

### 1. Projection-Based ROM
- Uses governing equations
- Applies Galerkin projection
- Physically interpretable

### 2. Data-Driven ROM
- Uses simulation or experimental data
- No direct use of governing equations
- Often combined with machine learning

---

## Advantages of ROM

- Significant reduction in computation time
- Enables real-time simulation
- Useful for optimization and control
- Easy integration with ML models

---

## Limitations of ROM

- Accuracy depends on quality of snapshots
- Cannot capture unseen physics
- Poor performance for highly nonlinear/turbulent flows (if not trained properly)
- Mode truncation introduces approximation error

---

## When ROM Works Best

- Systems with dominant coherent structures
- Low to moderate Reynolds number flows
- Flows with repeating patterns (periodic or quasi-steady)

---

## When ROM Struggles

- Highly turbulent flows
- Strongly chaotic systems
- Flows with sudden changes (shock, separation onset)

---

## Connection to CFD

CFD provides:

- High-fidelity data (snapshots)

ROM provides:

- Compressed representation of that data

Together:

CFD → Data → ROM → Fast prediction

---

## Key Insight

ROM does not "solve" the physics again.

Instead, it learns:

> "What are the most important patterns in the flow, and how do they evolve?"

---

## Summary

- ROM reduces system dimensionality
- POD extracts dominant flow structures
- SVD provides mathematical decomposition
- Only a few modes are needed to represent complex flows
- Enables fast and efficient simulation

---

## Final Takeaway

A complex CFD solution with thousands of variables can often be represented using just a few dominant modes without significant loss of accuracy.
