# NUMERICAL METHOD

## Why Numerical Method?

The governing equations (Navier–Stokes) cannot be solved exactly for this case.

So we solve them numerically by:

- Dividing the domain into small cells  
- Solving equations step-by-step in time  

---

## 1. Discretization of the Domain

The domain is divided into small square cells.

Each cell stores:

- Velocity (u)
- Pressure (p)

This allows us to track fluid motion locally.

---

## 2. Finite Volume Method (FVM)

The simulation uses the **Finite Volume Method**.

### Core idea:

Change inside a cell =
Incoming flux − Outgoing flux

---

### Why FVM?

- Conserves mass and momentum  
- Stable for fluid simulations  
- Widely used in CFD  

---

## 3. Time Stepping

The simulation progresses in small time steps:

DT = 5e-4

At each time step:

- Velocity is updated  
- Pressure is corrected  
- Flow evolves  

---

## 4. Advection (Transport of Velocity)

Term:

(u · ∇)u

### Meaning:

- Fluid carries its own motion  
- Responsible for movement of vortices  

---

## 5. Diffusion (Viscous Effect)

Term:

ν ∇²u

### Meaning:

- Smooths velocity differences  
- Reduces sharp gradients  

---

### Important Insight:

- Low viscosity → sharp vortices  
- High viscosity → diffused flow  

---

## 6. Pressure–Velocity Coupling

Condition:

∇ · u = 0

### Meaning:

- Fluid must remain incompressible  

---

### How it is enforced:

- Solve pressure equation  
- Correct velocity field  

---

## 7. Solver Used

The simulation uses:

- Basilisk centered Navier–Stokes solver  
- Multigrid method for pressure  

---

### Why this solver?

- Efficient  
- Stable  
- Suitable for incompressible flows  

---

## 8. Overall Algorithm

At each time step:

1. Compute advection  
2. Apply diffusion  
3. Solve pressure equation  
4. Correct velocity  
5. Update flow field  
6. Save results  

---

## Final Understanding

The numerical method converts complex fluid equations into small, manageable calculations performed at each grid cell and time step.

---

## One-Line Summary

The flow is simulated by solving conservation equations step-by-step using the Finite Volume Method while maintaining incompressibility.

---
