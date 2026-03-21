# Symplectic vs Non-Symplectic Integrators in Orbital Dynamics

## Overview

This project presents a computational study of numerical integrators applied to the classical two-body gravitational problem.

The primary goal is to understand how **symplectic** and **non-symplectic** methods differ in preserving the long-term behavior of Hamiltonian systems.

Four integrators are analyzed:

- **Heun Method (RK2)** — non-symplectic  
- **Runge–Kutta 4 (RK4)** — non-symplectic  
- **Velocity Verlet** — symplectic  
- **Leapfrog (Kick–Drift–Kick)** — symplectic  

The study focuses on how these methods affect orbital stability, conservation laws, and geometric structure over long simulations.

---

## Physical Model

The system simulated is the classical **two-body gravitational problem**:

d²r/dt² = −GM r / |r|³  

The gravitational parameter is normalized:

GM = 1  

Initial conditions correspond to a circular orbit:

Position: (1, 0)  
Velocity: (0, 1)  

---

## Integrators Studied

### Heun Method (RK2)
A second-order predictor–corrector scheme. It improves local accuracy over Euler but does not preserve the Hamiltonian structure, leading to energy growth.

### Runge–Kutta 4 (RK4)
A fourth-order method with excellent per-step accuracy. However, it is non-symplectic and exhibits slow secular drift over long simulations.

### Velocity Verlet
A second-order symplectic integrator widely used in physics. It preserves the geometric structure of phase space, resulting in bounded energy error.

### Leapfrog
A symplectic method equivalent to Velocity Verlet in a staggered formulation. It produces identical long-term behavior while using half-step velocity updates.

---

## Analysis Performed

The integrators are evaluated using multiple diagnostics:

### Orbit Geometry
Trajectory evolution in real space (x, y)

### Energy Conservation
Absolute energy error over time

### Radius Stability
Deviation from ideal circular orbit

### Phase Space Structure
Projected phase space (x, v_x) to analyze geometric preservation

### Angular Momentum Conservation
Deviation from exact angular momentum

### Timestep Sensitivity
Maximum energy error vs timestep size (convergence behavior)

---

## Key Results

- **Heun** exhibits strong energy growth and unstable orbits  
- **RK4** maintains high short-term accuracy but shows slow secular drift  
- **Velocity Verlet and Leapfrog** preserve bounded energy and stable trajectories  
- Symplectic methods maintain phase-space structure and conserved quantities over long times  
- Velocity Verlet and Leapfrog produce **indistinguishable results**, confirming their equivalence  

---

## Tools Used

- Python  
- NumPy  
- Matplotlib  
- Google Colab  

---

## Purpose

This project demonstrates how **algorithmic structure matters more than order** in long-term simulations of Hamiltonian systems.

It highlights why symplectic integrators are the standard choice in:

- Orbital mechanics  
- Molecular dynamics  
- Plasma physics  
- Long-time dynamical simulations  

---

## Future Work

- Extend to elliptical orbits (e ≠ 0)  
- Perform long-time simulations (10⁵+ steps)  
- Compare with higher-order symplectic methods  
- Extend to N-body systems  

---

## License

This project is released under the MIT License.
