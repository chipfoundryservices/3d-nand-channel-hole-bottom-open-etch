# Chapter 2: NAND String Geometry and Feature Scaling

## 2.1 String Configurations

### 2.1.1 Single-Level vs. Multi-Level Cells

The basic 3D NAND cell stores charge in a floating gate (or charge trap). The amount of charge determines the cell's threshold voltage (V_th). By storing different amounts of charge, a single physical cell can represent multiple bits:

- **SLC (Single-Level Cell):** 1 bit per cell (2 states: 0 or 1)
- **MLC (Multi-Level Cell):** 2 bits per cell (4 states)
- **TLC (Triple-Level Cell):** 3 bits per cell (8 states)
- **QLC (Quad-Level Cell):** 4 bits per cell (16 states)
- **PLC (Penta-Level Cell):** 5 bits per cell (32 states) — early research stage

Higher bits-per-cell increase storage density but reduce voltage margins and data retention. For 3D NAND, TLC and QLC are the industry standard as of 2026.

### 2.1.2 String Topology

In a **NAND string**, transistors are connected in series. All control gates are biased to the same word line voltage for a particular row. The string structure determines read and write current paths:

```
                [Bit Line - Metal]
                        |
            [Bit Line Select Transistor (SGD)]
                        |
            [Cell 63 - String 0 (Row 63)]
                        |
            [Cell 62 - String 0 (Row 62)]
                        |
                    ...
                        |
            [Cell 0 - String 0 (Row 0)]
                        |
            [Source Line Select Transistor (SGS)]
                        |
            [Common Source Line - Metal]
```

**Key Parameters:**

- **String width:** 1 to 4 transistors wide in parallel (rare; most 3D NAND uses single-width strings for simplicity)
- **Series resistance:** Dominated by the highest-resistance cell in the string (typically 1-10 MΩ per cell in production devices)
- **Current per string:** Typically 1-100 μA per cell during read (TLC) to 0.1-10 nA in retention mode
- **Voltage swings:** 0-12 V on word lines, 0-3 V on bit lines, for read/write/erase operations

### 2.1.3 Charge Trap vs. Floating Gate Architectures

**Floating Gate (FG) Design:**

- **Structure:** Isolated polysilicon island surrounded by tunnel oxide and control oxide
- **Charge storage:** Discrete charge on the polysilicon; charge distribution is relatively uniform
- **Advantages:** Simpler fabrication; mature technology; cell design is compact
- **Disadvantages:** Charge leakage through tunnel oxide; cell-to-cell charge coupling in dense arrays
- **Used by:** Intel (historical), some manufacturers in early 3D NAND

**Charge Trap (CT) Design:**

- **Structure:** Nitride layer (typically Si₃N₄) sandwiched between two oxide layers; charge is stored **in trap sites within the nitride**
- **Charge storage:** Distributed across many trap sites; charge is more localized to the trap position
- **Advantages:** Better retention (charge cannot leak out; it's trapped); reduced cell coupling; better for multi-level operation
- **Disadvantages:** More complex process flow; requires precise nitride layer thickness
- **Used by:** Samsung, SK Hynix, Micron, Intel (current), KIOXIA

**Etch Implications:**

The choice between FG and CT significantly affects channel hole etch requirements:

- **FG stacks:** Simpler materials (primarily polysilicon and SiO₂), easier selectivity control
- **CT stacks:** Multiple dielectric layers (SiO₂, Si₃N₄, SiO₂, sometimes high-k), requires more sophisticated selectivity

By 2026, **charge trap architectures dominate** 3D NAND production (>90% market share).

## 2.2 Layer Stacking Sequences

### 2.2.1 The Classical Alternating Layer Model

The simplest 3D NAND stack uses an alternating sequence:

```
Layer 175:  [SiO₂ sacrificial]
Layer 174:  [Polysilicon word line 87]
Layer 173:  [SiO₂ sacrificial]
Layer 172:  [Polysilicon word line 86]
            ...
Layer 3:    [SiO₂ sacrificial]
Layer 2:    [Polysilicon word line 0]
Layer 1:    [SiO₂ sacrificial / etch stop]
Layer 0:    [Bottom contact and source line]
```

**Spacing Evolution:**

- **First generation (2013):** ~50 nm pitch (word line + sacrificial)
- **Second generation (2016):** ~35-40 nm pitch
- **Third generation (2020):** ~20-25 nm pitch
- **Current production (2026):** ~15-20 nm pitch
- **Roadmap (2027+):** <15 nm pitch

Reducing pitch increases layer count for the same stack height, improving bit density but making the channel hole etch more challenging due to tighter aspect ratios.

### 2.2.2 Modern Charge Trap Stack Architecture

Modern charge trap stacks are significantly more complex than the classical model. A typical layer sequence for a single "memory unit" in a CT stack:

```
[Polysilicon word line (WL)] ─ 30 nm
    [Control oxide (CO)]      ─  5-8 nm   [SiO₂]
    [Charge trap layer (CT)]  ─ 5-10 nm   [Si₃N₄]
    [Tunnel oxide (TO)]       ─  5-8 nm   [SiO₂]
[Sacrificial oxide]           ─ 20-25 nm
```

**For each word line to the next:**

Full material stack = ~70-90 nm, of which:
- Polysilicon word line: 25-35 nm
- Dielectrics (CO, CT, TO): 15-25 nm
- Sacrificial SiO₂: 20-25 nm

### 2.2.3 Nitride Liner and Blocking Oxide

In addition to the charge trap layer, modern stacks include:

**Blocking Oxide (top):**
- Material: SiO₂ or high-k dielectric (e.g., Al₂O₃, HfO₂)
- Thickness: 5-10 nm
- Purpose: Prevent charge leakage into the gate during erase; improve retention
- **Etch impact:** May require different chemistry or selectivity than the charge trap layer

**Nitride Liner (sidewall):**
- Material: Si₃N₄
- Thickness: 5-15 nm
- Purpose: Passivate silicon interfaces; prevent parasitic conduction along the channel wall
- **Etch impact:** Critical to preserve during channel hole etch; over-etch → leakage current; under-etch → etch residue

### 2.2.4 Etch Stop Layers

At various depths in the stack, materials are designed to stop etch processes:

**Tungsten Etch Stop (Bottom):**
- Located ~100-500 nm above the source line
- Prevents over-etch into the source line metal
- Tungsten is significantly less etch-reactive than polysilicon in most Cl-based chemistries
- Selectivity requirement: Polysilicon/Tungsten > 100:1 (poly etches, tungsten does not)

**Oxide Etch Stop (Mid-Stack):**
- Sometimes SiO₂ with a different density or composition is used to stop etch at intermediate points
- Selectivity: Polysilicon/SiO₂ or Si₃N₄/SiO₂

**High-Density Oxide or Nitride:**
- Some manufacturers use specially deposited high-density oxide (HDO) or CVD nitride as intermediate etch stops
- Selectivity varies by chemistry

## 2.3 Feature Scaling and Layer Count Evolution

### 2.3.1 First Generation (2013-2015): 48-64 Layers

**Specifications:**
- Layers: 48-64 (typically 48 word lines + periphery)
- Stack height: 1.5-2.5 μm
- Pitch: 45-50 nm (WL + sacrificial)
- Hole diameter: 400-500 nm
- Aspect ratio: ~40-50:1

**Challenges at this generation:**
- First-generation plasma tools were adapted from deep trench capacitor etch
- Etch uniformity was marginal; yield issues common
- Thermal management was basic

**Status:** No longer in high-volume production.

### 2.3.2 Second Generation (2016-2018): 96 Layers

**Specifications:**
- Layers: 96 (or sometimes 88-100)
- Stack height: 3.5-5.0 μm
- Pitch: 35-42 nm
- Hole diameter: 350-450 nm
- Aspect ratio: 70-100:1

**Key improvements:**
- Better thermal management in chambers
- Improved gas distribution
- More sophisticated power modulation

**Challenges:**
- Aspect ratios pushing 100:1 created severe neutral depletion in deep trenches
- ARDE (aspect ratio dependent etching) became critical—holes at the edge of patterns etched differently than holes in the center
- Residue management critical; ashing step became mandatory

**Status:** Still in production by some manufacturers; being phased out in favor of higher layer counts.

### 2.3.3 Third Generation (2019-2022): 128-176 Layers

**Specifications:**
- Layers: 128-176 (typically 128, 136, or 176 word lines + periphery)
- Stack height: 7.0-10.5 μm
- Pitch: 20-28 nm
- Hole diameter: 300-380 nm
- Aspect ratio: 150-300:1+

**Design changes:**
- Reduced pitch required very thin word lines (~20-25 nm polysilicon)
- More dielectric layers → more selectivity challenges
- Tighter thermal control needed
- More aggressive ashing and residue removal

**Current status:** Mainstream production (2024-2026). Samsung, SK Hynix, KIOXIA, Micron all in high-volume.

### 2.3.4 Fourth Generation (2023-2026+): 200+ Layers

**Roadmap Specifications:**
- Layers: 200-240+ planned
- Stack height: 12-15 μm
- Pitch: 15-20 nm
- Hole diameter: 250-300 nm
- Aspect ratio: 300-500+:1

**Challenges being addressed:**
- Ultra-high aspect ratios approaching physical limits of plasma transport
- Thermal control becomes increasingly difficult
- Etch uniformity across the wafer becomes critical bottleneck
- New chamber designs with advanced electrode configurations

**Development status:** Early production (SKU releases in 2025-2026); most 200-layer production is still in development or early ramp.

## 2.4 Thermal Stability and Etch Implications

### 2.4.1 Gate Oxide Integrity (GOI)

The tunnel oxide and blocking oxide in floating-gate and charge-trap devices are extremely thin (5-10 nm). High temperatures during the channel hole etch can:

1. **Increase trap generation rates** in the oxide
2. **Accelerate charge leakage** through the oxide
3. **Cause charge redistribution** within the charge trap layer (especially problematic for CT devices)

**Temperature Limits by Generation:**

| Generation | Limit | Reason |
|-----------|-------|--------|
| 48-layer (2013) | 120-130°C | Gate oxide degradation; device instability above this |
| 96-layer (2016) | 100-110°C | Tighter thermal margins; thinner oxides |
| 176-layer (2020) | 80-90°C | Aggressive CT scaling; high trap generation rates |
| 200+ layer (2025+) | <80°C | Extreme CT scaling; research into thermal limits ongoing |

**Etch implication:** Chamber power and pressure must be carefully controlled to avoid wafer temperatures exceeding device limits. Active cooling with liquid nitrogen or chilled coolant is mandatory.

### 2.4.2 Floating Gate Charge Retention

During the etch process, floating gates (or charge trap sites) may contain pre-programmed charge from prior test patterns or device trimming steps. Elevated temperatures can cause:

1. **Charge loss** due to tunneling through the tunnel oxide
2. **Charge gain** due to tunnel current in the opposite direction
3. **Charge redistribution** within the floating gate or trap layer

For charge trap devices with distributed trap sites, temperature-induced redistribution can cause significant V_th shifts, which can lead to:
- Read disturb during the etch
- Post-etch bit errors if not compensated
- Device failures in extreme cases

**Mitigation:** Some manufacturers erase devices before channel hole etch to minimize thermal stress effects.

### 2.4.3 Polysilicon and Nitride Layer Stress

Polysilicon and nitride layers also experience stress from:

1. **Temperature cycling:** Expansion/contraction differences between materials
2. **Plasma ion bombardment:** Creates defects and stresses in crystalline structure
3. **Chemical reactions:** Chlorine and fluorine species can create oxide or nitride layers that alter stress state

**Impact on etch:**
- Residual stress can affect etch rates
- Stress-induced leakage current in highly stressed layers
- Yield loss if stress is relieved through cracking or peeling during ashing

## 2.5 Selectivity Requirements Across Material Boundaries

### 2.5.1 Selectivity Matrix

3D NAND etch must handle multiple materials sequentially with controlled selectivity. The key selectivity ratios needed:

| Interface | Selectivity Ratio | Why Important |
|-----------|------------------|---------------|
| Polysilicon / SiO₂ | >10:1 | Etch through SiO₂ without over-etching polysilicon word lines |
| SiO₂ / Si₃N₄ | >5-10:1 (or <1:1) | Etch through oxide layers without damaging nitride liners |
| Polysilicon / Tungsten | >100:1 | Etch down to tungsten etch stop without consuming tungsten |
| Si₃N₄ / SiO₂ | >5:1 (or reverse) | Depends on which layer is target |

### 2.5.2 Dynamic Selectivity Switching

Because a single chemistry cannot achieve all selectivity requirements simultaneously, modern 3D NAND etch uses **dynamic selectivity switching**:

1. **Phase 1:** Etch through sacrificial SiO₂ with high selectivity over polysilicon
   - Chemistry: Cl₂-based with low ion energy to suppress polysilicon etch
   - Selectivity: SiO₂/Polysilicon = 20:1 to 50:1

2. **Phase 2:** Etch polysilicon word lines
   - Chemistry: Same or different Cl-based chemistry with adjusted power
   - Selectivity: Polysilicon/SiO₂ = 10:1 to 20:1

3. **Phase 3:** Etch through Si₃N₄ liners and remaining oxide
   - Chemistry: May switch to F-based or mixed Cl/F chemistry
   - Selectivity: Si₃N₄/SiO₂ or vice versa, typically 5-10:1

4. **Phase 4 (Optional):** Final approach to tungsten etch stop
   - Chemistry: Conservative Cl₂ with low power
   - Selectivity: Polysilicon/Tungsten > 100:1

Each transition must be carefully timed to avoid over-etch or under-etch at material boundaries.

### 2.5.3 Aspect Ratio-Dependent Selectivity Loss

**Critical finding:** Selectivity ratios achieved in large, open areas (where neutral species and ions transport freely) are often **not achievable in deep, high-aspect-ratio trenches**.

Reasons:

1. **Neutral depletion** changes the Cl·/ion balance in the hole
2. **Ion scattering** alters the ion energy distribution reaching the sidewall vs. bottom
3. **Temperature gradients** in deep trenches cause different etch chemistry at bottom vs. sidewall
4. **Radical depletion** near the bottom limits etch rate on sidewalls, affecting relative selectivity

**Implication:** Selectivity matrices from test vehicles (which use low-aspect-ratio features) often over-predict performance in high-aspect-ratio production holes. This is a major source of unexpected yield loss when scaling to higher layer counts.

## 2.6 Contact and Via Integration

### 2.6.1 Source Line Contact

At the bottom of the channel hole stack, a tungsten contact plug connects the channel to the common source line metal:

**Typical structure:**
```
[Channel fill - Polysilicon]
[Contact plug - Tungsten] ─ 100-300 nm diameter
[Tungsten barrier/liner] ─ 10-20 nm (TiN or WN)
[Contact opening - SiO₂ or Cu]
[Source line - Al or Cu metal]
```

**Etch impact:**
- Tungsten etch stop must be precise: depth control ±20-50 nm
- Tungsten surface must be clean (no oxide or residue) for subsequent contact fill
- Etch must not damage or etch the tungsten plug, else resistance increases

### 2.6.2 Bit Line Connection (Top)

At the top of the stack, the bit line metallization connects to the channel through a contact:

**Typical structure:**
```
[Bit line - Al or Cu]
[Contact barrier - TiN]
[Contact vias - Cu]
[Top of channel fill]
```

**Etch impact:**
- Less critical to the channel hole etch (occurs earlier in the process)
- But interconnect etch must be coordinated with channel etch for process module compatibility

## 2.7 Summary: Implications for Channel Hole Etch

From this chapter's discussion of geometry and scaling:

1. **Layer count drives aspect ratio:** 48 layers → 50:1; 176 layers → 200:1; 200+ layers → 300:1+
2. **Pitch scaling creates tighter tolerances:** Thinner word lines, tighter etch stop windows
3. **Material complexity increases:** CT stacks with dielectrics are more challenging than simple FG/oxide stacks
4. **Thermal management is critical:** Higher aspect ratios require lower power → longer cycles → thermal stability is essential
5. **Selectivity control is dynamic:** Single chemistry cannot achieve all requirements; staged etching with chemistry changes is necessary
6. **ARDE becomes dominant effect:** Uniform etch of high-aspect-ratio features is more challenging than achieving bulk etch rates

These constraints directly drive the chamber design, plasma chemistry, and process control topics covered in subsequent chapters.

---

**Key Takeaways:**

1. Modern 3D NAND uses **charge trap architectures** with complex multi-layer dielectric stacks
2. **Aspect ratios have increased 6-8× in one decade:** from 40:1 (2013) to 200-300:1 (2026)
3. **Temperature control is critical:** Device thermal limits have tightened from >120°C to <80°C
4. **Selectivity switching between material phases** is mandatory; no single chemistry achieves all requirements
5. Future scaling to 200+ layers will require **further advances in chamber design and plasma chemistry**

---

*Next Chapter: [Chapter 3 - Etch Challenges: High Aspect Ratios, Selectivity, and Thermal Limits](chapter-03-etch-challenges.md)*
