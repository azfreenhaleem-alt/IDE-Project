# Solow-Swan Growth Model: Numerical & Analytical Simulation

This repository contains a Python-based numerical and analytical simulation of the **Solow-Swan Growth Model** featuring a structural savings rate shock. The simulation tracks capital accumulation, consumption dynamics, and output growth per worker over time, demonstrating how an economy transitions between two distinct steady states.

## Model Overview
The Solow-Swan model is simulated with standard textbook parameter values under the assumption of technological progress ($g$) and population growth ($n$). At $t = 20$ years, the economy experiences a **structural shock** where the savings rate permanently increases from an initial low rate to a higher rate.

### Parameters Used
- **Alpha ($\alpha$):** $1/3$ (Capital share of output)
- **Delta ($\delta$):** $0.05$ (Depreciation rate)
- **Population Growth ($n$):** $0.02$
- **Tech Growth ($g$):** $0.02$
- **Initial Savings Rate ($s_{old}$):** $0.20$
- **New Savings Rate ($s_{new}$):** $0.50$
- **Shock Time ($t_{shock}$):** Year $20$

---

## Key Theoretical Metrics

When evaluating the new economy ($s = 0.50$), the calculated structural parameters and steady-state values are:

| Metric | Code Variable | Value | Description |
| :--- | :--- | :--- | :--- |
| **New Steady-State Capital ($k^*$)** | `k_star` | `13.094570` | Long-run capital per effective worker |
| **New Steady-State Output ($y^*$)** | `y_star` | `2.357023` | Long-run output per effective worker |
| **Golden Rule Capital ($k_{gold}$)** | `k_golden` | `7.127781` | Capital level maximizing consumption |
| **Golden Rule Savings ($s_{gold}$)** | `s_golden` | `0.333333` | Savings rate maximizing consumption ($\equiv \alpha$) |
| **Convergence Speed ($\lambda$)** | `lambda` | `0.060000` | Rate of convergence toward steady state |
| **Half-Life ($t_{1/2}$)** | `half_life` | `11.552453` | Years required to close half the gap to $k^*$ |

---

## Features & Implementation

The implementation is written in a Python Jupyter Notebook using standard scientific computing libraries:
* **`scipy.integrate.solve_ivp`**: Utilized to solve the non-linear ordinary differential equation (ODE) governing capital accumulation numerically.
* **Analytical Grounding**: The numerical path is strictly verified against the model's exact closed-form analytical solution.
* **High Precision**: The maximum absolute error between the numerical solution and analytical formula is exceptionally low ($~4.41 \times 10^{-9}$), verifying the simulation's robustness.

---

## Visualizing the Transition Dynamics

The simulation outputs three distinct subplots tracking the economy across a 100-year horizon:

1. **Capital per Effective Worker ($k(t)$)**
   - The economy starts at its old steady state. Following the savings rate increase at Year 20, capital begins accumulating rapidly toward the new higher steady state ($k^* \approx 13.09$).
   - The plot shows a perfect overlay between the **analytical curve** and the **numerical data points**.

2. **Consumption per Effective Worker**
   - At Year 20, consumption drops sharply because a larger fraction of income is suddenly routed away from consumption into savings.
   - Over time, as the newly accumulated capital makes workers more productive, total output rises, allowing consumption to recover and eventually surpass its pre-shock level.

3. **Output per Worker (Log Scale)**
   - Reflects the real growth path of actual output per worker ($A(t) \cdot y$).
   - The log scale clearly displays a constant steady slope driven by technological progress ($g$), with a visible kink and acceleration after Year 20 due to transitional capital accumulation.

---

## Requirements

To run this notebook, ensure you have the following packages installed:

```bash
pip install numpy pandas matplotlib scipy
```

## Usage
Simply clone this repository and run the Jupyter Notebook in your preferred environment (e.g., VS Code or Jupyter Lab):
```bash
git clone https://github.com
code YOUR_NOTEBOOK_NAME.ipynb
```
