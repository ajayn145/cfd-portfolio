# Numerical Method

## Governing Equation

∂C/∂t + ∇·(uC) = D∇²C − kC

## Discretization

- Spatial discretization: Finite-volume (Basilisk)
- Time integration: Explicit time stepping

## Advection Scheme

Initially, a centered advection scheme was used, which resulted in:

- Non-physical oscillations
- Stripe-like artifacts in the solution

This behavior is due to numerical dispersion.

The issue was resolved by switching to a more stable advection formulation using Basilisk’s advection module, which introduces numerical damping and ensures stability.

## Diffusion

Diffusion is solved using an implicit solver:

- Improves stability for small grid sizes
- Handles steep gradients effectively

## Reaction

A first-order decay model is implemented:

C_new = C / (1 + k·dt)

## Stability Considerations

- Time step (DT) was reduced to maintain stability
- Grid resolution increased to improve accuracy
- Proper scaling of visualization ensured correct interpretation
