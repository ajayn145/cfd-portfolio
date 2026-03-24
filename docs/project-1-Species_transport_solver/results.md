# Results

## Simulation Video

<video controls width="600">
  <source src="/cfd-portfolio/assets/C.mp4" type="video/mp4">
</video>

## Result Analysis
The simulation captures the expected physical behavior of a reacting scalar transport problem.

### Observed Behavior
- The scalar field moves in the direction of the velocity field (advection)
- The concentration spreads over time (diffusion)
- The magnitude of the scalar decreases gradually (reaction)

---

### Effect of Physical Parameters

#### Diffusion Coefficient (D)
- Higher values → faster spreading
- Lower values → sharper concentration profile

#### Reaction Rate (k)
- Higher values → faster decay of scalar
- Lower values → longer persistence of the blob

---

### Effect of Numerical Parameters

#### Grid Resolution
- Higher resolution (512) → better shape preservation
- Lower resolution → increased numerical diffusion

#### Time Step (Δt)
- Smaller time step → stable and accurate solution
- Larger time step → potential instability

---

### Validation
The results are consistent with theoretical expectations of the species transport equation:

- Transport follows flow direction
- Diffusion smooths gradients
- Reaction reduces concentration

This confirms the correctness of the numerical implementation.
