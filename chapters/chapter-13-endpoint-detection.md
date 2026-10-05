# Chapter 13: Endpoint Detection and In-Situ Optical Monitoring

## 13.1 Optical Emission Spectroscopy (OES)

**Principle:** Monitor light emitted by plasma species during etch

**Wavelengths of interest (for Cl/F etch):**

| Species | Wavelength (nm) | Intensity increases when |
|---------|-----------------|------------------------|
| Cl (atomic) | 837.6 | Cl₂ dissociation active |
| F (atomic) | 703.0 | F-based chemistry active |
| C (atomic) | 193.0 | Hydrocarbon fragments present |
| O (atomic) | 776.0 | Ash/oxidation phase |

## 13.1.1 Material Transition Detection

**Transition 1 (Oxide → Polysilicon):**
- Cl emission increases (Si more reactive to Cl than SiO₂)
- Intensity ratio Cl/O increases sharply

**Transition 2 (Polysilicon → next Oxide layer):**
- Cl emission drops (entering lower-reactivity oxide layer)
- Transition detected; recipe switches to oxide-selective phase

**Transition 3 (Approaching etch stop at tungsten):**
- Characteristic signature change (Si/O/N lines disappear)
- Pressure may rise slightly (lower byproduct generation)

## 13.2 OES Hardware and Processing

### 13.2.1 Optical Setup

**Spectrometer specifications:**
- Wavelength range: 200-1000 nm (covers Cl, F, C, O, Ar)
- Resolution: 0.1-0.5 nm
- Sampling rate: 10-100 Hz (fast enough to catch layer transitions)

**Signal filtering:**
- Raw spectra noisy; smooth with moving average (10-100 point window)
- Subtract baseline (chamber-dependent background)

### 13.2.2 Endpoint Algorithms

**Simple threshold method:**
- Set threshold OES signal level
- When signal crosses threshold → endpoint reached
- Drawback: Prone to false triggers from noise

**Slope-based method:**
- Monitor rate of change of OES signal (dI/dt)
- Sharp negative slope → material transition
- More robust to noise

**Multi-parameter method (advanced):**
- Combine OES intensity, slope, pressure change, ion current
- Fuzzy logic or machine learning to detect endpoint
- Best performance; requires calibration per recipe

## 13.3 Pressure-Based Endpoint Detection

**Principle:** Etch rate affects byproduct generation → pressure change rate

**Observation:**
- During active etch: Pressure steady or slowly rising (byproduct generation)
- Reaching etch stop: Etch rate drops → pressure generation rate drops
- Pressure rise slows or plateaus → endpoint signal

**Advantage:** Simple; uses existing pressure gauge

**Disadvantage:** Slow response (~10-30 sec); limited sensitivity

## 13.4 Ion Current Monitoring

**Principle:** Higher ion current → faster etch; reaching etch stop → ion current drops

**Mechanism:**
- Measured at powered electrode (via current probe)
- Correlates with wafer current and etch rate

**Endpoint: Sharp drop in ion current when material changes from conductor (Si/W) to insulator (SiO₂/Si₃N₄)

**Advantage:** Very fast response (<100 ms)

**Disadvantage:** Depends on material electrical properties; not reliable for all transitions

## 13.5 Endpoint Challenges and Solutions

### 13.5.1 Multiple Transitions in Long Etch

**Problem:** 176-layer etch has ~176 layer transitions

**Solution:** **Stage-based endpoint detection**

1. **Macro-endpoint:** OES signal to detect major material transitions (e.g., first SiO₂ layer)
2. **Micro-endpoints:** Count expected time for each layer; use timing-based endpoints for layers 2-175
3. **Final endpoint:** Careful OES/pressure monitoring for last few micrometers (avoid tungsten over-etch)

### 13.5.2 Drift and Calibration

**Problem:** OES signals drift over time due to:
- Chamber wall buildup
- Liner erosion (changes optical properties)
- Light source aging (lamp drift)

**Solution:** **Periodic recalibration** (typically weekly or after liner change)

- Etch test wafer with known materials
- Record OES signature
- Update threshold/algorithm parameters

## 13.6 Emerging Techniques

### 13.6.1 In-Situ Reflectance Spectroscopy

**Principle:** Bounce light off wafer surface; analyze reflected spectrum

**Advantage:** Directly measures wafer thickness (via interference patterns) → more accurate endpoint

**Disadvantage:** Requires optical window in chamber (adds complexity)

### 13.6.2 Acoustic Emission

**Emerging research:** Monitor ultrasonic vibrations from etch process

**Potential:** Detect mechanical changes (surface morphology, residue buildup)

**Status:** Not yet production-ready

---

**Key Points:**
1. OES is primary endpoint detection method; spectral signatures guide layer transitions
2. Multi-parameter approach (OES + pressure + ion current) most robust
3. Stage-based endpoint needed for 176+ layer stacks
4. Periodic recalibration essential for sustained accuracy

*Next: Chapter 14*
