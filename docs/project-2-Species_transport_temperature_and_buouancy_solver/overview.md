# Project 2: Reactive Species Transport with Buoyancy (Basilisk)

## Overview

In this project, we extend the classical scalar transport problem into a **coupled multi-physics system** involving:

* Species transport
* Heat generation via reaction
* Buoyancy-driven flow (natural convection)

This transforms a simple diffusion problem into a **reactive flow simulation**, which is highly relevant in engineering domains such as combustion, fire dynamics, atmospheric plumes, and chemical reactors.

---

## What is being solved?

We simulate the evolution of two scalar fields:

* **Species concentration (C)**
* **Temperature (T)**

These fields are governed by:

### 1. Advection–Diffusion of Species

The species is transported due to:

* Fluid motion (advection)
* Molecular diffusion

Additionally, species is **consumed by a reaction**.

---

### 2. Heat Equation with Source Term

Temperature evolves due to:

* Diffusion
* Heat release from reaction

The reaction acts as a **source term**, increasing temperature locally.

---

### 3. Reaction Model (Arrhenius-type)

A temperature-dependent reaction is used:

* Reaction rate increases exponentially with temperature
* This creates **nonlinear feedback**:

  Higher temperature → faster reaction → more heat → even higher temperature

This mechanism is responsible for **thermal runaway behavior** observed in the results.

---

### 4. Fluid Flow (Navier–Stokes)

The flow field is governed by the incompressible Navier–Stokes equations.

A buoyancy force is introduced:

* Hot fluid becomes lighter and rises
* Cold fluid sinks

This generates **natural convection (plume formation)**.

---

## Why is this important?

This problem captures the **core physics of reactive flows**, which appear in:

* Combustion systems (engines, burners)
* Smoke and fire plume modeling
* Chemical reactors
* Atmospheric transport phenomena

It demonstrates how **multiple physical processes interact**:

* Diffusion smooths gradients
* Reaction sharpens gradients
* Buoyancy redistributes energy

Understanding this interplay is critical in real-world CFD applications.

---

## How this extends Project 1

### Project 1:

* Solved **pure species transport**
* Physics involved:

  * Diffusion
  * Advection (optional)

Behavior was **smooth and predictable**

---

### Project 2:

We introduce **three major complexities**:

#### 1. Reaction Coupling

* Species is no longer conserved
* It is **consumed dynamically**
* Temperature becomes a dependent variable

#### 2. Thermal Feedback

* Reaction depends on temperature
* Temperature depends on reaction

This creates **strong nonlinearity**

---

#### 3. Flow Coupling (Buoyancy)

* Temperature affects density (via buoyancy)
* Density drives flow
* Flow transports temperature and species

This creates full **two-way coupling**

---

### Summary of progression

| Feature         | Project 1 | Project 2 |
| --------------- | --------- | --------- |
| Diffusion       | Yes       | Yes       |
| Advection       | Yes       | Yes       |
| Reaction        | No        | Yes       |
| Heat generation | No        | Yes       |
| Fluid flow      | No        | Yes       |
| Buoyancy        | No        | Yes       |
| Nonlinearity    | Low       | High      |

---

## Key Physical Behavior Observed

### 1. Thermal Runaway

* Rapid increase in temperature due to reaction feedback
* Controlled by diffusion (kappa)

---

### 2. Diffusion vs Reaction Competition

* High diffusion → stable system
* Low diffusion → sharp gradients and instability

---

### 3. Plume Formation

* Heated fluid rises
* Forms characteristic mushroom-shaped structures

---

### 4. Rayleigh Number Scaling

A dimensionless number is used to quantify buoyancy effects:

* Higher temperature → higher buoyancy → stronger flow
* Lower diffusivity → higher Rayleigh number

---

## Numerical Method

The simulation is implemented using **Basilisk CFD framework**, which provides:

* Finite-volume discretization
* Adaptive grid capability (extendable)
* Built-in Navier–Stokes solver
* Efficient diffusion and advection operators

---

## Key Parameters Studied

The main parameter varied in this study is:

* Thermal diffusivity (kappa)

Values tested:

* 0.01
* 0.005
* 0.002

This allows investigation of:

* Stability vs instability
* Reaction intensity
* Buoyancy strength

---

## Outcome

This project demonstrates:

* Coupled multi-physics simulation capability
* Understanding of nonlinear reactive systems
* Ability to extract engineering insights from CFD data

It forms a strong foundation for advanced topics such as:

* Combustion modeling
* Turbulent reactive flows
* Multiphase reacting systems

---

## Next Steps

Future improvements may include:

* Adaptive mesh refinement (AMR)
* More realistic reaction kinetics
* Turbulence modeling
* 3D simulations

---

This project marks the transition from basic CFD to realistic engineering simulations involving strongly coupled physics.

