# Implementation

The solver is implemented using Basilisk C.

Key steps:

- Initialize scalar field (Gaussian blob)
- Define velocity field
- Solve advection using Basilisk's advection module
- Solve diffusion using diffusion operator
- Apply reaction term
