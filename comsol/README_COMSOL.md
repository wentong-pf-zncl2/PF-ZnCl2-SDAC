# COMSOL Model Documentation

## Model Setup (Section 3.2 in manuscript)

### Physics Interfaces
1. Mathematics → PDE Interfaces → General Form PDE (for phase field φ)
2. Heat Transfer → Heat Transfer in Solids (for temperature T)

### Geometry
- Rectangle: 12 × 12 (unit: nm, scale 1:20)
- Initial nucleus: Circle at center (0,0), radius 0.05

### Mesh
- Type: Mapped
- Distribution: 120 × 120 elements
- Maximum element size: 0.1
- Minimum element size: 6.75×10^-4

### Study Settings
- Type: Time Dependent
- Time step: 0.05
- Time range: 0 to 10 (adjust based on tau value)

### Key Parameters (from Table 1)
| Parameter | Value | Description |
|-----------|-------|-------------|
| T_m       | 1     | Dimensionless melting point |
| delta     | 0.04  | Anisotropy strength |
| gamma     | 10    | System parameter |
| alpha     | 0.9   | Material parameter |

### Equations Implemented
Equation (3): epsilon = epsilon0 * (1 + delta * cos(j * (theta - theta0)))
Equation (5): m = (alpha/pi) * arctan(gamma * (Tm - T))
Equation (6): Full phase-field equation
Equation (7): Temperature field equation

### How to Reproduce Figure 2 (tau series)
1. Open ZnCl2_Parametric_tau.mph
2. Study → Parametric Sweep
3. Add parameter tau: [0.003, 0.002, 0.001, 0.0005, 0.00036, 0.00034, 0.00032]
4. Click Compute All
5. Results → Export → Image

### How to Reproduce Figure 5 (K series)
1. Open ZnCl2_Parametric_K.mph
2. Set K values: [3.0, 2.2, 2.0, 1.9, 1.8, 1.7, 1.6]
3. Click Compute All

### Contact
For COMSOL model questions, please open an issue on GitHub.