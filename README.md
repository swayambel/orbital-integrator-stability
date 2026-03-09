# Symplectic vs Non-Symplectic Integrators in Orbital Dynamics

## Overview

This project investigates how different numerical integrators behave when simulating orbital motion in a gravitational two-body system.

The focus of the study is the distinction between **symplectic** and **non-symplectic** integration methods and how this affects long-term stability in dynamical simulations.

Three integrators are compared:

* **Heun Method** (Improved Euler) — non-symplectic
* **Runge–Kutta 4 (RK4)** — non-symplectic
* **Velocity Verlet** — symplectic

The goal is to analyze how these algorithms influence orbital stability, energy conservation, and radius drift during long simulations.

---

## Physical Model

The system simulated is the classical **two-body gravitational problem** governed by Newton's law of gravitation:

d²r/dt² = −GM r / |r|³

where:

* **G** is the gravitational constant
* **M** is the central mass
* **r** is the position vector

For simplicity, the gravitational parameter is normalized:

GM = 1

Initial conditions correspond to a circular orbit:

Position: (1, 0)
Velocity: (0, 1)

---

## Integrators Studied

### Heun Method (Improved Euler)

A second-order predictor–corrector method that improves upon the Euler method by averaging derivatives at two points. Although more accurate than Euler, it does not preserve the Hamiltonian structure of the system.

### Runge–Kutta 4 (RK4)

A fourth-order integrator that evaluates the derivative four times per timestep. It significantly reduces local truncation error but is **not symplectic**, meaning long-term energy drift can still occur.

### Velocity Verlet

A **symplectic integrator** commonly used in molecular dynamics and orbital simulations. Symplectic methods preserve the geometric structure of Hamiltonian systems, leading to improved long-term stability.

---

## Analysis Performed

The behavior of each integrator is evaluated using several diagnostics:

### Orbit Geometry

The orbital trajectories are plotted to visually inspect how each method maintains (or distorts) the orbit over time.

### Energy Drift

Specific mechanical energy is tracked throughout the simulation to evaluate how well each integrator conserves energy.

### Radius Drift

The orbital radius is monitored over time to detect gradual expansion or contraction of the orbit.

### Long-Term Stability

Simulations are run for a large number of timesteps to highlight differences between symplectic and non-symplectic methods.

---

## Key Expectations

Typical behavior observed in orbital simulations:

* Non-symplectic methods often show **gradual energy drift** over long timescales.
* Symplectic integrators tend to keep energy **bounded and oscillatory**, rather than drifting away.
* This difference becomes more pronounced during long simulations.

---

## Project Structure

symplectic-vs-nonsymplectic-integrators/

README.md — project documentation
symplectic_integrator_analysis.ipynb — main analysis notebook
LICENSE — MIT license

---

## Tools Used

Python
NumPy
Matplotlib
Google Colab

---

## Purpose of the Project

This project demonstrates how algorithmic choices influence the stability of numerical simulations in orbital dynamics. It highlights the importance of symplectic integrators for long-term simulations of Hamiltonian systems such as planetary motion.

---

## Future Work

Possible extensions include:

* Implementing Leapfrog and other symplectic schemes
* Studying angular momentum conservation
* Performing timestep sensitivity analysis
* Extending the simulation to N-body systems

---

## License

This project is released under the MIT License.
