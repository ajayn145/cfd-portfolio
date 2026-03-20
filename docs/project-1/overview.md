# Project 1: Reactive Scalar Transport Solver

## Objective

To develop a 2D CFD solver for scalar transport including advection, diffusion, and reaction using Basilisk.

## Problem Description

A scalar concentration field (C) is initialized as a Gaussian blob and transported in a uniform velocity field. The scalar undergoes:

- Advection (transport by flow)
- Diffusion (spreading due to gradients)
- Reaction (decay over time)

## Applications

This type of model is fundamental in:

- Pollutant transport in air and water
- Combustion (fuel species transport)
- Heat and mass transfer problems
- HVAC airflow and contaminant dispersion

## Key Features

- Finite-volume formulation (Basilisk)
- Transient simulation
- Reaction kinetics implementation
- Visualization using PPM → MP4 pipeline
