# Challenges & Debugging

During the setup and execution of the Ahmed body simulation, several issues were encountered and resolved.

---

## Summary Table

| # | Issue | Cause | Fix | Key Learning |
|---|------|------|-----|-------------|
| 1 | PIMPLE undefined | Missing PIMPLE dictionary in `fvSolution` | Added PIMPLE block | Solver algorithms depend on correct dictionary structure |
| 2 | OmegaFinal missing | Required by k-omega SST model | Added `omegaFinal` entry | Turbulence models need additional solver controls |
| 3 | wallDist undefined | Wall distance not specified | Added `meshWave` method | Wall models depend on geometric distance |
| 4 | div(phi,omega) missing | Missing discretization scheme | Added scheme in `fvSchemes` | Each equation needs explicit discretization |
| 5 | meshWave typo | Incorrect spelling | Corrected to `meshWave` | Runtime selection is sensitive to typos |
| 6 | Courant explosion | Time step too large | Reduced `deltaT`, enabled `adjustTimeStep`, limited `maxCo` | Stability depends on Courant number |
| 7 | Forces not generated | Function object placed incorrectly | Moved forces definition to `system/functions` | Function object placement affects execution |
| 8 | Frontal area confusion | Incorrect understanding of reference area | Used Ahmed body dimensions (0.389 × 0.288 m²) | Cd depends on correct reference area |

---

## Key Takeaways

- OpenFOAM requires strict dictionary structure
- Turbulence models introduce additional dependencies
- Numerical stability must be controlled through time stepping
- Small configuration errors can stop the simulation
- Correct post-processing setup is essential for meaningful results
