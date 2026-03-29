# Vector Calculus Basics (Used in This Project)

## Why This Section?

In this project, we use mathematical terms such as:

- Nabla
- Divergence
- Laplacian

These are simply tools used to describe how physical quantities:

- Move
- Spread
- Change in space

This section explains these ideas in a clear and simple way.

--------------------------------------------------

## 1. What is a Field?

A field is a quantity defined at every point in space.

Examples:

- Temperature field:
  T(x, y) → temperature at each location

- Velocity field:
  u(x, y) → fluid speed and direction at each location

--------------------------------------------------

## 2. What is Nabla?

Nabla represents change in space.

It answers the question:

- How does a value change if we move slightly in space?

--------------------------------------------------

## 3. Gradient

Written as:

grad(T)

### Meaning

- Shows the direction in which a value increases the fastest
- Indicates how strong that increase is

### Example

- If temperature increases upward:
  → Gradient points upward

### Simple understanding

- Gradient tells us:
  Where something increases and how fast

--------------------------------------------------

## 4. Divergence

Written as:

div(u)

### Meaning

- Measures how fluid spreads out or comes together

### Cases

- If fluid spreads outward:
  → Divergence is positive

- If fluid moves inward:
  → Divergence is negative

### Special case (important)

- div(u) = 0

This means:

- Fluid is incompressible
- Volume remains constant

--------------------------------------------------

## 5. Laplacian

Written as:

laplacian(T)

### Meaning

- Measures how different a value is compared to its surroundings

### Physical interpretation

- If a point is hotter than nearby points:
  → Heat spreads outward

- If a point is colder:
  → Heat flows inward

### Simple understanding

- Laplacian represents spreading

--------------------------------------------------

## 6. Connecting to This Project

### Species Equation

dC/dt + div(uC) = D * laplacian(C) - kC

#### Terms

- dC/dt  
  Change of concentration with time

- div(uC)  
  Transport due to fluid motion

- laplacian(C)  
  Diffusion (spreading)

- kC  
  Reaction (consumption of species)

--------------------------------------------------

### Temperature Equation

dT/dt + div(uT) = kappa * laplacian(T) + Q * kC

#### Terms

- dT/dt  
  Change of temperature with time

- div(uT)  
  Transport due to flow

- laplacian(T)  
  Heat diffusion

- Q * kC  
  Heat generation due to reaction

--------------------------------------------------

## 7. Physical Understanding of the System

The simulation follows this sequence:

1. Reaction occurs  
   - Species decreases  
   - Temperature increases  

2. Heat spreads  
   - Diffusion smooths temperature  

3. Buoyancy starts  
   - Hot fluid rises  

4. Flow develops  
   - Fluid motion carries species and heat  

5. Plume forms  
   - Visible rising structure appears  

--------------------------------------------------

## 8. Final Summary

Vector calculus helps describe:

- Movement  
  → div(uC)

- Spreading  
  → laplacian(C)

- Change over time  
  → d/dt

--------------------------------------------------

## One-Line Understanding

Vector calculus is a way to describe how physical quantities move, spread, and change in space.
