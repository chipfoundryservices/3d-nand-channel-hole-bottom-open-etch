# Chapter 15: Etch Bowing and Critical Dimension Runout (CDR) Management

## 15.1 Etch Bowing Definition and Causes

**Bowing:** Non-linear sidewall deflection in deep trenches

**Types:**

1. **Concave bowing:** Sidewalls bow inward (diameter smaller at bottom)
2. **Convex bowing:** Sidewalls bow outward (diameter larger at bottom)
3. **S-bowing:** Combination (inward near top, outward near bottom)

**Specification:** <1-2% diameter variation acceptable; >5% causes electrical failure

## 15.2 Root Causes of Bowing

### 15.2.1 Temperature Gradient Bowing

**Mechanism:** Bottom of trench is cooler than top (less heat input there)

- Bottom: ~60-70°C
- Top/opening: ~80-100°C

**Effect:** Lower temperature → lower etch rate → bottom etches slower → concave bowing

**Solution:** Improve thermal uniformity; increase bottom temperature via increased gas temperature or reduced heat loss

### 15.2.2 Ion Energy Gradient

**Mechanism:** Ions in deep trench lose energy via collisions

- Top of trench: High ion energy (~150 eV)
- Bottom of trench: Low ion energy (~50 eV) after collisions

**Effect:** Lower ion energy at bottom → different selectivity/etch rate → bowing

**Solution:** Lower operating pressure to reduce collisions; increase sheath voltage to compensate for energy loss

### 15.2.3 Neutral Depletion Bowing

**Mechanism:** Neutral species depleted with depth

- Top: High neutral flux
- Bottom: Low neutral flux (depletion)

**Effect:** Different etch mechanism at top vs. bottom → different profile

**Solution:** Increase gas flow; add inert diluent (Ar) for neutral transport

### 15.2.4 Stress-Induced Bowing

**Mechanism:** Residual stress in materials (polysilicon, nitride) gets relieved during etch

**Effect:** Stress relief → sidewall curvature changes → bowing

**Solution:** Control processing history upstream (deposition conditions); less controllable in etch

## 15.3 Critical Dimension Runout (CDR)

**Definition:** Undesired variation in hole diameter across wafer and within pattern

**Components:**

1. **Radial CDR:** Center vs. edge variation (typically <3-5%)
2. **Pattern-dependent CDR:** Isolated vs. dense hole variation (typically ±5-10%)
3. **Bowing CDR:** Top vs. bottom diameter (typically ±1-3%)

**Total allowable CDR:** ±15-30 nm for 300 nm nominal hole diameter

## 15.4 Uniformity Compensation for Bowing

### 15.4.1 Power Staging

**Strategy:** Adjust power at different etch stages to compensate for known bowing patterns

**Example (if experiencing concave bowing):**
- Early etch (0-20 min): Reduce power slightly (slower etch; protects bottom)
- Later etch (20-40 min): Increase power (accelerates bottom etch rate)
- Final approach: Moderate power (careful endpoint)

**Effect:** Partially compensates for temperature/ion/neutral gradients

### 15.4.2 Pressure Staging

**Alternative strategy:** Modify pressure to change transport characteristics

- Higher pressure: Better neutral transport (helps deep regions)
- Lower pressure: Better ion collimation (focuses ions on bottom)

**Trade-off:** Pressure changes affect selectivity; must coordinate with chemistry phases

### 15.4.3 Temperature Profile Optimization

**Passive method:** Chamber design to ensure wafer bottom stays warm

- Improved insulation of chuck backside
- Gas inlet heated (slightly)

**Active method:** Actively heat bottom during etch (challenging; not common)

## 15.5 Measurement and Monitoring

### 15.5.1 Cross-Section SEM

**Gold standard for bowing measurement**

- Slice wafer through hole region
- Mount cross-section and image with SEM
- Measure sidewall profile; quantify bowing angle

**Drawback:** Destructive; expensive; not suitable for 100% inspection

### 15.5.2 In-Line Metrology

**Non-destructive techniques:**

1. **Atomic Force Microscopy (AFM):** Profile hole opening; infer profile
2. **Focused Ion Beam (FIB) cross-section:** Semi-destructive; faster than SEM sample prep
3. **Optical profiling:** Recent advances in confocal microscopy for deep trenches

## 15.6 Design-for-Manufacturing (DFM) Strategies

### 15.6.1 Hole Diameter Design

**Larger holes (400-500 nm):** Easier to etch; less bowing due to better transport

**Smaller holes (200-300 nm):** Tighter CD control; more challenging etch; more bowing risk

**Trade-off:** Larger holes mean lower density; smaller holes favor density but increase defects

### 15.6.2 Pattern Layout Considerations

**Isolated holes:** Etch uniformly; fast; good CDR

**Dense patterns:** Mutual shielding; slower etch; loading effects; higher CDR

**Design strategy:** Mix of sparse and dense regions to average out effects

---

**Key Points:**
1. Bowing primarily caused by temperature, ion energy, and neutral gradients with depth
2. Concave bowing (inward) most common; caused by cooler/lower-etch-rate bottom
3. Power staging, pressure tuning, and thermal optimization reduce bowing
4. Cross-section SEM is gold standard for measurement
5. Design-for-manufacturing (larger holes, mixed pattern density) helps

*Next: Chapter 16*
