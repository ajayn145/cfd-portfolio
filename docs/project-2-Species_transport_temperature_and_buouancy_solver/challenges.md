# Challenges & Debugging

## 1. Numerical Instability (Temperature Blow-up)

### Problem:
- Temperature increased rapidly and became unbounded
- Simulation produced unrealistic values

### Cause:
- Strong reaction term (exponential growth)
- Insufficient diffusion

### Solution:
- Limited reaction rate (`k_local`)
- Introduced minimum temperature threshold
- Tuned heat release parameter (Q)

### Learning:
> Reaction-dominated systems can easily become unstable

---

## 2. Sensitivity to Diffusion Coefficient (κ)

### Problem:
- Small changes in κ caused drastically different results

### Observation:
- Low κ → sharp gradients → instability
- High κ → smooth solution

### Solution:
- Performed multiple simulations with different κ values
- Compared results using plots

### Learning:
> Diffusion plays a critical role in stabilizing the system

---

## 3. Coupling Between Equations

### Problem:
- Unexpected flow behavior
- Hard to understand cause-effect relationships

### Cause:
Strong coupling between:
- Temperature → buoyancy → velocity → transport → reaction

### Solution:
- Studied each term individually
- Monitored key variables (Tmax, Csum, plume height)

### Learning:
> Multi-physics systems are highly nonlinear and interdependent

---

## 4. Incorrect File Handling (Log Files)

### Problem:
- Only one log file was generated despite multiple runs

### Cause:
- File naming was not parameterized properly

### Solution:
- Used dynamic filenames:**log_kappa_%g.dat**


- Ensured each simulation writes separate output

### Learning:
> Proper data management is essential for parametric studies

---

## 5. Plotting Errors in Python

### Problem:
- Missing plots
- Incorrect file references

### Cause:
- File name mismatch (0.01 vs 0.001)
- Duplicate code blocks

### Solution:
- Cleaned Python script
- Verified file names
- Structured plotting logic clearly

### Learning:
> Post-processing is as important as simulation

---

## 6. Video Rendering Issues

### Problem:
- Videos not appearing in website
- 404 errors

### Cause:
- Incorrect file paths
- Files not placed in correct directory

### Solution:
- Moved videos to proper folder:**docs/project-2-.../images/**

- Updated markdown paths

### Learning:
> File organization is crucial for documentation

---

## 7. MkDocs Navigation Errors (404 Issues)

### Problem:
- Pages not loading
- "404 Not Found" errors

### Cause:
- Incorrect paths in `mkdocs.yml`
- Typographical mistakes

### Solution:
- Fixed navigation paths
- Ensured folder structure matches config

### Learning:
> Documentation requires the same debugging mindset as coding

---

## 8. Understanding Physical Meaning

### Problem:
- Difficulty interpreting results initially

### Solution:
- Related results to physical concepts:
- Diffusion → smoothing
- Reaction → heat generation
- Buoyancy → plume rise

### Learning:
> CFD is not just coding — it is physical interpretation

---

## 9. Managing Multiple Outputs

### Problem:
- Handling multiple plots and videos became messy

### Solution:
- Organized outputs:
- Separate folders for images and videos
- Clear naming conventions

### Learning:
> Structured workflow improves productivity

---

## 10. Learning Curve (From Project 1 to Project 2)

### Challenge:
- Moving from simple transport to multi-physics system

### Differences:
- Project 1 → single equation
- Project 2 → coupled system

### Learning:
> Understanding evolves significantly with complexity

---

## Final Takeaway

The biggest lesson from this project:

> Debugging is not just fixing errors — it is understanding the physics, numerics, and implementation together.

Every challenge improved:
- Problem-solving ability
- Physical intuition
- CFD understanding













