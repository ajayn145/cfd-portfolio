# Project 1: Reactive Scalar Transport Solver

## Objective

To develop a 2D finite-volume CFD solver for scalar transport including advection, diffusion, and reaction using Basilisk.

---

## Problem Description

A scalar concentration field (C) is initialized as a Gaussian blob and transported in a uniform velocity field.

The governing equation solved is:

`∂C/∂t + ∇·(uC) = D∇²C − kC`

The scalar undergoes:

- Advection (transport by flow)
- Diffusion (spreading due to gradients)
- Reaction (decay over time)

---

## Advection (Transport by Flow)

![Advection](../assets/diagrams/advection.png)
The scalar is transported by the velocity field without changing its shape significantly.
---

## Diffusion (Spreading)

![Diffusion](../assets/diagrams/diffusion.png)
The scalar spreads from regions of high concentration to low concentration, smoothing the distribution.
---

## Reaction (Decay)

![Reaction](../assets/diagrams/reaction.png)
The scalar concentration decreases over time due to a decay process.
---

## Combined Effect

![Combined](../assets/diagrams/combined.png)

---

## Key Insight

The scalar field evolution depends strongly on both physical parameters and the numerical scheme used, which affects stability and accuracy.
