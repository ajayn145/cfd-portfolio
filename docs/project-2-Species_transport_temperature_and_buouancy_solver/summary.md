# Project Summary

## Overview

- Developed a 2D reactive flow simulation using Basilisk (C)
- Modeled coupled physics: species transport, heat transfer, and buoyancy
- Simulated plume formation driven by thermal effects
- Performed parametric study on thermal diffusivity (kappa)

--------------------------------------------------

## Key Physics Modeled

- Advection (transport by fluid flow)
- Diffusion (spreading of species and heat)
- Reaction (heat-generating chemical process)
- Buoyancy (temperature-driven fluid motion)

--------------------------------------------------

## Key Results

- Lower kappa → strong heat accumulation → thermal runaway
- Higher kappa → smooth diffusion → stable system
- Clear plume formation due to buoyancy effects
- Rayleigh number increased significantly with decreasing kappa

--------------------------------------------------

## My Contribution

- Implemented reaction and heat coupling in Basilisk
- Designed and executed parametric study (kappa variation)
- Developed Python scripts for post-processing
- Generated plots and flow visualization videos
- Structured full CFD workflow from simulation to analysis

--------------------------------------------------

## Tools & Technologies

- Basilisk (CFD solver)
- C programming
- Python (NumPy, Matplotlib)
- MkDocs (documentation)
- GitHub (version control)

--------------------------------------------------

## Applications

- Combustion systems
- Thermal runaway analysis (batteries)
- Fire and smoke plume modeling
- Natural convection problems

--------------------------------------------------

## Questions This Project Answers

- How does diffusion affect stability in reactive systems?
- What causes thermal runaway?
- How does buoyancy generate flow?
- How are coupled PDEs solved numerically?

--------------------------------------------------

## One-Line Summary

This project demonstrates how reaction, heat transfer, and fluid flow interact to produce buoyancy-driven plume formation in a coupled CFD simulation.
