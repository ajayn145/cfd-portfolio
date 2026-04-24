# Results — Reduced Order Modeling of Lid-Driven Cavity Flow

## Snapshot Data

- Total snapshots generated: 101  
- Grid resolution: 64 × 64  
- Degrees of freedom: 8192 (u_x and u_y combined)  

The dataset captures the transient evolution of the flow from rest to steady state.

---

## Energy Distribution of POD Modes

The energy captured by each mode is computed using singular values obtained from SVD.

### Observed Distribution:

- Mode 1: 98.43%  
- Mode 2: 1.38%  
- Mode 3: 0.15%  

---

## Interpretation

- The first mode dominates the system  
- The flow is highly low-dimensional  
- Most of the flow physics is captured by a single structure  

This indicates that the lid-driven cavity flow at Re = 100 is governed by a dominant coherent vortex.

---

## Flow Reconstruction

The flow field was reconstructed using a reduced number of modes.

### Reconstruction Setup:
- Number of modes used: 5  

### Error:
- Relative reconstruction error ≈ 0.003859  

---

## Interpretation

- High accuracy achieved with very few modes  
- Minimal loss of information despite strong dimensionality reduction  
- Confirms effectiveness of POD for this flow regime  

---

## Spatial Modes

<p align="center">
  <img src="../figures/mode1_ux.png" width="45%">
  <img src="../figures/mode1_uy.png" width="45%">
</p>

The first POD mode represents the dominant flow structure.

### Observations:

- u_x mode shows strong shear near the moving lid  
- u_y mode captures vertical recirculation  
- The structure corresponds to the primary vortex inside the cavity  

Higher modes represent minor corrections and localized effects.

---

## Temporal Coefficients

<p align="center">
  <img src="../images/cavity/temporal_coeffs.png" width="60%">
</p>

Temporal coefficients describe how each mode evolves over time.

### Observations:

- Mode 1 increases and stabilizes  
- Modes 2 and 3 decay to zero  

---

## Interpretation

- Flow starts from rest and develops over time  
- System reaches steady state  
- No sustained oscillations are present  

---

## Key Insight

The flow can be effectively represented as:

- One dominant mode (primary vortex)  
- Small transient corrections  

This confirms that the system is strongly low-dimensional.

---

## Limitations of Results

- Flow is steady and lacks dynamic richness  
- Temporal behavior is not oscillatory  
- Predictive ROM is limited in this case  

---

## Overall Conclusion

- POD successfully reduces system dimensionality  
- A small number of modes capture most of the physics  
- Lid-driven cavity flow at low Reynolds number is highly compressible in modal space  

This validates the use of POD for efficient representation of laminar flow systems.

---
