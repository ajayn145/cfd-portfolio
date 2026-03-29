# Numerical Method 

## Why Do We Need a Numerical Method?

The equations we are solving (fluid flow + heat + reaction) are:

* Very complex
* Nonlinear
* Coupled together

This means we **cannot solve them exactly using formulas**.

So instead, we:

* Break the domain into small pieces
* Solve equations approximately
* March forward in time

This is called a **numerical method**.

---

# 1. Governing Idea

We solve equations of the form:
```
Change = Transport + Diffusion + Reaction
```

For species (C):
```
∂C/∂t + ∇·(uC) = D∇²C - kC
```

For temperature (T):
```
∂T/∂t + ∇·(uT) = κ∇²T + QkC
```

---

## What each term means

### ∂C/∂t

* Change of concentration with time
* "How fast is it changing?"

---

### ∇·(uC)

Advection (movement by fluid)
* u → velocity (how fast fluid moves)
* C → how much species is present
Fluid carries the species along with it

---

### D∇²C

Diffusion
* D → diffusion coefficient
* ∇² → spreading operator
Species spreads from high concentration → low concentration

---

### -kC
Reaction (consumption)
* k → reaction rate
* C → amount of species
Species gets consumed

---

### QkC (Temperature equation)
Heat generation due to reaction
* Q → heat released per reaction
* kC → reaction strength
More reaction = more heat

---

# 2. Domain Discretization (Breaking the Space)
We divide the domain into small squares:

```
|---|---|---|
|   |   |   |
|---|---|---|
|   |   |   |
|---|---|---|
```

Each box = **control volume (cell)**

---

## What is stored in each cell?
Each cell contains:
* Velocity (u)
* Pressure (p)
* Species (C)
* Temperature (T)

---

# 3. Finite Volume Method (Core Idea)
Instead of solving equations at a point:
We solve them over a **small box**

---

## Fundamental Equation
For any cell:
```
Rate of change inside cell = Flux entering - Flux leaving + Source
```
---

### Break it down:
* Flux entering → stuff coming in
* Flux leaving → stuff going out
* Source → generation (reaction, heat, etc.)
---
This ensures:
* Conservation
* Nothing is lost or magically created
---

# 4. Discretizing Time

We move forward step by step:
```
t = 0 → t = DT → t = 2DT → ...
```
Time step:
```
DT = 1e-4
```
---
## Time derivative approximation
Instead of:
```
∂C/∂t
```
We use:
```
(C_new - C_old) / DT
```
---
Meaning:
New value = Old value + change over time
---
# 5. Advection (Transport by Fluid)

Equation:

```
∇·(uC)
```

---

## Physical Meaning
Imagine
* Water flowing in a pipe
* Dye mixed in it
Dye moves with water
---

## Numerical Treatment
At each cell face:
```
Flux = velocity × concentration
```
---
Basilisk handles this automatically:
```
advection({C, T}, u, dt)
```
---
## Important Property
* Conservative
* Stable
* Handles moving fronts
---
# 6. Diffusion (Spreading)
Equation:
```
D∇²C
```
---
## Physical Meaning

If concentration is high here:

```
HIGH → LOW
```

It spreads out

---

## Numerical Approximation

Second derivative:

```
∇²C ≈ (C_right + C_left + C_top + C_bottom - 4*C_center)
```

---

## Solver

```
diffusion(C, dt, Df)
```

---

### Important:

✔ Implicit method
✔ Stable even for larger time steps

---

# 7. Reaction (Chemical Process)

Equation:

```
Rate = k * C
```

---

## Temperature-dependent reaction

```
k = k0 * exp(-Ea / T)
```

---

### Meaning:

* k0 → base reaction rate
* Ea → activation energy
* T → temperature

---

Higher temperature → faster reaction

---

## Numerical update

```
dC = k * C * dt
C = C - dC
T = T + Q * dC
```

---

### Meaning:

* Species decreases
* Temperature increases

---

# 8. Fluid Flow (Navier–Stokes)

We solve:

```
Momentum equation + Continuity equation
```

---

## Simplified idea

Fluid motion depends on:

* Pressure
* Viscosity
* External forces

---

## Incompressibility condition

```
∇·u = 0
```

Fluid cannot compress

---

## Numerical Method

Projection method:

1. Predict velocity
2. Solve pressure equation
3. Correct velocity

---

# 9. Buoyancy (IMPORTANT PHYSICS)

Hot fluid rises

---

## Model used

```
Force ∝ Temperature
```

In code:

```
av.y = average(T)
```

---

## Meaning

* Higher T → stronger upward force
* Causes plume rise

---

# 10. Full Algorithm (VERY IMPORTANT)

At each time step:

```
1. Move species & temperature (advection)
2. Spread them (diffusion)
3. Apply reaction
4. Solve fluid motion
5. Apply buoyancy
6. Save results
```

---

# 11. Stability (Why simulation works)

To avoid errors:

### Time step must be small

```
DT << grid size / velocity
```

---

### Diffusion stability

Handled automatically (implicit)

---

# 12. Key Concepts Summary

| Concept   | Meaning                    |
| --------- | -------------------------- |
| Advection | Transport by fluid         |
| Diffusion | Spreading                  |
| Reaction  | Chemical change            |
| Buoyancy  | Hot fluid rises            |
| FVM       | Solve over small volumes   |
| Time step | March forward step-by-step |

---

# Final Understanding

This solver combines:

* Fluid flow
* Heat transfer
* Chemical reaction

All interacting together.

---

This is why we see:

* Plume formation
* Temperature rise
* Reaction zones

---

## One-Line Summary

We simulate how **fluid moves, carries species, reacts, produces heat, and rises due to buoyancy** — using a stable and conservative numerical method.

