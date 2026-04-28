# Overview

## Project Title

# Reduced Order Modeling of Flow Around a Circular Cylinder using POD in Basilisk

---

## Problem Statement

The objective of this project is to simulate 2D incompressible flow around a circular cylinder at Reynolds number Re = 100 and develop a Reduced Order Model (ROM) using Proper Orthogonal Decomposition (POD).

Flow around a cylinder is one of the most classical benchmark problems in Computational Fluid Dynamics (CFD) because it contains essential fluid physics such as:

- boundary layer development
- flow separation
- wake formation
- recirculation region
- vortex shedding
- transient unsteady flow behavior

Instead of only solving the full CFD problem, this project focuses on extracting the dominant coherent flow structures using POD and building the foundation for a computationally efficient reduced-order representation of the system.

The goal is not only simulation, but also physics compression.

---

## Engineering Relevance

Reduced Order Modeling is extremely important in engineering because high-fidelity CFD simulations are computationally expensive.

For real industrial applications such as:

- aerodynamic design
- thermal management
- flow control
- digital twins
- optimization studies
- real-time monitoring
- design space exploration

running full CFD repeatedly becomes impractical.

ROM solves this problem by:

> capturing the dominant physics of the system using only a small number of modes

This enables:

- faster simulations
- near real-time predictions
- lower computational cost
- rapid design iterations

Cylinder wake flow provides an ideal benchmark to study ROM because it contains both steady and transient flow structures.

---

## Motivation for This Project

The motivation for doing this project came from an important practical engineering problem:

High-fidelity CFD simulations are expensive and slow.

In industrial environments, engineers often need to perform:

 - multiple design iterations
 - optimization studies
 - parametric analysis
 - transient performance evaluation
 - real-time monitoring

Running full CFD for every case becomes computationally expensive and often impractical. This creates the need for Reduced Order Models (ROM). ROM allows engineers to preserve the dominant system physics while dramatically reducing computational cost.

---

## Why This Project After Lid-Driven Cavity?

The lid-driven cavity project was the first ROM project used to understand the fundamentals of:

 - snapshot generation
 - POD matrix construction
 - Singular Value Decomposition (SVD)
 - mode extraction
 - temporal coefficient analysis

However, the lid-driven cavity problem is primarily:-

				Internal + confined + mostly steady flow

where the dominant structure is largely stable and symmetric. It is excellent for learning the mathematics of POD, but it does not fully represent the complexity of real engineering flows.

The cylinder flow project was chosen as the next step because it introduces:

			External + separated + transient + wake-dominated flow

which is much closer to industrial CFD problems. This project helps bridge the gap between:
learning POD theory and Applying POD to realistic engineering physics

## Difference Between Lid-Driven Cavity and Cylinder ROM

| Feature               | Lid-Driven Cavity              | Flow Around Cylinder              |
| --------------------- | ------------------------------ | --------------------------------- |
| Flow Type             | Internal flow                  | External flow                     |
| Geometry              | Closed square cavity           | Bluff body in open domain         |
| Driving Mechanism     | Moving top wall                | Inlet free stream                 |
| Flow Nature           | Mostly steady / weak transient | Strongly transient                |
| Dominant Physics      | Recirculation vortex           | Wake + vortex shedding            |
| POD Behavior          | One dominant steady mode       | Paired oscillatory modes expected |
| Engineering Relevance | Fundamental learning case      | Real industrial relevance         |
| ROM Complexity        | Beginner level                 | Intermediate / advanced           |


The cavity project teaches:"How POD works"

The cylinder project teaches:"Why POD matters in real engineering"



### Low Reynolds Number

- attached flow
- symmetric wake

### Moderate Reynolds Number (Re ≈ 100)

- wake instability
- vortex shedding begins
- periodic oscillations appear

### High Reynolds Number

- turbulent wake
- strong nonlinear behavior

This makes the cylinder case an excellent candidate for understanding how POD captures coherent flow structures.

---

## What Was Done

In this project:

- 2D incompressible Navier–Stokes equations were solved using Basilisk
- the embedded boundary (`embed.h`) approach was used to represent the circular cylinder
- the centered pressure–velocity coupled solver was used
- transient flow simulation was performed up to t = 10
- velocity snapshots were saved at regular intervals
- Proper Orthogonal Decomposition (POD) was applied using Python
- Singular Value Decomposition (SVD) was used to extract dominant modes
- temporal coefficients were analyzed
- modal energy distribution was studied
- dominant coherent structures were interpreted

The full workflow was:

```text
CFD Simulation → Snapshot Generation → POD → Modal Analysis → Physical Interpretation
