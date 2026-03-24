# Key Learnings

## 1. Numerical Schemes Matter

Using a centered scheme for advection caused non-physical oscillations (stripes). This highlighted the importance of selecting stable numerical methods.

## 2. Difference Between Physical and Numerical Diffusion

- Physical diffusion: controlled by diffusivity (D)
- Numerical diffusion: introduced by discretization

Understanding this distinction was critical to interpreting results.

## 3. Importance of Scaling in Visualization

Incorrect scaling initially made the blob invisible. Proper min/max values are essential for meaningful visualization.

## 4. Mesh Resolution Effects

Increasing grid resolution (128 → 512):

- Improved solution accuracy
- Reduced numerical errors
- Better captured gradients

## 5. Coupled Physics Understanding

This project demonstrated how:

- Advection transports the scalar
- Diffusion spreads it
- Reaction reduces it

All three processes interact simultaneously.

## 6. Debugging CFD Simulations

Several issues were encountered and resolved:

- Compilation errors due to missing includes
- Instability due to large time steps
- Incorrect field definitions (uf, Df)
- Visualization issues

This significantly improved debugging and solver-level understanding.
