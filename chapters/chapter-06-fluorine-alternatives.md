# Chapter 6: Fluorine-Based Alternatives and Advanced Chemistries

## 6.1 Introduction to Fluorine Etch Chemistries

While chlorine dominates 3D NAND etch historically, fluorine-based chemistries offer important advantages for certain layers and process phases:

**Advantages of fluorine:**
1. **SiO₂ etch rate:** F-based chemistry etches SiO₂ 3-5× faster than Cl-based chemistry
2. **Natural selectivity:** F/SiO₂ selectivity is naturally high due to Si-F bond formation
3. **Lower residue:** Fluorosilane byproducts (SiF₄) are highly volatile; less residue in deep trenches

**Disadvantages:**
1. **Material compatibility:** Fluorine is highly corrosive; requires special chamber materials (stainless steel, ceramic liners)
2. **Equipment complexity:** Fluorine chemistry requires more sophisticated gas cabinets and safety systems
3. **Cost:** Fluorine-containing precursors (C₄F₆, C₅F₈) are expensive
4. **Process knowledge:** Less mature than chlorine for 3D NAND integration

## 6.2 Molecular Fluorine (F₂)

### 6.2.1 F₂ Chemistry Basics

**Fluorine radical production:**
$$e^- + F_2 \rightarrow F \cdot + F \cdot + e^-$$
Threshold: 1.67 eV (very low; efficient production)

**Fluorine radical (F·) reactions:**

F· is highly reactive to silicon:
$$Si + F \cdot \rightarrow Si-F$$

Cascade reaction:
$$Si-F + F \cdot \rightarrow Si-F_2$$
$$Si-F_2 + F \cdot \rightarrow Si-F_3$$
$$Si-F_3 + F \cdot \rightarrow Si-F_4$$

**Final product:** SiF₄ (silicon tetrafluoride), highly volatile.

### 6.2.2 Silicon Etch Rate in F₂

**Typical etch rates:** 1-3 μm/min (3-5× higher than Cl₂)

**Why so much faster:**
1. F-Si bond formation is more favorable thermodynamically than Cl-Si
2. Si-F₄ formation is highly exothermic; reaction drives forward
3. Byproducts are volatile at low temperature; no residue accumulation

### 6.2.3 SiO₂ Etch Rate in F₂

**Mechanism:** F· attacks Si-O-Si bonds differently than Cl·.

$$SiO_2 + F \cdot \rightarrow \text{SiOF} + \text{other products}$$

Unlike Cl-based chemistry, F-based etch of SiO₂ doesn't require high ion energy; neutral F· alone is sufficient.

**Typical etch rates:** 0.5-1.5 μm/min (comparable to Si rate; selectivity is poor)

**Selectivity Si/SiO₂:** ~1-2:1 (unfavorable for Si-protective phase)

### 6.2.4 Practical Issues with F₂

**Safety:** F₂ is extremely toxic; concentrations >1% in air can be lethal within minutes. Requires specialized safety infrastructure.

**Material compatibility:** F₂ corrodes most metals; chamber must be stainless steel or ceramic-lined. Electrodes must be specially treated.

**Usage in 3D NAND:** Not commonly used alone in production due to safety/complexity. Sometimes used in specialized applications.

## 6.3 Hydrofluorocarbon Chemistry (HFC): C₄F₆, C₅F₈

### 6.3.1 C₄F₆ (Perfluorbutane)

**Molecular structure:** Linear C-C-C-C chain with 6 F atoms

**Advantages over F₂:**
1. Safer: Less aggressive than pure F₂; lower reactivity
2. Easier handling: Can be diluted in inert gas; bottles at moderate pressure
3. Better selectivity tuning: Carbon component provides additional chemistry control

**Dissociation in plasma:**
$$e^- + C_4F_6 \rightarrow F \cdot + CFx \cdot + C_x F_y^+ + e^-$$

Produces F· radicals plus carbon-containing fragments (CF, CF₂, CF₃).

### 6.3.2 C₅F₈ (Perfluorocyclopentane)

**Molecular structure:** Cyclic C-C-C-C-C ring with 8 F atoms

**Advantages:**
1. Higher F content (more fluorine per molecule)
2. Carbon fragments may polymerize → sidewall passivation films
3. Selectivity tuning via carbon deposition

**Etch characteristics similar to C₄F₆** but with more pronounced sidewall effects.

### 6.3.3 Selective SiO₂ Etch: C₄F₆ + Ar

**Common 3D NAND process:** C₄F₆ + 40-50% Ar at 30-50 Pa pressure

**Etch mechanism:**

F· radicals attack SiO₂:
$$SiO_2 + F \cdot \rightarrow SiOF, \text{SiF}_2, \text{byproducts}$$

C fragments deposit protective layer on Si surfaces (if exposed):
$$\text{Si surface} + CF_x \rightarrow \text{polymer-like CFx layer}$$

**Result:**
- SiO₂ etch rate: 1.5-2.5 μm/min
- Si etch rate: 0.1-0.3 μm/min (protected by C-polymer)
- Selectivity SiO₂/Si: 5-25:1

**Advantage:** Excellent for selective SiO₂ etch (e.g., etching sacrificial oxide layers while protecting polysilicon word lines)

### 6.3.4 Si₃N₄ Etch in F-Based Chemistry

**Mechanism:** F· attacks Si-N bonds

$$Si_3N_4 + F \cdot \rightarrow \text{SiF}_x, NFx, \text{byproducts}$$

**Etch rate:** 0.5-1.5 μm/min (similar to SiO₂)

**Selectivity concern:** F-based chemistry doesn't distinguish well between SiO₂ and Si₃N₄. Both etch at similar rates.

**Solution:** Use **dynamic selectivity switching** or chemistry modulation to etch different layers in phases.

## 6.4 Mixed Cl/F Chemistries

### 6.4.1 Why Mix?

Pure Cl and pure F chemistries each have pros and cons:

- **Cl alone:** Good for Si/SiO₂ selectivity control; poor SiO₂ etch rate; residue issues
- **F alone:** Excellent SiO₂ etch rate; poor Si/SiO₂ selectivity; corrosive

**Mixed Cl/F:** Combines benefits; allows tuning selectivity continuously.

### 6.4.2 Cl₂ + C₄F₆ Mixture

**Composition:** 40-60% Cl₂, 40-60% C₄F₆, small amount Ar

**Etch characteristics:**

| Material | Rate (μm/min) | Notes |
|----------|---------------|-------|
| Si | 0.8-1.5 | Moderate; Cl· and F· both attack Si |
| SiO₂ | 1.0-1.8 | F· dominates; some Cl· contribution |
| Si₃N₄ | 0.2-0.8 | Selectivity depends on power/pressure |

**Selectivity:** Tunable; intermediate between pure Cl and pure F

**Advantage:** Offers flexibility; single chemistry can span multiple etch phases with parameter adjustment

## 6.5 Advanced Chemistries and Emerging Approaches

### 6.5.1 Plasma-Induced Etch (PIE) with Chemically Inert Ions

**Approach:** Use inert ions (Ar⁺) for sputtering; chemical etch from radicals (Cl or F)

**Advantage:** Decouples ion-energy (for physical removal) from chemistry (for selectivity)

**Usage:** Some advanced chambers employ Ar⁺ for ion damage without introducing additional chemistry

### 6.5.2 Neutral Beam Etch

**Concept:** Generate directed beams of neutral radicals (not ions) to avoid damage and improve sidewall quality

**Production status:** Research; not yet production-scale for 3D NAND

### 6.5.3 Two-Gas High-Density Plasma (HDP)

**Approach:** Use ICP source (inductively coupled) to create very high ion density, then use chemical selectivity tuning

**Status:** Established in some production chambers; requires larger capital investment

## 6.6 Selectivity Engineering: Practical Staging

Most 3D NAND processes use **multi-stage etch sequences:**

| Stage | Chemistry | Material | Selectivity Target |
|-------|-----------|----------|-------------------|
| 1 | C₄F₆ + Ar | SiO₂ | High SiO₂/Si (protect word lines) |
| 2 | Cl₂ + BCl₃ | Polysilicon | High Si/oxide |
| 3 | C₄F₆ or Cl₂+F mix | SiO₂ | High SiO₂/Si₃N₄ (protect liners) |
| 4 | Conservative Cl₂ | Final etch to etch stop | High selectivity to tungsten |
| 5 | O₂/Ar plasma | Ash/residue | Remove deposits |

**Each stage:** 30 s to 2 min; optimized for specific material and selectivity requirement

**Total time:** 35-50 minutes for complete 176-layer etch + ash

## 6.7 Cost-Benefit Analysis

### 6.7.1 Equipment Cost

**Chlorine-only system:**
- Capital cost: ~$2-3M
- Lower material costs; standard materials

**Chlorine + Fluorine system:**
- Capital cost: ~$3.5-5M (additional gas handling, chamber materials)
- Higher maintenance; specialty materials consume faster

### 6.7.2 Operating Cost

**Gas cost per wafer:**
- Cl₂-based: ~$10-15
- C₄F₆-based: ~$50-100 (C₄F₆ is 10-20× more expensive than Cl₂)

**Chemistry strategy:** Use F-based chemistry only for phases where it's essential; minimize F chemistry usage.

## 6.8 Summary: Fluorine Chemistry in 3D NAND

**Status (2026):**
- **Chlorine-only:** Declining; being phased out
- **Chlorine + Selective Fluorine phases:** Mainstream; 60-70% of new systems
- **Mixed Cl/F throughout:** Emerging; ~20% of advanced systems
- **Pure Fluorine:** Niche applications; <5% of systems

**Trend:** Increasing fluorine usage as higher layer counts require tighter selectivity windows and lower residue

---

**Key Takeaways:**

1. **Fluorine radicals** etch SiO₂ 3-5× faster than Cl; excellent for oxide-specific phases
2. **C₄F₆ + Ar** provides SiO₂/Si selectivity >10:1 via F-etch + C-polymer passivation
3. **Mixed Cl/F** offers flexibility; selectivity tunable with power/pressure
4. **Multi-stage approach** uses Cl for Si-selective phases; F for oxide-selective phases
5. **Cost tradeoff:** F-chemistry is 5-10× more expensive; use judiciously

---

*Next Chapter: [Chapter 7 - Mixed Cl/F Chemistries and Selectivity Switching](chapter-07-mixed-chemistries.md)*
