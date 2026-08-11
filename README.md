# Plasma-Digital-Twin-CCP-Reactors


## Physics-Based Modeling → COMSOL Multiphysics → Machine Learning

A computational framework for developing a digital twin of an
argon capacitively coupled plasma (CCP) reactor by integrating
zero-dimensional plasma modeling, COMSOL Multiphysics simulations,
large-scale parameter sweeps, and machine-learning surrogate models.

---

## Project Overview

This project aims to develop a computationally efficient digital
twin capable of predicting plasma characteristics and identifying
operating/design conditions that improve plasma uniformity.

The project follows a hierarchical modeling approach:

0D Plasma Model
        ↓
COMSOL Multiphysics
        ↓
Parametric Simulation
        ↓
Dataset Generation
        ↓
Machine Learning Surrogate
        ↓
Optimization

---

## Objectives

- Develop a simplified 0D plasma model
- Build a physics-based CCP model in COMSOL
- Perform parametric sweeps over reactor parameters
- Generate a large simulation dataset
- Train ML surrogate models
- Predict plasma properties without running full COMSOL simulations
- Identify operating conditions that improve plasma uniformity

---

## Modeling Framework

### 1. Zero-Dimensional Model

The project initially begins with a simplified 0D plasma model
to understand the fundamental dependence of plasma properties on
operating conditions.

Key quantities include:

- Electron density
- Electron temperature
- Ionization rate
- Power deposition
- Plasma potential

[Read the 0D model documentation](docs/0d_model.md)

---

### 2. COMSOL Multiphysics Model

The physics-based model is implemented in COMSOL Multiphysics
using an argon capacitively coupled plasma configuration.

Key parameters include:

| Parameter | Symbol | Baseline |
|---|---:|---:|
| RF frequency | f₀ | 13.56 MHz |
| Input power | P₀ | 1 W |
| Discharge gap | L | 2.54 cm |
| Inner radius | R₁ | 5.38 cm |
| Outer radius | R₂ | 10.16 cm |
| Dielectric thickness | d | 3 mm |

The model is used to investigate the influence of reactor geometry
and operating conditions on plasma behavior.

[Read the COMSOL documentation](docs/comsol_model.md)

---

### 3. Parametric Sweeps

Parameter sweeps are performed over quantities such as:

- RF power
- Discharge gap
- Electrode radius
- Dielectric thickness
- Pressure
- Frequency

For each simulation, quantities such as plasma density,
electron temperature, ionization rate and power deposition are
extracted.

---

### 4. Dataset Generation

The COMSOL simulations are converted into a structured dataset
for machine-learning applications.

Example features:

```text
Input Parameters
----------------
Power
Pressure
Frequency
Electrode Radius
Discharge Gap
Dielectric Thickness

Target Variables
----------------
Mean Plasma Density
Maximum Plasma Density
Minimum Plasma Density
Electron Temperature
Ionization Rate
Power Deposition
Uniformity
