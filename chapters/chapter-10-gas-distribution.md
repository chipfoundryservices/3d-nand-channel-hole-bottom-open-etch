# Chapter 10: Gas Distribution and Pressure Uniformity at Extreme Aspect Ratios

## 10.1 Gas Flow Physics in Plasma Chambers

### 10.1.1 Flow Regimes

Gas flow in the chamber depends on the Knudsen number:

$$Kn = \frac{\lambda}{D}$$

Where λ is mean free path and D is characteristic chamber dimension.

**Three regimes:**

| Regime | Kn | Condition | Flow Type |
|--------|-----|-----------|-----------|
| Continuum | <0.01 | P high | Hydrodynamic (classical fluid dynamics) |
| Transition | 0.01-10 | P moderate | Partially collisional |
| Molecular | >10 | P very low | Free molecular flow; particles follow ballistic paths |

**3D NAND operating point:** At 40-80 Pa, Kn ≈ 0.5-2 → **Transition regime**

Implication: Flow doesn't follow classical fluid equations; requires kinetic theory or molecular simulation.

### 10.1.2 Gas Distribution Inlet Design

**Goals:**
1. **Uniform pressure across chamber:** Target <5% variation radially
2. **Prevent central crowding:** Gas shouldn't concentrate at center
3. **Avoid edge starvation:** Peripheral regions need adequate gas flux

**Inlet types:**

**Radial inlet (most common):**
- Gas enters perpendicular to wafer, at multiple points around chamber circumference
- Provides natural radial spreading
- Challenge: Perfectly symmetric design difficult; small asymmetries cause non-uniformity

**Showerhead inlet:**
- Gas flows down from top through many small holes (500-2000 holes, 1-2 mm dia)
- Creates nearly uniform flux downward
- Advantage: Very good uniformity (typically <3%)
- Disadvantage: Hole clogging risk if particles present

**Dual-stage inlet:**
- Primary inlet distributes gas to secondary distribution ring
- Secondary ring (multiple outlets) distributes further
- Best uniformity achievable (~2-3%)
- More complex; higher cost

### 10.1.3 Pressure Control

**Automatic Pressure Control (APC):**

1. **Capacitive pressure gauge:** Measures chamber pressure continuously
2. **Throttle valve:** Controls flow to pump (bypass or variable conductance)
3. **Feedback loop:** If P > setpoint, open valve more; if P < setpoint, close

**Typical control bandwidth:** 0.1-0.5 Hz (slow response; prevents oscillation)

**Setpoint tolerance:** ±2-5% achievable in production

**Pressure uniformity across 300mm wafer:**

Variation sources:
- **Gas inlet non-uniformity:** ±3-5% if inlet design not optimized
- **Radial temperature gradient:** Hotter center → lower density → pressure appears lower
- **Pump line asymmetry:** Pump location and lines can create pressure gradient

Target: **<5% pressure variation** (typically 3-4% achieved with good design)

## 10.2 Gas Flow Patterns and Trench Penetration

### 10.2.1 Neutral Species Transport into Trenches

**Key challenge:** Getting neutral radicals deep into high-AR holes.

**Mechanisms:**

1. **Diffusion:** Random walk of gas molecules into hole
2. **Convection:** Directed flow into hole (weak in high-AR geometry)
3. **Ballistic entry:** Some molecules enter on straight paths

**Effective penetration depth:**

For a hole of radius r and depth d:

$$\text{Penetration} \propto \sqrt{\frac{r \cdot D_{\text{eff}}}{v_z}}$$

Where D_eff is effective diffusivity and v_z is vertical velocity.

**Result:** In 100:1 AR holes, neutral flux decreases exponentially with depth; significant depletion below ~1 μm.

### 10.2.2 Convective Gas Flow Enhancement

**Technique:** Apply slight radial or spiral gas flow to improve transport into trenches.

**Spiral inlet design:**
- Inlet creates tangential velocity component
- Gas spirals down into chamber → enters trenches with directed motion
- Can improve penetration by 20-30%

**Limitation:** Must not create pressure non-uniformity (conflicting goal)

### 10.2.3 Aspect Ratio Effects on Gas Transport

**Loading effect:** In dense patterns (high local AR), gas is depleted faster.

**Result:** Isolated holes (low local AR) etch faster than dense holes (high local AR) → pattern-dependent loading

**Compensation techniques:**
- Dynamic recipe adjustment: Increase power in later stages when AR becomes higher
- Pattern-dependent bias: Apply different RF power to different pattern density regions (not yet practical in production)

## 10.3 Pressure Effects on Etch Behavior

### 10.3.1 Ion Mean Free Path vs. Pressure

At typical process pressure 50 Pa:

$$\lambda_i \approx 50-100 \, \text{μm}$$

**Implication:** Ions undergo multiple collisions before reaching wafer; ion energy degrades.

$$E_{\text{final}} = E_0 e^{-\sigma_i \cdot n \cdot d}$$

Where σ_i is collision cross-section, n is neutral density, d is distance.

**Pressure dependence:**

- **Low pressure (<30 Pa):** Ions reach wafer with high energy; good ion collimation but poor neutral transport
- **Optimal (50-70 Pa):** Balance between ion collimation and neutral transport
- **High pressure (>100 Pa):** Ions are thermalized; ion energy low; poor selectivity

### 10.3.2 Etch Rate vs. Pressure

**Typical behavior (for Cl₂-based chemistry):**

| Pressure (Pa) | SiO₂ Rate (μm/min) | Si Rate (μm/min) | Notes |
|--------------|-------------------|-----------------|-------|
| 20 | 0.3 | 0.2 | Too low; poor transport |
| 40 | 0.8 | 0.5 | Improving transport |
| 60 | 1.5 | 1.0 | Near optimal |
| 80 | 1.4 | 0.95 | Slight decrease |
| 120 | 1.0 | 0.7 | Thermal collision regime |

**Peak etch rate at ~50-70 Pa** (material-dependent; slight optimization needed per chemistry)

### 10.3.3 Selectivity vs. Pressure

**Key finding:** Selectivity (ratio of etch rates) is **most sensitive to pressure** among all parameters.

Example (SiO₂/Si selectivity):

| Pressure (Pa) | Selectivity |
|--------------|-------------|
| 30 | 1.5:1 |
| 50 | 5:1 |
| 70 | 3:1 |
| 100 | 1:1 |

**Explanation:** At low pressure, ions are energetic → Si etches preferentially → low SiO₂/Si selectivity.
At high pressure, ions are thermalized → neutral-limited regime → SiO₂ and Si etch at similar rates.

**Practical implication:** Pressure setpoint is critical; ±5% variation causes ±20-30% selectivity drift

## 10.4 Gas Composition and Mixing

### 10.4.1 Multi-Component Gas Streams

**Typical 3D NAND recipe:**

Cl₂/BCl₃/Ar mixture (polysilicon-selective phase):
- Cl₂: 40-60% (primary etchant)
- BCl₃: 20-40% (etch carrier; provides selectivity control)
- Ar: 10-20% (cooling agent; neutral transport enhancement)

**Flow control:**

Each component controlled via Mass Flow Controller (MFC):
- Cl₂: 100-200 sccm
- BCl₃: 80-120 sccm
- Ar: 30-80 sccm
- Total: 250-400 sccm

**Ratio stability:**

MFC accuracy: ±2% typical
Result: Gas composition stable to ±5% over time

### 10.4.2 Gas Switching Strategy

**Between chemistry phases:**

1. **Ramp down "old" gas:** Cl₂/BCl₃ flow reduced to 0 over ~5 seconds
2. **Ramp up "new" gas:** C₄F₆/Ar flow increased to setpoint over ~5 seconds
3. **Stabilization:** Wait ~15-30 sec for chamber equilibrium
4. **Resume etch:** After pressure stabilizes to ±2% of setpoint

**Critical timing:** Smooth transitions prevent etch rate spikes; sharp transitions cause transient effects

## 10.5 Uniformity Measurement and Control

### 10.5.1 Pressure Uniformity Measurement

**Measurement technique:**
- Multiple capacitive pressure gauges distributed around chamber
- Typical: 4-8 gauges at different radial positions
- Record pressure at each location during steady-state etch

**Acceptance criteria:**
$$\frac{P_{\max} - P_{\min}}{P_{\text{avg}}} < 5\%$$

### 10.5.2 Etch Rate Uniformity Mapping

**Method:** Etch test wafer; measure depth at multiple locations (usually 25-49 points across 300mm wafer)

**Analysis:**
- Calculate depth mean and standard deviation
- Plot radial profile (center vs. edge)
- Identify systematic patterns (center high/low, edge effects, etc.)

**Targets:**
- **Radial uniformity:** ±3% (center vs. edge within 3%)
- **Azimuthal uniformity:** ±2% (no azimuthal variation)
- **Overall σ:** <3% of mean depth

### 10.5.3 Correction Methods

**Passive design (hardware):**
- Optimize inlet geometry (showerhead, dual-stage)
- Careful chamber thermal design (uniform cooling)
- Symmetric pump and gas routing

**Active correction (recipe tuning):**
- Radial power correction: Apply different power levels to center vs. edge regions (advanced systems only)
- Temporal correction: Adjust gas flow during etch based on real-time pressure feedback

## 10.6 Advanced Techniques: Coil Tuning (ICP)

### 10.6.1 Inductive Coupling Tuning

In ICP systems, RF coil proximity and configuration affect plasma density distribution:

**Tuning element:** Variable capacitor or shorted turn in coil

- **Increase coupling:** More RF energy couples to plasma → higher plasma density everywhere
- **Decrease coupling:** Less energy → lower density
- **Asymmetric coupling:** Position tuning element to preferentially couple to one side → asymmetric density

**Advantage:** Can correct for natural asymmetries in chamber geometry (e.g., pump location).

### 10.6.2 Coil Geometry Design

**Flat spiral coils (3-turn typical):**
- Outer diameter ≈ chamber diameter
- Spacing between turns: ~20-30 mm
- Distance from chamber wall: ~10-20 mm

**Effect of coil position:**
- Coil closer to center: More uniform density
- Coil closer to edge: Higher edge density (can compensate for natural edge depletion)

## 10.7 Summary: Achieving Uniformity in High-AR Etch

**Competing demands:**

1. **High pressure** → Better neutral transport into deep holes
2. **Low pressure** → Better ion collimation into deep holes
3. **Uniform pressure distribution** → <5% variation across 300mm
4. **Stable pressure over time** → ±2% setpoint tracking during 40-min etch

**Solution:** Combine:
- Optimized inlet geometry (showerhead or dual-stage)
- Careful thermal and electrode design (symmetric)
- Active pressure feedback with fast-responding APC valve
- Recipe tuning with predictive etch rate models

**State-of-art uniformity achieved:** 3-4% depth variation across 300mm wafer for 176-layer etch

---

**Key Takeaways:**

1. **Transition flow regime** (Kn ~0.5-2) requires kinetic theory; classical fluid dynamics insufficient
2. **Optimal pressure:** 50-70 Pa balances ion/neutral transport
3. **Gas distribution inlet design** critical; showerhead achieves <3% uniformity
4. **Pressure uniformity:** <5% variation needed; requires <5% pressure variation
5. **Selectivity highly sensitive to pressure:** ±5% pressure → ±20-30% selectivity drift

---

*Next Chapter: [Chapter 11 - Bias and RF Power Optimization for Vertical Sidewalls](chapter-11-bias-rf-optimization.md)*
