# Appendix B: Etch Rate Scaling Laws and Power Correlations

## B.1 Empirical Etch Rate Models

**Power-law model (widely used):**

$$E = E_0 \\cdot P^\\alpha \\cdot P^\\beta \\cdot T^\\gamma$$

Typical exponents:
- α (power dependence): 0.5-1.0
- β (pressure dependence): 0.3-0.8
- γ (temperature dependence): 0.04-0.06 (1/°C)

**Example (Cl₂ SiO₂ etch):**

$$E(\\text{μm/min}) = 0.1 \\cdot P^{0.7} \\cdot (1 + 0.02 \\cdot \\Delta T)$$

Where P is power in kW, ΔT is temperature above 60°C

## B.2 Temperature Sensitivity

**Arrhenius form:**

$$E(T) = E_0 \\exp\\left(\\frac{E_a}{R} \\left(\\frac{1}{T_0} - \\frac{1}{T}\\right)\\right)$$

**Typical activation energies for Si/SiO₂:**
- Si etch: E_a ~20-30 kJ/mol
- SiO₂ etch (F-based): E_a ~15-25 kJ/mol
- SiO₂ etch (Cl-based): E_a ~30-50 kJ/mol

**Doubling rate:** Occurs for ~20-40°C temperature increase

## B.3 Pressure Scaling

**Etch rate vs. pressure (typical Cl₂/BCl₃):**

| Pressure (Pa) | Relative Rate |
|-------------|---------------|
| 30 | 0.6 |
| 50 | 1.0 (reference) |
| 70 | 0.95 |
| 100 | 0.7 |

**Shape:** Peak at 40-60 Pa; rolls off at higher and lower pressures

## B.4 Ion Current Scaling

**Ion flux (mA/cm²) vs. power and pressure:**

$$j_i = j_0 \\cdot \\left(\\frac{P}{P_0}\\right)^{0.6} \\cdot f(P_{pressure})$$

Where j₀ ~0.5 mA/cm² at 3 kW, 50 Pa baseline

**Effect on etch rate:**

Total rate = Chemical rate + 0.1 × j_i (sputtering contribution)

Sputtering becomes dominant only at very high power (>8-10 kW)

---

*See Chapter 11-12 for process parameter effects and control strategies.*
