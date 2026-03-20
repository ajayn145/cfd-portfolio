# Project 1: Reactive Scalar Transport Solver

## Objective

To develop a 2D CFD solver for scalar transport including advection, diffusion, and reaction using Basilisk.

## Problem Description

A scalar concentration field (C) is initialized as a Gaussian blob and transported in a uniform velocity field. The scalar undergoes:

- Advection (transport by flow)
## Advection (Transport by Flow)

```mermaid
flowchart LR
    A[Blob at Left] --> B[Moves Right]
    B --> C[Continues Moving]
    
- Diffusion (spreading due to gradients)

---

## Diagram 2 — Diffusion

```markdown
## Diffusion (Spreading)

```mermaid
flowchart LR
    A[Concentrated Blob] --> B[Spreads Out]
    B --> C[More Uniform]
    
    
- Reaction (decay over time)


---

## Diagram 3 — Reaction

```markdown
## Reaction (Decay)

```mermaid
flowchart LR
    A[High Concentration] --> B[Reduced]
    B --> C[Almost Zero]
    
    

---

## Diagram 4 — Combined Physics (VERY IMPORTANT)

```markdown
## Combined Effect

```mermaid
flowchart LR
    A[Initial Blob]
    A --> B[Moves Right]
    B --> C[Spreads]
    C --> D[Decays]
    

---

## Step 3 — Add CFD-Style Diagram (Advanced Look)

Add this (very powerful):

```markdown
## Governing Physics

```mermaid
flowchart TD
    A[Advection\n(u · ∇C)]
    B[Diffusion\n(D ∇²C)]
    C[Reaction\n(-kC)]

    A --> D[Final Solution]
    B --> D
    C --> D    
    


## Applications

This type of model is fundamental in:

- Pollutant transport in air and water
- Combustion (fuel species transport)
- Heat and mass transfer problems
- HVAC airflow and contaminant dispersion

## Key Features

- Finite-volume formulation (Basilisk)
- Transient simulation
- Reaction kinetics implementation
- Visualization using PPM → MP4 pipeline
