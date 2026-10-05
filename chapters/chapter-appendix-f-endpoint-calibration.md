# Appendix F: Endpoint Detection Calibration Procedures

## F.1 OES Calibration Process

### Step 1: Reference Measurement

1. Etch test wafer with known materials (oxide → polysilicon → etch stop sequence)
2. Record depth at each layer via cross-section SEM
3. Cross-reference with OES spectra recorded during etch

### Step 2: Spectrum Analysis

**OES intensity (a.u.) vs. etch depth:**

| Depth (μm) | Cl (837.6 nm) | SiO (specific line) | Signal Quality |
|-----------|--------|--------|--------|
| 5 (in SiO₂) | 450 | 200 | Good |
| 10 | 480 | 180 | Good |
| 20 (transitioning to Si) | 550 | 50 | Transition |
| 25 (in polysilicon) | 620 | <10 | Good (Si-only) |
| 40 (near etch stop) | 580 | <5 | Approaching end |

### Step 3: Endpoint Threshold Setting

**Algorithm:**
1. Calculate dI/dt (slope of Cl emission over 10-second window)
2. When dI/dt crosses threshold (e.g., slope increase >50 a.u./sec), signal endpoint
3. Empirically set threshold based on test wafer data

## F.2 Calibration Frequency

| Condition | Recalibration Interval |
|-----------|----------|
| Normal operation | Weekly |
| After liner change | Immediately |
| After electrode replacement | Within 10 wafers |
| Pressure/temperature drift noted | Immediately |

## F.3 Endpoint Verification

**Post-etch SEM cross-section verification:**
- Measure actual etch depth vs. predicted (based on OES endpoint)
- If actual ≠ predicted by >±5%, adjust threshold

**Target accuracy:** OES endpoint within ±2 min of actual etch stop time

---

*See Chapter 13 for endpoint detection principles.*
