# Chapter 12: Etch Rate Control and Uniformity Compensation Algorithms

## 12.1 Etch Rate Feedback Control

**Challenge:** Etch rate varies due to:
- Chamber drift (wall buildup, electrode erosion)
- Workload-dependent effects (pattern density)
- Thermal drift during extended etch cycles

**Compensation:** Real-time measurement and process adjustment

### 12.1.1 Etch Rate Monitoring Methods

**Real-time estimates:**
1. **Ion current measurement:** Higher ion current → faster etch rate
2. **Optical emission spectroscopy (OES):** Plasma spectra correlate with etch rate
3. **Pressure change rate:** Etch rate affects byproduct generation → pressure change

**Post-process verification:**
- Cross-section SEM: Direct depth measurement
- Ellipsometry: Non-destructive depth measurement (used on test wafers)

### 12.1.2 Feedback Algorithm

**Simple proportional control:**

$$P(t) = P_0 + K_p (E_{	ext{target}} - E_{	ext{measured}})$$

Where:
- P(t) = RF power at time t
- E_measured = real-time etch rate estimate
- K_p = proportional gain (typically 0.1-0.5)

**Result:** Adjusts power to maintain constant etch rate ±5-10%

## 12.2 ARDE (Aspect Ratio Dependent Etch) Mitigation

### 12.2.1 ARDE Problem

**Observation:** Etch rate varies with local aspect ratio

- Isolated holes (AR ~50:1): Etch rate ≈ 1.5 μm/min
- Dense holes (AR ~150:1): Etch rate ≈ 0.8 μm/min

**Mechanism:** Neutral depletion at higher local AR

### 12.2.2 ARDE Compensation

**Approach 1: Conservative etch time**
- Use slow etch rate (target dense-hole rate)
- Isolated holes etch slightly slower; acceptable trade-off
- Simple; no real-time feedback needed

**Approach 2: Pattern-dependent bias**
- Apply different power to center vs. edge (advanced systems only)
- Center typically has higher AR (denser) → apply more power there

**Approach 3: Dynamic recipe adjustment**
- Increase power in later stages of etch (when global AR higher due to depth)
- Partially compensates for natural ARDE trend

**Effectiveness:** Can reduce ARDE variation from 3-4× down to 1.5-2×; cannot eliminate completely

## 12.3 Uniformity Compensation

### 12.3.1 Radial Non-Uniformity Correction

**Problem:** Center often etches faster/slower than edge (depends on inlet design)

**Typical pattern:** Center etch rate 5-15% higher than edge (due to better gas access)

**Correction methods:**

1. **Passive (hardware):** Optimize inlet and cooling design (most effective)
2. **Active (recipe):** Adjust pressure, power radially (limited by symmetry constraints)
3. **Temporal:** Adjust power/pressure during etch to correct historical trends

### 12.3.2 Recursive Optimization

**Method used in advanced production systems:**

1. **Etch test wafer:** Record depth uniformity across 25-49 points
2. **Analyze:** Fit surface to identify systematic patterns (radial, azimuthal)
3. **Adjust recipe:** Modify gas flow or power based on observed drift
4. **Repeat:** Continue until uniformity converges to <5%

**Convergence:** Typically 3-5 recipe iterations to achieve stable uniformity

## 12.4 Ion-Neutral Balance Control

**Key insight:** Etch selectivity depends on ion-to-neutral ratio

**Ion flux:** Proportional to plasma density, which scales with power

**Neutral flux:** Proportional to gas flow rate

**Ratio:** Ion/Neutral ratio = (Power) / (Gas flow)

**Selectivity tuning:**

- High Ion/Neutral ratio (high power, low gas): Si-selective (ions preferentially etch Si)
- Low Ion/Neutral ratio (low power, high gas): Material-neutral (all etch similarly)
- Optimal ratio depends on target selectivity requirement

---

**Key Points:**
1. Real-time etch rate feedback keeps rate ±5-10% of target
2. ARDE variation can be reduced from 3-4× to 1.5-2× via compensation
3. Radial uniformity <5% achievable with active feedback
4. Ion/Neutral ratio directly controls selectivity

*Next: Chapter 13*
