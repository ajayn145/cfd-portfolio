# Tools & Implementation Stack

## Overview

This project was developed using a combination of CFD frameworks, programming tools, and visualization utilities. Each tool was selected based on its role in solving the governing equations efficiently and transparently.

---

## Core Solver Framework

### Basilisk (CFD Library)

**Why it was used:**
- Easy for learning and implementing the libraries.
- Provides built-in numerical solvers for:
  - Advection
  - Diffusion
  - Multigrid methods
- Allows direct implementation of governing equations
- Offers fine control over numerical methods

**Role in Project:**
- Solves the species transport equation
- Handles grid generation and time-stepping
- Provides efficient numerical operators

---

## Programming Language

### C Language

**Why it was used:**
- Required for working with Basilisk
- Allows low-level control over numerical operations
- High computational efficiency (important for CFD)

**Role in Project:**
- Implements solver logic
- Defines simulation events (initialization, advection, diffusion, reaction)
- Controls simulation flow

---

## Numerical Methods

### Finite Volume Method (FVM)

**Why it was used:**
- Conserves physical quantities (mass, species)
- Widely used in industrial CFD solvers

**Role in Project:**
- Discretizes the governing equation over control volumes

---

### Explicit Time Stepping

**Why it was used:**
- Simple to implement and understand
- Suitable for transient simulations

**Trade-off:**
- Requires small time step for stability

---

### Multigrid Solver (Diffusion)

**Why it was used:**
- Efficient for solving diffusion equations
- Reduces computational cost compared to simple solvers

---

## Visualization

### Basilisk Output (`output_ppm`)

**Why it was used:**
- Built-in and easy to integrate with solver
- Generates frame-by-frame visualization

---

### Video Conversion (`ppm2mp4`)

**Why it was used:**
- Converts simulation frames into a continuous video
- Helps visualize transient behavior clearly

---

## Development Environment

### Linux / WSL

**Why it was used:**
- Basilisk is best supported in Linux environments
- Provides stable compilation and execution setup

---

### GCC / qcc Compiler

**Why it was used:**
- Required to compile Basilisk-based C programs
- Optimized for numerical computations

---

## Version Control

### Git & GitHub

**Why it was used:**
- Tracks changes in code and documentation
- Enables project versioning and sharing

---

## Documentation

### MkDocs + Material Theme

**Why it was used:**
- Converts project into structured documentation
- Helps present work professionally
- Easy deployment via GitHub Pages

---

## Summary

Each tool in this project was selected based on its ability to support:

- Accurate numerical simulation
- Efficient computation
- Clear visualization
- Professional documentation

Together, they form a complete workflow similar to real-world CFD development pipelines.
