# Phase-Field Simulation of ZnCl₂ Dendritic Growth in Sludge-Derived Activated Carbon

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20319718.svg)](https://doi.org/10.5281/zenodo.20319718)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📄 Manuscript
This repository supports the manuscript submitted to *Computational Materials Science*:
&gt; **"Phase-Field Simulation of ZnCl₂ Molten Salt Preparation of Sludge-Derived Activated Carbon"**

## 🔬 Overview
This project simulates the ZnCl₂ dendritic crystallization process during sludge-derived activated carbon (SDAC) preparation using the phase-field method. The model is built upon the Ryo Kobayashi pure substance phase-field model with modified temperature field equations.

Key simulation parameters (from Table 1 in manuscript):
- Melting point Tₘ = 274 °C
- Thermal conductivity k = 3.0 W/(m·K)
- Anisotropy strength δ = 0.04
- Anisotropy mode j = 6

## 📁 Repository Structure

### `comsol/` — COMSOL Multiphysics 6.1 Models
- `ZnCl2_PhaseField_Main.mph`: Main phase-field model (Eq. 1-7 in manuscript)
  - Domain: 12×12 (scale 1:20 nm)
  - Mesh: Mapped 120×120, max element 0.1
  - Time step: 0.05
  - Initial nucleus: center position, radius 0.05
- Parameter sweep models for τ, K, θ₀, j, ε₀

### `matlab/` — MATLAB Analysis Scripts
- `dendrite_area_ratio*.m`: Calculates crystal area ratio (Fig. 3d)
- `plot_dendrite_morphology.m`: Generates dendrite morphology plots
- `BET_data_process.m`: Processes BET surface area and pore volume data (Table 2)

### `data/` — Raw Data
- `experiment/area_ratio_summary.txt`: Dendrite area ratios from simulation (Fig. 3d)
- `experiment/BET_results*.csv`: Experimental BET surface area and pore volume (Table 2)

### `figures/` — High-Resolution Manuscript Figures
- Original PNG files for all manuscript figures (300 DPI)

## 🛠️ Requirements

### COMSOL
- **COMSOL Multiphysics 6.1** (or later)
- Required modules: Mathematics → PDE Interfaces, Heat Transfer
- License: Required to open .mph files

### MATLAB
- **MATLAB R2022a** or later
- Required Toolbox: Image Processing Toolbox
- No additional custom toolboxes needed

## 🚀 Quick Start

### 1. Reproduce Phase-Field Simulation
1. Open COMSOL 6.1
2. File → Open → Select `comsol/ZnCl2_PhaseField_Main.mph`
3. In Model Builder: 
   - Study 1 → Step 1: Time Dependent
   - Set Time range: `range(0, 0.05, 10)` (adjust as needed)
   - Click Compute
4. Results → Export → Image to save dendrite morphology

### 2. Reproduce Parametric Study (Fig. 2-3)
1. Open `comsol/ZnCl2_Parametric_tau1.mph`
2. Study → Parametric Sweep
3. Add parameter `tau`: [0.003, 0.002, 0.001, 0.0005, 0.00036, 0.00034, 0.00032]
4. Click Compute All
5. Export results to `data/experiment/`

### 3. Run MATLAB Analysis
```matlab
% In MATLAB Command Window:
cd('matlab/')
dendrite_area_ratio0.5        % Generates Fig. 3d data

## 📊 Data Availability
All simulation and experimental data are openly available:
- **GitHub**: https://github.com/wentong-pf-zncl2/PF-ZnCl2-SDAC
- **Zenodo Archive**: https://doi.org/10.5281/zenodo.20319718 (DOI: 10.5281/zenodo.20319718)
