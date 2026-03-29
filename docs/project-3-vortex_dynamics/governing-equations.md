# GOVERNING EQUATIONS

This project solves the **incompressible Navier–Stokes equations**, which describe how fluid moves.

---

## 1. Continuity Equation (Mass Conservation)

∇ · u = 0

### What it means:

- u → velocity of the fluid  
- ∇ · u → divergence (how much fluid is expanding or compressing)

This equation ensures the fluid is **incompressible**  
Fluid volume does not change

---

## 2. Momentum Equation

∂u/∂t + (u · ∇)u = −∇p + ν ∇²u

---

## Explanation of each term

### 1. ∂u/∂t → Time change
- How velocity changes with time  

---

### 2. (u · ∇)u → Advection
- Fluid carries its own velocity  
- Responsible for movement of flow structures  

---

### 3. −∇p → Pressure force
- Fluid moves from high pressure to low pressure  

---

### 4. ν ∇²u → Diffusion (Viscosity)
- Smooths out velocity differences  
- Controls how sharp or diffused the flow is  

---

## 3. Initial Shear Layer

uₓ = U₀ * tanh((y − y₀)/δ)

---

### Meaning of terms:

- U₀ → velocity magnitude  
- y₀ → center of the domain  
- δ → thickness of the shear layer  

 This creates two regions:

- Top layer → moving right  
- Bottom layer → moving left  

---

## 4. Perturbation (Instability Trigger)

uᵧ = A * sin(2πkx)

---

### Meaning:

- A → amplitude (strength of disturbance)  
- k → wave number (how many waves)  

This small disturbance grows over time and causes instability  

---

## Physical Interpretation

- The velocity difference creates **shear**
- Shear leads to **instability**
- Instability leads to **vortex formation**

---

## Final Insight

Even a very small disturbance in a fluid can grow into large vortex structures due to instability.

---
