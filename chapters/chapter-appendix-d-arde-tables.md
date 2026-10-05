# Appendix D: ARDE Compensation Lookup Tables

## D.1 Etch Rate vs. Aspect Ratio (Cl₂/BCl₃, 60 Pa, 5 kW)

| Aspect Ratio | Normalized Rate | Etch Rate (μm/min) | Depth per 1 min |
|------------|-------|----------|----------|
| 20:1 | 1.00 | 1.5 | 1.5 μm |
| 40:1 | 0.75 | 1.1 | 1.1 μm |
| 60:1 | 0.60 | 0.9 | 0.9 μm |
| 80:1 | 0.50 | 0.75 | 0.75 μm |
| 100:1 | 0.42 | 0.63 | 0.63 μm |
| 120:1 | 0.36 | 0.54 | 0.54 μm |
| 150:1 | 0.30 | 0.45 | 0.45 μm |

**ARDE correction:** Increase power by ~0.05 kW per increase of 20 in AR to maintain constant etch rate

## D.2 Power Adjustment for ARDE Compensation

| Stage | Time Elapsed | Estimated AR | Baseline Power | ARDE Correction | Total Power |
|-------|-----------|--------|----------|-------|----------|
| 1 | 0-10 min | 50:1 | 5.0 kW | 0 | 5.0 kW |
| 2 | 10-20 min | 80:1 | 5.0 kW | +0.1 | 5.1 kW |
| 3 | 20-30 min | 120:1 | 5.0 kW | +0.2 | 5.2 kW |
| 4 | 30-40 min | 150:1 | 5.0 kW | +0.25 | 5.25 kW |
| 5 | 40-45 min | 180:1 | 4.5 kW | +0.2 | 4.7 kW (reduce for final endpoint) |

**Result:** Etch rate variation reduced from ±30% to ±10%

---

*See Chapter 14 for ARDE feedback algorithm details.*
