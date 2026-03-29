# Implementation

## Introduction

This section explains how the governing equations are implemented in code using the Basilisk framework.

The implementation is event-based, where each physical process is handled in a structured sequence.

--------------------------------------------------

## 1. Overall Structure of the Code

The solver is written using Basilisk’s event-driven architecture.

Main components:

- Field definitions
- Initialization
- Physical processes (advection, diffusion, reaction)
- Fluid solver
- Output

Each part is handled using "events".

--------------------------------------------------

## 2. Field Definitions

The following variables are defined:

- C → species concentration
- T → temperature
- u → velocity field
- p → pressure

In code:

scalar C[], T[];

These represent values stored at each grid cell.

--------------------------------------------------

## 3. Initialization

The simulation starts by defining initial conditions.

A Gaussian distribution is used:

- Species is concentrated in a small region
- Temperature follows the same distribution

Meaning:

- A "blob" is created at the start
- This blob evolves over time

--------------------------------------------------

## 4. Time Loop (Core Execution)

The simulation progresses step-by-step in time.

At each time step, the following processes occur:

1. Advection
2. Diffusion
3. Reaction
4. Fluid flow update
5. Buoyancy effect
6. Output

--------------------------------------------------

## 5. Advection Implementation

Advection moves quantities with the fluid.

In code:

advection({C, T}, u, dt);

Meaning:

- Species and temperature are transported
- Movement depends on velocity field

--------------------------------------------------

## 6. Diffusion Implementation

Diffusion spreads quantities from high to low values.

In code:

diffusion(C, dt, Df);
diffusion(T, dt, Df);

Meaning:

- C spreads using diffusion coefficient D
- T spreads using thermal diffusivity kappa

--------------------------------------------------

## 7. Reaction Implementation

Reaction is computed explicitly at each cell.

Steps:

1. Compute reaction rate:

k = k0 * exp(-Ea / T)

2. Compute change in species:

dC = k * C * dt

3. Update values:

C = C - dC  
T = T + Q * dC  

Meaning:

- Species is consumed
- Temperature increases

--------------------------------------------------

## 8. Fluid Solver (Navier–Stokes)

Fluid motion is handled using Basilisk’s built-in solver.

Included using:

#include "navier-stokes/centered.h"

Meaning:

- Velocity and pressure are solved internally
- No need to manually implement equations

--------------------------------------------------

## 9. Buoyancy Implementation

Buoyancy is added as a force in the vertical direction.

In code:

av.y[] = (T[] + T[-1]) / 2;

Meaning:

- Temperature generates upward force
- Hot fluid rises

--------------------------------------------------

## 10. Boundary Conditions

Velocity:

- No-slip condition
- Fluid velocity is zero at walls

Scalars (C and T):

- Initialized at the beginning
- No external inflow or outflow

--------------------------------------------------

## 11. Output Generation

Results are saved at regular time intervals.

Outputs include:

- Species field (C)
- Temperature field (T)
- Velocity magnitude
- Vorticity

Also, videos are generated using:

ppm2mp4

--------------------------------------------------

## 12. Data Logging

Key quantities are tracked over time:

- Maximum temperature
- Total species mass
- Plume height

These are stored in log files for analysis.

--------------------------------------------------

## 13. Workflow Summary

At each time step:

1. Transport (advection)
2. Spread (diffusion)
3. React (reaction)
4. Move fluid (Navier–Stokes)
5. Apply buoyancy
6. Save results

--------------------------------------------------

## 14. Key Implementation Insight

This solver does not just solve separate equations.

It combines:

- Reaction
- Heat transfer
- Fluid motion

All interacting together.

--------------------------------------------------

## Final Understanding

The implementation shows how a complex physical system can be built step-by-step using:

- Simple operations
- Clear sequence of processes
- Strong coupling between physics

--------------------------------------------------

## One-Line Summary

The code simulates how species reacts, heat is generated, and fluid moves, by updating each physical process step-by-step in time.
