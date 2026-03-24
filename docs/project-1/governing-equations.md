## What Equation is Being Solved?

This project solves a **species transport equation**, which describes how a substance (species) moves and changes inside a flowing medium.

The governing equation is:

`∂C/∂t + ∇·(uC) = D∇²C − kC`

Where:

- **C** → concentration of the species
- **u** → velocity field (flow direction and speed)
- **D** → diffusion coefficient 
- **k** → reaction rate

---

## Physical Meaning of Each Term

- **∂C/∂t**
  Change of concentration with time

- **∇·(uC)**
  Transport due to fluid motion (Advection)

- **D∇²C**
  Spreading due to concentration gradients (Diffusion)

- **−kC**
  Decay or consumption of species (Reaction)

---

## How This Relates to Real CFD Problems

In real-world simulations, this equation is used to model:

- Pollutant transport in air and water
- Mixing of different fluids
- Heat transfer (temperature behaves like a scalar)
- Combustion and chemical reactions

---

## Important Note

This project solves a **single-species transport problem**, which is a simplified version of real industrial simulations.

In advanced cases, multiple species interact with each other through complex reactions.

