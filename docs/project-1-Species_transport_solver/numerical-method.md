# Numerical Method

## Overview

This section explains how the governing species transport equation is solved numerically.

The equation:

`∂C/∂t + ∇·(uC) = D∇²C − kC`

is solved using a finite-volume approach with time-stepping.

---

## Discretization Approach

### Finite Volume Method (FVM)

The computational domain is divided into small control volumes (cells).

**Why this method?**
- Ensures conservation of mass and species
- Widely used in industrial CFD solvers

**Concept:**
Each cell stores an average value of concentration (C), and fluxes across cell faces determine how C changes.

---

## Time Integration

### Explicit Time Stepping

The solution is advanced in time using small time steps (Δt).

**Why used here?**
- Simple to implement
- Easy to understand for transient problems

**Limitation:**
- Requires small time step for stability

---

## Advection Term

### Equation Term:
`∇·(uC)`

### Numerical Treatment:

- Solved using Basilisk’s built-in `advection()` function
- Uses a stable flux-based scheme

**Why this is important:**
Initially, a naive or centered approach caused:
- Non-physical oscillations
- Stripe-like artifacts

Switching to a proper advection scheme:
- Eliminated oscillations
- Ensured stable transport

---

## Diffusion Term

### Equation Term:
`D∇²C`

### Numerical Treatment:

- Solved using Basilisk’s `diffusion()` function
- Uses an implicit multigrid solver

**Why implicit?**
- Stable even for larger time steps
- Efficient for solving diffusion equations

---

## Reaction Term

### Equation Term:
`−kC`

### Numerical Treatment:

```text
C_new = C / (1 + k·dt)
