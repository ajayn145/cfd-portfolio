# Project 1: Reactive Scalar Transport Solver

## Objective

To develop a 2D finite-volume CFD solver for scalar transport including advection, diffusion, and reaction using Basilisk.

---

## Problem Description

A scalar concentration field (C) is initialized as a Gaussian blob and transported in a uniform velocity field.

The governing equation solved is:

∂C/∂t + ∇·(uC) = D∇²C − kC

The scalar undergoes:

- Advection (transport by flow)
- Diffusion (spreading due to gradients)
- Reaction (decay over time)

---

## Physical Interpretation

```mermaid
flowchart LR
    A[Initial Blob] --> B[Moves with Flow]
    B --> C[Spreads]
    C --> D[Decays]
