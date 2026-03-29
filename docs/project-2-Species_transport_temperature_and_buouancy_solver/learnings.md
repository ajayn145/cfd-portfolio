
This introduced strong temperature dependence.

### Learning:
- Reaction is not linear
- Small increase in temperature → large increase in reaction rate

To maintain stability:
- Reaction rate was capped
- Temperature lower bound was enforced

This highlighted:

> Numerical stability must sometimes be enforced manually

---

## 5. Buoyancy Drives Flow Formation

Buoyancy was modeled as:
                  a_y ∝ T
                  

This resulted in:
- Rising plume formation
- Vortex structures
- Flow instabilities

### Key understanding:

> Temperature differences create fluid motion even without external forcing

This is fundamental in:
- Natural convection
- Atmospheric flows
- Fire dynamics

---

## 6. Emergence of Complex Flow Structures

Even with simple initial conditions (Gaussian blob), the system developed:

- Mushroom-shaped plumes
- Vortices
- Mixing layers

This shows:

> Complex flow behavior can emerge from simple equations

This is one of the most fascinating aspects of CFD.

---

## 7. Numerical Sensitivity and Stability

The simulation required careful tuning of:

- Time step (DT)
- Diffusion coefficients
- Reaction parameters

If not handled properly:
- Solution diverges
- Temperature blows up
- Simulation becomes unstable

### Key takeaway:

> Stability is as important as accuracy in CFD

---

## 8. Importance of Monitoring Quantities

Tracking the following quantities was crucial:

- Maximum temperature (Tmax)
- Total species (Csum)
- Plume height (center of mass)

These helped in:
- Understanding system behavior
- Comparing different cases
- Identifying instability regions

---

## 9. Rayleigh Number as a Physical Indicator

Rayleigh number was computed as:
                         Ra ∝ Tmax / (nu * kappa)
               



This provided insight into:

- Strength of buoyancy-driven flow
- Transition from stable to unstable regimes

### Learning:

> Non-dimensional numbers help interpret physical behavior

---

## 10. Difference Between Project 1 and Project 2

### Project 1:
- Only species transport
- No flow coupling
- Simpler physics

### Project 2:
- Fully coupled system
- Includes velocity, temperature, reaction, buoyancy
- Highly nonlinear behavior

### Key evolution:

> From solving a single equation → to solving a multi-physics coupled system

---

## 11. Understanding Through Visualization

Visual outputs (videos and plots) played a major role:

- Helped observe plume evolution
- Showed vortex formation
- Revealed instability patterns

### Learning:

> Visualization is essential to understand CFD results

---

## 12. Practical CFD Insight Gained

By completing this project, I gained:

- Understanding of multi-physics coupling
- Experience with instability mechanisms
- Insight into convection-diffusion-reaction systems
- Ability to interpret simulation results physically

---

## Final Takeaway

This project demonstrated that:

> CFD is not just solving equations — it is understanding how physics, numerics, and computation interact.

Small parameter changes can lead to:
- Stable diffusion-dominated flow  
OR  
- Violent convection-driven instability  

Understanding this balance is key to real-world simulations.
























