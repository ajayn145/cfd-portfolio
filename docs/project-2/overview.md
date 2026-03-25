# Ahmed Body Aerodynamics Study (OpenFOAM)

## Problem Statement
The objective of this project is to simulate external flow over a 25° Ahmed body and estimate the drag coefficient.

The Ahmed body is a simplified car-like geometry widely used in automotive aerodynamics to study flow separation and wake behavior.

---

## Engineering Relevance
Understanding flow over bluff bodies is critical in automotive design because:

- Drag directly affects fuel efficiency
- Wake structure influences vehicle stability
- Pressure distribution determines aerodynamic performance

The Ahmed body provides a benchmark case for validating CFD setups.

---

## What Was Done
In this project:

- A transient CFD simulation was set up using OpenFOAM
- The case was adapted from the `pitzDaily` tutorial
- The PIMPLE algorithm was used for pressure-velocity coupling
- The k-omega SST turbulence model was applied
- The simulation was run up to 5 seconds to allow wake development
- Forces were computed using OpenFOAM function objects

---

## Key Challenges
During the setup and execution, multiple issues were encountered:

- PIMPLE dictionary undefined
- Missing OmegaFinal entry
- wallDist not defined
- Missing div(phi,omega) term
- meshWave typo in fvSchemes
- Courant number instability
- forces.dat not generated
- Uncertainty in frontal area for Cd calculation

These challenges required debugging at both solver and physics levels.

---

## Flow Behavior Observed

- Flow separates at the slanted rear surface
- A recirculation region forms behind the body
- The wake remains unsteady
- Drag force oscillates around a mean value

Even after 5 seconds, the flow remained transient but reached a statistically steady state.

---

## Results (Preliminary)
- Drag force ≈ 32 N
- Estimated Cd ≈ 0.75

Expected Cd ≈ 0.3 (literature value)

---

## Initial Analysis
The higher drag coefficient is attributed to:

- Coarse mesh (~40k tetrahedral cells)
- Poor resolution of wake region
- Lack of near-wall refinement

The solver setup is stable, but the solution is not yet grid-independent.

---

## Engineering Log
The complete step-by-step development process is documented below:

<iframe src="https://nbviewer.org/github/ajayn145/AhmedBody_OpenFOAM12/blob/main/notebooks/01_Engineering_Log.ipynb"
width="100%" height="900px"></iframe>
