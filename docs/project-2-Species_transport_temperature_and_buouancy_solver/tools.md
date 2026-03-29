# Tools & Libraries Used

## 1. Basilisk CFD Framework

The core solver for this project was developed using **Basilisk**, an advanced CFD framework designed for solving partial differential equations with high efficiency.

### Key Basilisk Modules Used

#### grid/multigrid.h
- Provides structured grid with multigrid solver
- Ensures fast convergence of pressure Poisson equation

> Used for efficient pressure-velocity coupling

---

#### navier-stokes/centered.h
- Implements incompressible Navier-Stokes equations
- Uses centered discretization scheme

> Handles velocity and pressure fields

---

#### diffusion.h
- Solves diffusion equation for scalar fields

> Used for:
- Species diffusion
- Thermal diffusion

---

#### run.h
- Controls simulation loop
- Manages time stepping and events

> Enables event-driven simulation structure

---

#### output.h
- Handles output generation
- Supports field visualization and file writing

> Used for:
- PPM image output
- Video generation

---

## 2. C Programming Language

The solver is implemented in **C**, which is the native language of Basilisk.

### Why C?
- High computational efficiency
- Low-level control over numerical operations
- Essential for performance-critical CFD solvers

---

## 3. Python (Post-Processing & Analysis)

Python was used to analyze simulation results and generate plots.

### Libraries Used:

#### NumPy
- Reading `.dat` files
- Numerical computations

#### Matplotlib
- Plotting graphs
- Comparing simulation cases

### Applications:
- Tmax vs Time
- Species decay (Csum)
- Plume height evolution
- Rayleigh number analysis

---

## 4. Flow Visualization Tools

### ppm2mp4
- Converts `.ppm` image sequences into videos

### Outputs Generated:
- Temperature field evolution (`T.mp4`)
- Species distribution (`C.mp4`)
- Velocity magnitude (`vel.mp4`)
- Vorticity field (`vort.mp4`)

> Enables clear understanding of flow physics

---

## 5. MkDocs (Documentation Framework)

Used to create a structured and professional project website.

### Features:
- Markdown-based documentation
- Easy navigation
- Clean UI using Material theme

---

## 6. GitHub (Version Control & Hosting)

Used for:
- Managing project code
- Hosting documentation website

### Benefits:
- Version tracking
- Public portfolio showcasing

---

## 7. Linux / Terminal Environment

All simulations and workflows were executed via terminal.

### Tasks Performed:
- Compiling Basilisk solver
- Running simulations with different parameters
- Executing Python scripts
- Managing files and directories

---

## Final Insight

This project integrates:

- Numerical simulation (Basilisk + C)
- Scientific computing (CFD modeling)
- Data analysis (Python)
- Visualization (Matplotlib + videos)
- Documentation (MkDocs)

> This reflects a complete end-to-end CFD workflow from simulation to presentation
