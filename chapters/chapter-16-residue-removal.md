# Chapter 16: Residue Removal Techniques (In-Situ Plasma Ash, Remote Ash)

## 16.1 Post-Etch Ash Process Overview

**Purpose:** Remove SiOxCly residue left at trench bottom after main etch

**Residue level before ash:** 10-50 nm thickness typical (can be severe, >100 nm, in extreme AR)

**Residue level after ash:** 2-10 nm (residual; cannot be completely removed)

## 16.2 In-Situ Plasma Ash (Chamber-Based)

### 16.2.1 In-Situ Ash Chemistry

**Gas change:** From Cl₂/BCl₃ to O₂/Ar mixture

**Reaction mechanism:**
$$\text{SiOxCly + O₂ radicals} \rightarrow \text{SiO₂ + CO/CO₂ + other volatiles}$$

Oxygen radicals oxidize organic components; carbon leaves as gas; final product is glassy SiO₂.

### 16.2.2 Ash Parameters

**Power:** 2-3 kW (lower than etch power; avoid device damage)

**Gas mix:** O₂ 80-90%, Ar 10-20%

**Pressure:** 40-80 Pa (similar to etch)

**Time:** 5-10 minutes per wafer

**Temperature:** Maintain 70-85°C (same limits as etch)

**Effectiveness:** Removes 70-90% of residue

### 16.2.3 Advantages and Disadvantages

**Advantages:**
- Single-chamber process (no equipment duplication)
- Fast transitions (same chamber, just gas/power change)
- Cost-effective

**Disadvantages:**
- Limited effectiveness (cannot remove all residue)
- Temperature limits prevent more aggressive ash
- Wafer already near thermal limits from etch; ash adds heat

## 16.3 Remote Plasma Ash (Separate Chamber)

### 16.3.1 RPA System Architecture

**Two-chamber cluster:**

1. **Etch chamber:** Standard Cl₂ or F-based etch
2. **Ash chamber:** Separate chamber with O₂/Ar plasma

**Transfer:** Wafer moves from etch chamber to ash chamber via transfer arm

**Advantage:** Decoupled temperature; ash chamber can operate hotter (100-150°C)

### 16.3.2 Remote Ash Mechanism

**Neutral radical approach:**
- O₂/Ar plasma generated in remote chamber (away from wafer)
- Plasma confined to remote region via magnetic field
- Neutral radicals extracted through port → delivered to wafer
- Ions not present (or present in very low density)

**Benefits:**
- No ion damage to resist or device layers
- Cleaner ash process
- More effective residue removal (higher temperature possible; ion-free environment)

### 16.3.3 RPA Effectiveness and Costs

**Residue removal:** 90-95% (compared to 70-90% for in-situ)

**Capital cost:** Additional $500K-1M for separate chamber

**Operational cost:** Increased cycle time (~10-20 sec transfer); ~20% longer total cycle

**Adoption:** Growing; ~30-40% of new 176+ layer production systems

## 16.4 Post-Ash Cleaning Options

### 16.4.1 HF Dip Treatment

**After plasma ash, optional HF dip:**

- HF strength: 2-10% (dilute)
- Duration: 5-30 seconds
- Temperature: 20-40°C

**Purpose:** Dissolve residual SiO₂ (result of oxidized residue)

**Mechanism:**
$$\text{SiO₂ + 4HF} \rightarrow \text{SiF₄ + 2H₂O}$$

**Advantages:** Effective at removing oxidized residue
**Disadvantages:** Wet chemistry; adds process steps and complexity

## 16.5 Advanced Ash Techniques

### 16.5.1 Pulsed Plasma Ash

**Concept:** Ash power applied in pulses (rather than continuous)

**Benefit:** Off-time allows cooling; lower average temperature; reduced device stress

**Adoption:** Emerging; not yet standard

### 16.5.2 Alternative Ash Gases

**N₂ plasma ash:** Nitrogen radicals for selective oxidation (research stage)

**H₂ plasma ash:** Reducing atmosphere; removes oxide and chlorides (experimental)

**Status:** Not production-ready; potential future directions

## 16.6 Residue Measurement

### 16.6.1 Cross-Section Measurement

**SEM cross-section:** Direct observation of residue layer thickness

**X-ray Photoelectron Spectroscopy (XPS):** Measures chemical composition

**Challenge:** Time-consuming; only sampled analysis

### 16.6.2 Electrical Characterization

**Leakage current measurement:** Test structures with parasitic capacitance

- Ash off: High leakage (residue provides conduction path)
- Ash on: Lower leakage (residue removed)

**Correlation:** Leakage reduction indicates ash effectiveness

## 16.7 Residue at Extreme Aspect Ratios (>250:1)

**Challenge:** At 250:1+ AR, residue trapping is severe

**Current solutions:**
- Oscillating etch-ash cycles (etch 2-3 min, ash 1 min, repeat) improves effectiveness
- Longer ash times (10-15 min) necessary

**Emerging challenge:** 300:1+ AR may require fundamentally different approaches

---

**Key Points:**
1. Post-etch ash mandatory for high-AR holes (mandatory by 176-layer level)
2. In-situ ash removes 70-90%; remote ash removes 90-95%
3. Temperature limits prevent more aggressive ash conditions
4. Residue cannot be completely eliminated; 2-10 nm typically remains
5. Extreme AR (>250:1) requires oscillating etch-ash cycles

*Next: Chapter 17 (Final Chapter)*
