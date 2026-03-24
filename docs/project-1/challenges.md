# Challenges & Debugging

## Overview

During the development of the species transport solver, several numerical and implementation challenges were encountered. Addressing these issues was essential to obtaining a stable and physically meaningful solution.

---

## 1. Non-Physical Oscillations (Stripe Patterns)

### Problem
The scalar field exhibited stripe-like oscillations instead of a smooth distribution.

### Root Cause
- Use of an inappropriate advection treatment
- Numerical dispersion introduced by the scheme

### Resolution
- Replaced the initial approach with Basilisk’s `advection()` operator
- Ensured proper flux-based transport

### Key Insight
The choice of numerical scheme has a direct impact on solution stability and can introduce non-physical artifacts if not handled correctly.

---

## 2. Incorrect Transport Direction

### Problem
The scalar field moved in an unintended direction (vertical instead of horizontal).

### Root Cause
- Incorrect assignment of face-centered velocity (`uf`)
- Misinterpretation of staggered grid variables

### Resolution
Assigned velocity components explicitly:

```c
foreach_face(x)
  uf.x[] = 0.2;

foreach_face(y)
  uf.y[] = 0.0;
```

### Key Insight
Face-centered variables must be handled carefully, especially in staggered grid formulations.

---

## 3. Compilation Error Due to Variable Redefinition

### Problem
Compilation failed due to redefinition of the velocity field (`uf`).

### Root Cause
- Manual declaration of `uf` while it was already defined in `advection.h`

### Resolution
- Removed redundant declaration
- Relied on Basilisk’s internal definitions

### Key Insight
Understanding the internal structure of the solver framework helps avoid conflicts and redundant definitions.

---

## 4. Missing Tracer Definition

### Problem
Compilation error indicating an undefined reference to `tracers`.

### Root Cause
- Basilisk requires a tracer list for scalar transport

### Resolution
Defined tracer explicitly:

```c
scalar * tracers = {C};
```

### Key Insight
Framework-specific requirements must be satisfied even if they are not immediately obvious.

---

## 5. Scalar Field Not Visible

### Problem
The scalar field (blob) was not visible in the output visualization.

### Root Cause
- Improper visualization scaling
- Very low magnitude values of concentration

### Resolution
- Adjusted visualization range (`min` and `max`)
- Tuned initial condition for better visibility

### Key Insight
Visualization parameters can significantly affect interpretation and may hide correct physical behavior.

---

## 6. Excessive Diffusion

### Problem
The scalar field dissipated too quickly, losing its structure.

### Root Cause
- High diffusion coefficient
- Strong reaction rate

### Resolution
- Reduced diffusion coefficient
- Adjusted reaction rate constant

### Key Insight
Physical parameters must be carefully balanced to capture meaningful system behavior.

---

## 7. Time Step Stability Issues

### Problem
The simulation became unstable or produced inaccurate results.

### Root Cause
- Time step too large for explicit time integration

### Resolution
Reduced time step:

```c
DT = 1e-4;
```

### Key Insight
Time step size is critical for stability, especially in explicit schemes.

---

## Summary
These challenges highlight that CFD development involves more than solving equations. It requires:

- Careful selection of numerical methods
- Understanding of solver internals
- Systematic debugging of both numerical and implementation issues

Resolving these problems significantly improved both the accuracy of the solution and the understanding of computational fluid dynamics principles.
