# ROM for Lid Driven Cavity (Basilisk)

## Problem Statement
The objective of this project is to develop a Reduced Order Model (ROM) for a 2D incompressible lid-driven cavity flow.

Instead of solving the full Navier–Stokes equations at every grid point, the goal is to extract dominant flow structures and represent the system using a reduced number of variables.

This is achieved using Proper Orthogonal Decomposition applied to high-fidelity CFD data generated using Basilisk

---

## Engineering Relevance
High-fidelity CFD simulations are computationally expensive and not suitable for:

 - Real-time simulations
 - Optimization loops
 - Digital twin applications
 - Control systems

Reduced Order Modeling addresses this by:

 - Compressing large CFD datasets
 - Identifying dominant flow physics
 - Enabling fast approximate solutions

ROM is widely used in:

 - Automotive aerodynamics
 - Thermal management systems
 - Flow control and optimization
 - Machine learning-based CFD
---

## What Was Done
In this project:

 - A transient CFD simulation of lid-driven cavity flow was performed using Basilisk
 - The domain was discretized using a 64 × 64 Cartesian grid
 - Reynolds number was set to 100 (laminar regime)
 - Velocity field snapshots were exported at regular time intervals

Post-processing steps:

 - Velocity fields ((u_x, u_y)) were flattened into vectors
 - A snapshot matrix was constructed from all time steps
 - POD was applied using Singular Value Decomposition (SVD)
 - Dominant modes and their energy contributions were extracted
 - Flow reconstruction was performed using a reduced number of modes

---

## Key Challenges
During the development, several technical issues were encountered:

 - Handling viscosity field definition (mu) in Basilisk
 - Conflict between constant and variable field representations
 - OpenGL dependency errors due to view.h
 - Ensuring consistent grid structure across all snapshots
 - Converting unstructured CFD output into matrix form for POD
 - Understanding physical meaning of POD modes and coefficients

These required debugging at both solver and data-processing levels.

---

## Flow Behavior Observed

 - The flow is driven by the motion of the top lid
 - A primary vortex forms at the center of the cavity
 - Weak secondary recirculation regions appear near corners
 - Initial transient behavior is observed
 - The flow eventually reaches a steady state

Temporal analysis showed:

 - Dominant mode stabilizes over time
 - Higher modes decay rapidly
---

## Results (Preliminary)
Total snapshots: 101
Degrees of freedom: 8192
Energy Distribution:
 - Mode 1: 98.43%
 - Mode 2: 1.38%
 - Mode 3: 0.15%
Reconstruction:
 - Using 5 modes → error ≈ 0.003859

---

## Initial Analysis
The results indicate that:

 - The flow is highly low-dimensional
 - A single dominant structure (primary vortex) governs the system
 - Higher modes represent transient corrections
 - The system quickly converges to steady state

This explains why:

 - POD captures most energy in the first mode
 - Temporal coefficients stabilize over time
 
---

## Limitations
 - Flow is steady → lacks dynamic richness
 - No oscillatory behavior (no vortex shedding)
 - Limited scope for predictive ROM modeling

---

## Conclusion

This project demonstrates that:

 - Complex CFD systems can be reduced to a small set of dominant modes
 - POD effectively separates spatial and temporal behavior
 - Lid-driven cavity flow is strongly low-dimensional

The ROM developed is accurate for reconstruction but limited in predictive capability due to steady-state nature of the flow.

---


## Future Direction

To extend this work:

 - Apply ROM to unsteady flows (e.g., flow past cylinder)
 - Capture oscillatory dynamics and vortex shedding
 - Develop predictive ROM using temporal coefficients
 - Integrate machine learning models for time evolution

---




























