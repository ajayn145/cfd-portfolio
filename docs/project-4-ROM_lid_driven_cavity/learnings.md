# Key Learnings

This project provided significant insights into both CFD fundamentals and practical solver usage in OpenFOAM.

---

## 1. Solver Understanding (PIMPLE Algorithm)

- Learned how pressure-velocity coupling works in transient simulations
- Understood the role of outer (PIMPLE) and inner (PISO/SIMPLE) loops
- Realized that incorrect solver settings can lead to instability or divergence

👉 Key Insight:
Solver configuration is not just syntax — it directly affects physical accuracy and stability

---

## 2. Turbulence Modeling (k-omega SST)

- Understood why k-omega SST is preferred for external aerodynamics
- Learned that turbulence models require additional variables (k, omega)
- Observed sensitivity of results to turbulence modeling

👉 Key Insight:
Turbulence models are critical for predicting separation and wake behavior

---

## 3. Importance of Wall Distance (wallDist)

- Learned that wall distance is required for near-wall turbulence treatment
- Understood how wall modeling affects boundary layer prediction

👉 Key Insight:
Geometry-related quantities (like wall distance) are essential for turbulence closure

---

## 4. Numerical Stability (Courant Number)

- Observed simulation failure due to high Courant number
- Learned to control time step using:
  - deltaT
  - adjustTimeStep
  - maxCo

👉 Key Insight:
Numerical stability must be actively controlled in transient simulations

---

## 5. Discretization Schemes Matter

- Learned that missing schemes (e.g., div(phi,omega)) can crash the solver
- Understood that different schemes affect numerical diffusion and accuracy

👉 Key Insight:
Discretization is not just configuration — it influences solution quality

---

## 6. Function Objects and Post-Processing

- Learned how OpenFOAM computes forces using function objects
- Understood the importance of correct placement (`system/functions`)

👉 Key Insight:
Post-processing must be set up correctly during simulation, not after

---

## 7. Transient vs Steady Behavior

- Observed that flow remained transient even after 5 seconds
- Learned concept of **statistically steady state**

👉 Key Insight:
Unsteady flows cannot always be solved using steady-state assumptions

---

## 8. Mesh Quality and Accuracy

- Realized that coarse mesh leads to inaccurate drag prediction
- Observed strong sensitivity of results to mesh resolution

👉 Key Insight:
Mesh quality is one of the most critical factors in CFD accuracy

---

## 9. Drag Coefficient Sensitivity

- Learned that Cd depends on:
  - Reference area
  - Flow velocity
  - Mesh resolution
  - Wake prediction

👉 Key Insight:
Even small mistakes in reference parameters can lead to large errors

---

## 10. Debugging Skills in OpenFOAM

- Learned to interpret error messages
- Fixed issues related to:
  - solver dictionaries
  - turbulence setup
  - numerical schemes

👉 Key Insight:
CFD requires strong debugging and problem-solving skills, not just theory

---

## Final Reflection

This project transformed my understanding of CFD from:

- Running tutorials  
→ to  
- Building, debugging, and analyzing a full simulation workflow

It highlighted the importance of:

- Physics understanding  
- Numerical methods  
- Solver configuration  
- Engineering judgment
