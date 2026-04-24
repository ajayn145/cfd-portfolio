## Flowchart — cavity.c Logic

Start
  |
  v
Initialize Domain & Grid
  |
  v
Apply Boundary Conditions
  |
  v
Initialize Velocity Field (u = 0)
  |
  v
---------------------------------
|        Time Loop Begins        |
---------------------------------
  |
  v
Update Viscosity (mu)
  |
  v
Solve Navier–Stokes Equations
  |
  v
Check Time Condition
  |
  +----> Write Snapshot (every dt)
  |
  v
Advance Time
  |
  v
Is End Time Reached?
  |
  +---- No ----> Repeat Loop
  |
  +---- Yes ---> End Simulation
  
  
  
  
![cavity_code](figures/cavity_code.png)
