# Governing Equations — Lid-Driven Cavity Flow

## Introduction

The flow inside the lid-driven cavity is governed by the incompressible Navier–Stokes equations, which describe conservation of mass and momentum for a Newtonian fluid.

These equations form the mathematical foundation of the CFD simulation performed in this project.

---

## Continuity Equation (Mass Conservation)

For incompressible flow:

∇ · u = 0

Where:
- u = (u_x, u_y) is the velocity vector

### Physical Meaning
- Ensures mass conservation
- No accumulation of mass within the domain
- Flow entering a control volume equals flow leaving it

---

## Momentum Equation (Navier–Stokes)

∂u/∂t + (u · ∇)u = - (1/ρ) ∇p + ν ∇²u

Where:
- u → velocity vector
- p → pressure
- ρ → density
- ν → kinematic viscosity

---

## Term-by-Term Explanation

### 1. Transient Term
∂u/∂t

- Represents time-dependent changes in velocity
- Important during flow startup and evolution

---

### 2. Convective Term
(u · ∇)u

- Represents transport of momentum by the fluid
- Introduces nonlinearity into the equations

---

### 3. Pressure Gradient Term
-∇p

- Drives the flow
- Adjusts to maintain incompressibility

---

### 4. Viscous (Diffusion) Term
ν ∇²u

- Represents momentum diffusion due to viscosity
- Smooths velocity gradients
- Dominant in laminar flows

---

## Reynolds Number

Re = (U L) / ν

Where:
- U → lid velocity
- L → cavity length
- ν → kinematic viscosity

### In This Project:
Re = 100

### Interpretation:
- Flow is laminar
- Viscous effects dominate
- System evolves to steady state

---

## Boundary Conditions

### Top Wall (Moving Lid)
u_x = U
u_y = 0

- Drives the flow inside the cavity

---

### Bottom and Side Walls (No-slip)
u_x = 0
u_y = 0

- Fluid sticks to the wall

---

## Pressure Treatment

- Pressure is not explicitly prescribed
- It is computed to enforce ∇ · u = 0
- Ensures incompressibility constraint is satisfied

---

## Assumptions

- Incompressible flow
- Newtonian fluid
- Constant viscosity
- No body forces (gravity neglected)
- Two-dimensional domain

---

## Connection to Reduced Order Modeling (ROM)

The governing equations define the full-order system:

u(x, y, t)

ROM approximates this as:

u(x, y, t) ≈ Σ [ a_i(t) · φ_i(x, y) ]

Where:
- φ_i(x, y) → spatial modes
- a_i(t) → temporal coefficients
- i = 1 to r, where r << N

---

## Key Insight

Instead of solving Navier–Stokes equations at all grid points:

- Solve for a small number of modal coefficients
- Capture dominant flow physics efficiently

---

## Summary

- Navier–Stokes equations govern fluid motion
- Continuity ensures mass conservation
- Momentum equation balances forces
- Reynolds number defines flow regime
- Boundary conditions drive cavity circulation

These equations form the foundation of the high-fidelity simulation used to build the reduced order model.
