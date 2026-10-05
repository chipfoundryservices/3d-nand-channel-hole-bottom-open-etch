# Chapter 11: Bias and RF Power Optimization for Vertical Sidewalls

## 11.1 Ion Energy and Sheath Voltage

**Plasma potential (V_p):** ~10-20 V above ground in typical discharge

**Sheath voltage:** V_sheath = plasma edge - electrode

**Ion energy at surface:** E_i = e · V_sheath (typically 50-150 eV for 3D NAND)

## 11.1.1 Ion Energy Effects

- **20-50 eV:** Chemical etch; good selectivity; lower rate
- **50-150 eV:** Ion-assisted etch; balanced rate/selectivity (OPTIMAL)
- **150-300 eV:** Sputtering-dominated; high rate but poor selectivity

## 11.2 RF Power Coupling and Matching

**CCP (Capacitive Coupling):** Direct RF coupling to electrode (standard)
- Frequency: 13.56 MHz
- Matching network goal: Minimize reflected power (<5%)
- Quality factor Q = 5-15 (relatively broadband)

**ICP (Inductive Coupling):** RF coil creates magnetic field
- Decoupled from electrode; higher plasma density possible
- More forgiving matching; 50-80% efficiency typical

## 11.3 Pressure-Temperature-Power (PTP) Phase Space

**Viable operating window for 176-layer etch:**

| Parameter | Minimum | Optimal | Maximum |
|-----------|---------|---------|---------|
| Pressure (Pa) | 40 | 50-70 | 80 |
| Temperature (°C) | 60 | 70-85 | 85 |
| Power (kW) | 3 | 5-7 | 10 |

- Outside this space: Poor uniformity, selectivity loss, or thermal runaway
- Selectivity most sensitive to pressure (3-5% change per % pressure variation)

## 11.4 Multi-Power Staging

**Strategy:**
1. Initial oxide etch: High power (7-8 kW)
2. Polysilicon etch: Medium power (5-6 kW)
3. Final approach: Low power (2-3 kW) - careful endpoint

**Pulsed RF:** Emerging technique; duty cycle 50-80%; reduces thermal load and residue

---

**Key Points:**
1. Optimal ion energy: 80-120 eV
2. Pressure is most critical parameter for selectivity
3. Multi-stage power improves uniformity and endpoint control
4. Pulsed RF reduces thermal load and residue formation

*Next: Chapter 12*
