# Governing Equations

## What Equations Are Being Solved?

This project solves a coupled reactive flow problem involving:

* Species transport
* Heat transfer
* Fluid flow
* Buoyancy

---

## 1. Species Transport Equation

The governing equation is:

```
dC/dt + div(u*C) = D * laplacian(C) - R
```

Where:

* C → species concentration
* u → velocity field
* D → diffusion coefficient
* R → reaction rate

---

### Physical Meaning of Each Term

* dC/dt → change of concentration with time
* div(u*C) → transport due to fluid motion (advection)
* D * laplacian(C) → spreading due to diffusion
* -R → consumption of species due to reaction

---

## 2. Temperature Equation

The temperature evolution is given by:

```
dT/dt + div(u*T) = kappa * laplacian(T) + Q * R
```

Where:

* T → temperature
* kappa → thermal diffusivity
* Q → heat release coefficient

---

### Interpretation

* Temperature spreads due to diffusion
* Reaction generates heat
* Fluid flow transports heat

---

## 3. Reaction Model

The reaction rate is defined as:

```
R = k0 * C * exp(-Ea / T)
```

Where:

* k0 → reaction constant
* Ea → activation energy
* T → temperature

---

### Key Insight

* Low T → slow reaction
* High T → very fast reaction

This leads to **thermal runaway behavior**.

---

## 4. Momentum Equation (Navier–Stokes)

The velocity field follows:

```
du/dt + (u · grad)u = -grad(p) + nu * laplacian(u) + buoyancy
```

And:

```
div(u) = 0
```

Where:

* u → velocity
* p → pressure
* nu → kinematic viscosity

---

## 5. Buoyancy Model

Buoyancy force is modeled as:

```
buoyancy = T (in vertical direction)
```

---

### Interpretation

* Hot fluid rises
* Cold fluid sinks

This creates **natural convection (plume formation)**.

---

## 6. Coupling Between Equations

The system is strongly coupled:

* Reaction consumes species → increases temperature
* Temperature increases → accelerates reaction
* Temperature generates buoyancy → induces flow
* Flow transports species and temperature

---

### Feedback Loop

```
Temperature ↑ → Reaction ↑ → Temperature ↑
```

---

## 7. Rayleigh Number (Physical Insight)

Rayleigh number is estimated as:

```
Ra = T / (nu * kappa)
```

---

### Meaning

* High Ra → strong convection
* Low Ra → stable diffusion-dominated flow

---

## 8. Boundary Conditions

* Velocity: no-slip (u = 0 at all walls)
* Scalars (C, T): initialized as Gaussian distribution
* No inflow or outflow

---

## Summary

This is a nonlinear coupled system where:

* Diffusion stabilizes
* Reaction destabilizes
* Buoyancy redistributes energy

This interaction produces complex plume structures similar to real engineering systems.

