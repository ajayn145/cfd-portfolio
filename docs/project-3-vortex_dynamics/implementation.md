# IMPLEMENTATION

## Introduction

This section explains how the governing equations are implemented using the Basilisk framework.

The solver follows an **event-driven structure**, where each physical process is handled step-by-step.

---

## 1. Including Required Libraries

```c
#include "grid/multigrid.h"
#include "navier-stokes/centered.h"
#include "output.h"
#include <math.h>
```

### Purpose:

- grid/multigrid.h → grid and solver structure  
- navier-stokes/centered.h → fluid flow equations  
- output.h → visualization  
- math.h → mathematical functions  

---

## 2. Domain Setup

```c
size (1.0);
origin (0, 0);
init_grid (256);
```

### Meaning:

- Domain size = 1 × 1  
- Grid resolution = 256 × 256  
- Higher resolution → better accuracy  

---

## 3. Physical Parameters

```c
double U0 = 1.0;
double thickness = 0.01;
double nu = 1e-4;
```

### Meaning:

- U0 → velocity strength  
- thickness → shear layer thickness  
- nu → viscosity  

---

## 4. Initial Condition

```c
u.x[] = U0 * tanh((y - y_mid)/thickness);
u.y[] = 0.05 * sin(4*pi*x);
```

### Explanation:

- tanh profile creates shear layer  
- sine function adds disturbance  

---

### Physical meaning:

- Two fluid layers moving in opposite directions  
- Small disturbance triggers instability  

---

## 5. Viscosity Definition

```c
face vector muv[];

event properties (i++) {
  foreach_face()
    muv.x[] = nu;
}
```

### Meaning:

- Defines viscosity in the system  
- Controls diffusion of velocity  

---

## 6. Time Stepping

```c
DT = 5e-4;
```

### Meaning:

- Simulation advances in small time steps  
- Smaller DT → more stable solution  

---

## 7. Output: Velocity Field

```c
scalar magU[];

foreach()
  magU[] = sqrt(u.x[]*u.x[] + u.y[]*u.y[]);
```

### Meaning:

- Computes velocity magnitude  
- Used for visualization  

---

## 8. Output: Vorticity Field

```c
omega[] = (u.y[1] - u.y[-1] - u.x[0,1] + u.x[0,-1])/(2*Delta);
```

### Meaning:

- Measures rotation of fluid  
- Highlights vortices  

---

## 9. Video Generation

```c
popen("ppm2mp4 -r 25 vort.mp4", "w");
```

### Meaning:

- Converts simulation frames into video  
- Helps visualize flow evolution  

---

## 10. Simulation Flow

At each time step:

1. Solve Navier–Stokes equations  
2. Update velocity field  
3. Apply viscosity  
4. Enforce incompressibility  
5. Generate output  

---

## Final Understanding

Each line of code directly corresponds to a physical process in the fluid.

---

## One-Line Summary

The implementation translates fluid equations into computational steps using Basilisk’s event-driven solver.

---
