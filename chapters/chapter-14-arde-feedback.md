# Chapter 14: Aspect Ratio Dependent Etching (ARDE) Feedback and Correction

## 14.1 ARDE Quantification

**Etch rate as function of aspect ratio:**

$$E(AR) = E_{max} \cdot f(AR)$$

Where $f(AR) = \frac{1}{1 + k \cdot AR}$ (empirical model)

**Typical values for Cl₂-based 3D NAND etch:**

| AR (aspect ratio) | f(AR) | Etch Rate |
|-------------|-------|-----------|
| 20:1 | 0.75 | 1.1 μm/min |
| 50:1 | 0.50 | 0.8 μm/min |
| 100:1 | 0.33 | 0.5 μm/min |
| 150:1 | 0.25 | 0.4 μm/min |

**ARDE factor:** Ratio of highest to lowest rate ≈ 2-3× for 20-150:1 AR range

## 14.2 ARDE Root Cause

**Primary:** Neutral radical depletion in high-AR holes

- Neutral diffusion depth limited to ~1-3 μm (hole diameters)
- Deeper portions of hole increasingly ion-limited
- Ion current also limited by sheath geometry
- Result: High-AR features etch 2-3× slower than low-AR features

## 14.3 ARDE Feedback Correction

### 14.3.1 Aspect Ratio Estimation

**Challenge:** Real-time AR during etch is unknown

**Solution:** **Estimate AR based on etch progress:**

$$AR(t) = \frac{\text{etch depth}(t)}{\text{hole diameter}} = \frac{E(t) \cdot t}{d}$$

Where E(t) = etch rate estimate at time t, d = hole diameter (~300 nm)

**Aspect ratio increases during etch:** Starts at ~50:1, increases to ~200:1 over 45-minute cycle

### 14.3.2 Adaptive Power Control

**Strategy:** Increase power as etch progresses to compensate for ARDE

**Algorithm:**

$$P(t) = P_{base} + K_{ARDE} \cdot AR(t)$$

Where K_ARDE is ARDE compensation gain (~0.1-0.3 kW per 100:1 AR)

**Example:**
- t=0 min: AR=50:1 → P = 5 kW
- t=20 min: AR=100:1 → P = 5 + 0.2 = 5.2 kW
- t=40 min: AR=150:1 → P = 5 + 0.3 = 5.3 kW

**Effectiveness:** Reduces ARDE variation from 3× to ~1.5×

### 14.3.3 Dynamic Gas Flow Adjustment

**Alternative/complementary strategy:** Increase gas flow in later stages

Higher gas flow → more neutrals available → reduces neutral depletion effect

**Trade-off:** Increased gas flow can affect pressure uniformity

## 14.4 Pattern-Dependent ARDE (Microloading)

**Beyond bulk ARDE:** Local aspect ratio variation within pattern

**Example:**
- Isolated hole (surrounded by open space): AR = 50:1 (local view)
- Dense cluster hole (surrounded by many other holes): AR = 100:1 (effective local AR)

**Result:** CD variation ±5-10% within single wafer due to microloading

## 14.5 ARDE Lookup Tables

**Production approach:** Pre-calculated lookup tables of expected etch depth vs. aspect ratio

**Method:**
1. Etch test wafers with known patterns (isolated vs. dense)
2. Measure depth uniformity across pattern variations
3. Build table: AR → expected depth correction

**Use:** Compare actual measured depth to lookup table; if drift detected, adjust future recipe parameters

**Table format:**

| Pattern Type | Local AR | Expected Depth Ratio |
|------------|---------|----------------------|
| Isolated | 50:1 | 1.0 (reference) |
| Medium density | 80:1 | 0.85 |
| High density | 120:1 | 0.65 |
| Very high density | 150:1 | 0.55 |

## 14.6 Advanced ARDE Compensation

### 14.6.1 Machine Learning Approach

**Emerging technique:** Train neural network on historical process data

**Inputs:** Current time, estimated AR, previous etch rate measurements

**Output:** Predicted etch rate; optimal power/pressure setting to maintain target rate

**Status:** Experimental in some advanced fabs; not yet widespread

### 14.6.2 Coupled Simulation

**High-fidelity approach:** Couple fluid dynamics, plasma chemistry, and materials models

**Capability:** Predict ARDE behavior for new chemistries or chamber designs before building hardware

**Status:** Research tool; too slow for real-time control

---

**Key Points:**
1. ARDE causes 2-3× etch rate variation across 20-150:1 AR range
2. Root cause: Neutral depletion + ion current limitation at high AR
3. Power increase during etch compensates; reduces ARDE to ~1.5×
4. Pattern-dependent microloading adds local variation
5. Lookup tables and machine learning emerging for advanced compensation

*Next: Chapter 15*
