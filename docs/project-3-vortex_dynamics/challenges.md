# CHALLENGES FACED

## 1. No Vortex Formation Initially

### Problem

- Flow remained smooth  
- No visible instability  

### Cause

- Perturbation amplitude too small  

### Solution

- Increased disturbance strength  
- Adjusted sine wave frequency  

---

## 2. Weak or Blurry Vortices

### Problem

- Vortices were not clearly visible  

### Cause

- High numerical diffusion  
- Low grid resolution  

### Solution

- Increased grid resolution (256)  
- Reduced viscosity  

---

## 3. Slow Instability Growth

### Problem

- Instability took too long to develop  

### Cause

- Thick shear layer  

### Solution

- Reduced shear thickness  

---

## 4. Compilation Errors

### Problem

- Errors related to math functions (tanh, sin, sqrt)  

### Cause

- Math library not linked  

### Solution

- Added:
  -lm during compilation  

---

## 5. Video Not Rendering in Website

### Problem

- Videos not loading in MkDocs  

### Cause

- Incorrect file path  

### Solution

- Used correct relative path:
  ../images/video.mp4  

---

## Final Learning

Most issues were resolved by understanding the physics and adjusting parameters accordingly.

---
