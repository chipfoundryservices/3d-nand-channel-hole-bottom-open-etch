# Appendix E: Thermal Simulation Data and Cooling Design

## E.1 Wafer Temperature vs. Power and Coolant Temperature

**Calculated wafer surface temperature (°C) during sustained etch:**

| Coolant Temp (°C) | 3 kW | 5 kW | 7 kW | 9 kW |
|------------|------|------|------|------|
| 10 | 45 | 60 | 75 | 88 |
| 15 | 50 | 65 | 80 | 93 |
| 20 | 55 | 70 | 85 | 98 |

**Assumptions:**
- Chuck thermal resistance: 1.0 K·cm²/W
- Chamber radiant coupling: ~10°C at 80°C operation
- Gas convection contribution: ~5°C

**Safe operating zone:** Wafer temp ≤ 85°C (shaded region above)

## E.2 Transient Temperature Response

**Wafer temperature rise vs. time after power on (5 kW, 15°C coolant):**

| Time (min) | Wafer Temp (°C) | Temperature Rise Rate (°C/min) |
|---------|-------|-----------|
| 0 | 35 | - |
| 5 | 55 | 4.0 |
| 10 | 68 | 2.6 |
| 20 | 75 | 0.7 |
| 30 | 78 | 0.3 |
| 50 | 80 | 0.1 |

**Time constant:** ~15-20 minutes to reach steady-state (~80°C)

## E.3 Cooling System Specifications

**Required cooling capacity for 7 kW chamber etch + 3 kW ash:**

| Mode | Heat Load | Coolant Flow | Temp Rise |
|------|-----------|-------------|-----------|
| Etch (7 kW) | 1.4 kW to wafer | 3 L/min | 25°C rise |
| Ash (3 kW) | 0.6 kW to wafer | 2 L/min | 10°C rise |
| Electrode (avg) | 1-2 kW | 2 L/min | 15°C rise |

**Chiller specifications:**
- Cooling capacity: >5 kW
- Temperature stability: ±1°C
- Flow rate: >5 L/min total

---

*See Chapter 9 for thermal management design.*
