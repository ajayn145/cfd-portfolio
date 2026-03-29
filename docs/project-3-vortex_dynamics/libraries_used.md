# TOOLS & LIBRARIES USED

## 1. Basilisk CFD Framework

The simulation is developed using **Basilisk**, a lightweight and efficient CFD framework.

---

## Key Basilisk Modules Used

### grid/multigrid.h
- Provides grid structure
- Uses multigrid solver for fast convergence  

---

### navier-stokes/centered.h
- Solves incompressible Navier–Stokes equations  
- Handles velocity and pressure coupling  

---

### output.h
- Used for visualization  
- Generates PPM images and videos  

---

## 2. C Programming Language

- Used to implement the solver  
- Provides high performance and control  

---

## 3. Visualization Tools

### ppm2mp4
- Converts simulation frames into videos  
- Used for:
  - Vorticity visualization  
  - Velocity field visualization  

---

## 4. Development Environment

- Linux / Terminal  
- GCC / qcc compiler  

---

## Final Insight

This project integrates:

- Numerical simulation (Basilisk + C)  
- Fluid dynamics modeling  
- Visualization and analysis  

 Represents a complete CFD workflow  

---
