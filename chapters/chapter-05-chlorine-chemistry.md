# Chapter 5: Chlorine-Based Deep Trench Etch Chemistry

## 5.1 Overview: Why Chlorine?

Chlorine-based chemistries have been the industrial standard for semiconductor etch since the 1990s. For 3D NAND channel hole etching, chlorine provides several advantages:

1. **Versatility:** Cl₂ can etch silicon, silicon oxides, silicon nitride, and polysilicon with adjustable selectivity
2. **Volatility:** Cl₂ and most chlorine-bearing byproducts (SiCl₄, SiCl₂) are volatile at process temperatures
3. **Controllability:** Selectivity can be tuned by adjusting power, pressure, and gas mix
4. **Maturity:** Decades of development; extensive process knowledge base
5. **Cost:** Chlorine gas is inexpensive compared to fluorine alternatives

This chapter focuses on chlorine chemistry mechanisms for silicon, SiO₂, and Si₃N₄ etch in the context of ultra-high-aspect-ratio 3D NAND applications.

## 5.2 Chlorine Sources and Activation

### 5.2.1 Molecular Chlorine (Cl₂)

**Source:** Chlorine gas bottles (99.5% purity for semiconductor use)

**Activation mechanisms in plasma:**

1. **Electron impact ionization:**
   $$e^- + Cl_2 \rightarrow Cl_2^+ + 2e^-$$
   Threshold energy: 11.5 eV

2. **Electron impact dissociation:**
   $$e^- + Cl_2 \rightarrow Cl \cdot + Cl \cdot + e^-$$
   Threshold energy: 2.5 eV (much lower than ionization)

3. **Excited state formation:**
   $$e^- + Cl_2 \rightarrow Cl_2^* + e^-$$
   (Metastable excited state; can dissociate spontaneously or via collisions)

**Key point:** Electron impact dissociation is much more probable than ionization for Cl₂. At typical electron temperatures (2-5 eV), dissociation via Eq. 2 dominates, producing Cl· radicals.

### 5.2.2 Alternative Chlorine Sources

**HCl (Hydrogen Chloride):**
- Sometimes added (10-30% of feed) to control sidewall passivation
- Provides additional H atoms for etch chemistry
- More aggressive toward silicon than Cl₂ alone

**BCl₃ (Boron Trichloride):**
- Added as chlorine carrier (20-50% of feed)
- Boron can deposit protective coatings on sidewalls (BCxOy, BCxNy)
- Enhances selectivity between materials
- Used especially in SiO₂/Si₃N₄ selective etches

**CCl₄ (Carbon Tetrachloride):**
- Provides chlorine and carbon
- Carbon can form sidewall inhibitor layers (SiCl_x, SiOCl_x)
- Less common than BCl₃ in modern processes

## 5.3 Chlorine Radical Chemistry

### 5.3.1 Chlorine Radical (Cl·)

**Primary neutral species for material etch.**

**Formation routes:**
1. Electron impact on Cl₂ (dominant)
2. Dissociative recombination: $Cl_2^+ + e^- \rightarrow Cl + Cl$
3. Thermal dissociation at high wafer temperature

**Reaction with silicon:**

$$Si + Cl \cdot \rightarrow SiCl_x + \text{byproducts}$$

(Exact stoichiometry depends on surface temperature and Cl flux)

**Overall reaction (simplified):**
$$Si + 2Cl_2 \rightarrow SiCl_4 + \text{byproducts}$$

**Etch rate dependence on [Cl·]:**

Etch rate typically follows first-order kinetics in radical concentration:
$$E = k \times [Cl \cdot]$$

Where k is reaction rate constant (temperature dependent).

### 5.3.2 Chlorine Atomic Ion (Cl⁺)

**Secondary species; less reactive than Cl· but important for ion-assisted etch.**

**Formation:**
$$e^- + Cl_2 \rightarrow Cl_2^+ + 2e^-$$
$$Cl_2^+ + Cl_2 \rightarrow Cl_3^+ + Cl \cdot$$
$$Cl_3^+ + e^- \rightarrow Cl_2^+ Cl \cdot$$
(Complex ion chemistry; simplified above)

Net result: Cl⁺ and Cl₃⁺ present in discharge.

**Role in etch:**

Cl⁺ ions impact the surface with energy 50-200 eV, causing:
1. **Sputtering:** Eject surface atoms
2. **Surface activation:** Create reactive sites for Cl· to attack
3. **Ion-assisted chemical etch:** Enhanced etch rate compared to Cl· alone

## 5.4 Silicon Etch Chemistry

### 5.4.1 Pure Cl₂ Etch of Silicon

**Reaction mechanism:**

Silicon surface has Si-Si bonds (and surface oxides/chlorides). Chlorine radical attacks:

$$Si-Si + Cl \cdot \rightarrow Si-Cl + Si \cdot$$

Chain reaction propagates until Si-Cl coverage becomes significant:

$$\text{Si surface} + n \times Cl \cdot \rightarrow \text{Si-Cl}_n$$

Once fully chlorinated, Si-Cl bonds are relatively stable. Further etch requires:

1. **Ion bombardment:** Ions break Si-Cl bonds, creating sites for additional Cl· attack
2. **Higher temperature:** Thermal energy promotes desorption of SiCl₃ and formation of volatile SiCl₄

**Etch rate characteristics:**

- **Low power, low temp:** ~0.3-0.5 μm/min (neutral radical limited)
- **Medium power:** ~0.5-1.5 μm/min (balanced radical/ion)
- **High power, high temp:** ~1.0-2.0 μm/min (becomes ion-energy limited or thermal-desorption limited)

### 5.4.2 Ion-Assisted Silicon Etch

**Pure Cl₂ chemistry becomes ion-assisted at moderate-to-high RF power.**

The ion energy (typically 50-200 eV) is sufficient to:

1. Break Si-Si backbonds and create reactive surface sites
2. Cause physical sputtering of chlorosilane intermediates
3. Increase effective reaction rate beyond what Cl· alone can achieve

**Etch rate increase with ion energy:**

$$E_{\text{ion-assisted}} = E_{\text{neutral}} + k_i \times j_{\text{ion}} \times E_{\text{ion}}^{\alpha}$$

Where:
- $k_i$ is ion-assist coefficient
- $j_{\text{ion}}$ is ion current density
- $E_{\text{ion}}$ is ion impact energy
- α ≈ 0.5-1.0 (empirical exponent)

This explains why etch rate increases sharply with applied power in the 1-8 kW range for 3D NAND etch.

### 5.4.3 Selectivity: Silicon over SiO₂

**Goal:** Etch polysilicon word lines while protecting SiO₂ sacrificial layers.

**Mechanism:**

SiO₂ is much less reactive to Cl· than silicon because:

1. **Si-O bonds stronger:** Bond dissociation energy Si-O ≈ 840 kJ/mol vs. Si-Si ≈ 320 kJ/mol
2. **Surface saturation:** SiO₂ surface becomes saturated with Cl; further reaction requires ion-assisted breaking of Si-O bonds
3. **Stoichiometry:** SiO₂ + nCl· doesn't readily form volatile products

**Achieving Si/SiO₂ selectivity (>10:1):**

Strategy: **Use low ion energy and neutral-limited etch**

- Lower RF power to reduce ion flux and energy
- This reduces Si etch rate only slightly (it's limited by Cl· availability anyway)
- But SiO₂ etch rate drops dramatically (it depends strongly on ion assist)

Result: At 2-4 kW power and 50-70 V bias:
- Si etch rate: ~0.5-1.0 μm/min
- SiO₂ etch rate: ~0.05-0.1 μm/min
- Selectivity: 5-20:1

### 5.4.4 Sidewall Passivation on Silicon

When etching polysilicon in chlorine, the sidewalls can accumulate SiCl_x deposits that form a **passive layer**:

$$\text{Si sidewall} + \text{Cl} \rightarrow \text{Si-Cl}_x \text{ (polymer-like)}$$

This layer:
1. Protects the sidewall from further lateral etch
2. Contributes to vertical sidewall profile (no lateral undercut)
3. Can cause aspect ratio-dependent effects if too thick

**Thickness control:**

Thinner sidewall passivation → more lateral etch rate → more undercut/taper
Thicker sidewall passivation → less lateral etch rate → more vertical profile

Balance is achieved by adjusting:
- Ion energy (higher energy → thinner passivation)
- Temperature (higher temp → faster passivation layer removal)
- Gas mix (HCl addition can modify passivation)

## 5.5 SiO₂ (Oxide) Etch Chemistry

### 5.5.1 Why SiO₂ is Harder to Etch with Cl₂

Silicon dioxide is relatively inert to chlorine radicals compared to silicon because:

1. **Si-O bonds are polar and strong**
2. **Surface is oxidized:** Si-O-Si species; additional Cl· attack doesn't readily produce volatile products
3. **No simple SiCl₄ formation path:** Would require breaking Si-O-Si framework

**Observation:** Pure Cl₂ is inefficient for SiO₂ etch; fluorine-based chemistries are much more efficient.

### 5.5.2 Cl₂-Based SiO₂ Etch Mechanisms

Despite these challenges, Cl₂ can etch SiO₂ via:

**1. Ion-assisted mechanism:**

Ions (Cl⁺, Ar⁺, etc.) break Si-O bonds; Cl· radicals then attack reactive sites:

$$Si-O-Si \xrightarrow[\text{impact}]{ion} Si^* + O + Si^*$$

$$Si^* + Cl \rightarrow SiCl_x$$

Etch rate strongly dependent on ion energy and flux.

**2. Oxygen desorption:**

At elevated temperature, oxygen can desorb from SiO₂ surface; chlorine then attacks:

$$SiO_2 \xrightarrow{\text{high T}} Si + O_{(desorbed)}$$

$$Si + Cl \cdot \rightarrow SiCl_x$$

This becomes more important at higher wafer temperatures.

**3. Hydroxyl-assisted etch:**

If moisture is present, HCl/H₂O species can attack SiO₂:

$$SiO_2 + HCl + e^- \rightarrow \text{products}$$

Not used in modern vacuum etch; mentioned for completeness.

### 5.5.3 Selectivity: SiO₂ over Silicon

**Goal:** Etch sacrificial oxide while protecting polysilicon word lines.

**Challenge:** Natural selectivity of Cl₂ is opposite to what's needed: Si etches faster than SiO₂.

**Solution: Control mechanism to favor oxide etch**

Achieved by **increasing ion energy and flux:**

- Higher RF power (6-10 kW) → more ions
- Higher bias voltage (120-200 V) → higher ion energy
- Lower pressure (30-50 Pa) → better ion collimation

Result at high power/high bias:
- Si etch rate: ~1.5-2.0 μm/min (ion-assisted)
- SiO₂ etch rate: ~0.5-1.5 μm/min (ion-dependent)

But this is still not ideal selectivity for oxide over silicon. **Dynamic selectivity switching** is needed: Process in phases with different chemistries/powers.

### 5.5.4 Byproducts: SiCl₂, SiCl₄

Primary byproducts of SiO₂ etch in Cl-based chemistry:

**SiCl₂:** Reactive intermediate
$$\text{SiO}_2 + Cl \rightarrow \text{SiCl}_2 + O$$

SiCl₂ can:
1. React further with Cl: $SiCl_2 + Cl \rightarrow SiCl_3$
2. Recombine: $2 SiCl_2 \rightarrow Si_2Cl_4$ (polymeric)

**SiCl₄:** Final volatile product

$$Si-Cl_x + Cl \rightarrow SiCl_4 + \text{ligands}$$

SiCl₄ is volatile at typical etch temps (~50-80°C for process, but can be ~150-200°C at wafer surface with ion bombardment).

**Condensation risk:**

In deep trenches or cool regions of the chamber, SiCl₄ can condense:

$$SiCl_4 \text{ (gas)} \rightarrow SiCl_4 \text{ (liquid/solid)}$$

This condensed byproduct forms the residue discussed in Chapter 3. Residue management is critical for high-AR etch.

## 5.6 Silicon Nitride (Si₃N₄) Etch Chemistry

### 5.6.1 Si₃N₄ in Chlorine

Silicon nitride is intermediate in reactivity between Si and SiO₂:

$$Si_3N_4 + \text{Cl radical/ion} \rightarrow \text{products}$$

The Si-N bond energy (~450 kJ/mol) is intermediate between Si-Si and Si-O.

**Etch products:**

Not completely characterized, but likely involve:
- Volatile SiCl_x (from Si component)
- NCl₃ or N₂ (from N component; nitrogen radicals readily escape)
- Mixed SiNCl_x species

### 5.6.2 Selective SiO₂/Si₃N₄ Etch

**Goal:** Etch through SiO₂ layer while preserving Si₃N₄ liner/charge trap layer.

**Challenge:** Both materials are relatively inert to Cl; selectivity window is tight.

**Strategy:**

Use high-power, high-bias chlorine etch, but with **very tight timing**:

1. **SiO₂ etch phase:** 1.5-2.0 μm/min
2. **Si₃N₄ etch phase (slow):** 0.1-0.3 μm/min
3. **Selectivity:** ~10:1 if process is controlled

Selectivity is achieved by:
- Ion-energy dependence (Si₃N₄ more resistant to ion damage than SiO₂)
- Temperature effects (Si₃N₄ remains protective at mod temperatures)

**In practice:** Many 3D NAND processes use **dynamic chemistry switching** to separate SiO₂ and Si₃N₄ etch phases rather than relying on selectivity alone.

## 5.7 Byproduct Chemistry and Residue Formation

### 5.7.1 Primary Byproducts

**From Si etch:**
- SiCl₂, SiCl₃, SiCl₄ (volatility increases: SiCl₂ < SiCl₃ < SiCl₄)
- Etch rate often correlates with SiCl₄ production

**From SiO₂ etch:**
- SiOCl, SiOCl₂, SiO₂Cl (oxygen-containing chlorosilanes)
- These are typically volatile but can condense in cool regions

**From Si₃N₄ etch:**
- Complex mixed SiNCl_x species
- Nitrogen oxychlorides (NOCl)
- Nitrogen can escape as N₂

### 5.7.2 Polymerization and Residue

In deep trenches, byproducts can:

1. **Recombine:** SiCl₂ + SiCl₂ → Si₂Cl₄ (polymeric)
2. **Oxidize:** SiCl_x + O → SiOCl_x (via reactions with oxygen from SiO₂ etch)
3. **Condense:** Cool regions near hole bottom → solid deposits

**Residue composition:** Typically SiOxCly or Si-O-Cl polymers with x = 1-3, y = 2-4.

**Residue consequences:**
- Conductive deposits can cause parasitic leakage
- Blocks subsequent process steps
- May degrade endpoint detection capability

### 5.7.3 Residue Prevention Strategies

**During etch:**

1. **Higher temperature:** Keeps byproducts volatile
2. **Better convection:** Gas flow helps remove byproducts (challenging in deep holes)
3. **Ion-assist flux:** Ions can break up nascent polymers

**Post-etch (in-situ ash):**

1. **Plasma ash:** Additional etch step using O₂/Ar plasma to remove deposits
2. **Remote plasma ash:** Ash occurs in separate chamber; allows separate temperature/pressure optimization
3. **Combination:** Cl₂ for etch; O₂ for ash removal

Ash step typically adds 5-10 minutes per wafer to cycle time.

## 5.8 Process Parameter Sensitivities

### 5.8.1 Etch Rate vs. Power

**Power sensitivity:** Etch rate approximately proportional to ion flux:

$$E \propto P$$

Doubling power roughly doubles etch rate (within limitations of ion-to-neutral balance).

**Example:** 
- 3 kW → 0.5 μm/min
- 6 kW → 1.0 μm/min
- 10 kW → 1.5-1.8 μm/min (saturation begins; ion-limited etch)

### 5.8.2 Etch Rate vs. Pressure

**Pressure sensitivity:** Complex dependence.

- **Too low:** Ion mean free path is large; ions lose direction; effective ion flux to trenches drops
- **Optimal:** ~50-70 Pa; good transport balance
- **Too high:** Ion-neutral collisions reduce ion energy; etch becomes neutral-dominated

Result: Etch rate peaks around 50-80 Pa; falls off at both lower and higher pressures.

### 5.8.3 Etch Rate vs. Temperature

**Temperature dependence (Arrhenius):**

$$E(T) = E_0 \exp\left(\frac{E_a}{R}\left(\frac{1}{T_0} - \frac{1}{T}\right)\right)$$

Typical activation energy $E_a$ ≈ 20-50 kJ/mol.

Doubling etch rate requires ΔT ≈ 20-40°C.

**Implication:** Tight temperature control (±5°C) is necessary for etch rate stability ±20%.

### 5.8.4 Selectivity Drift

Selectivity is sensitive to many parameters:

- **Power:** Higher power shifts selectivity toward ion-assisted regime
- **Pressure:** Affects ion/neutral ratio
- **Temperature:** Affects reaction rates of different materials differently
- **Workload/pattern:** ARDE effects change selectivity with local AR

**Production implication:** Endpoint detection is critical; run-to-run selectivity variation of ±20% is typical without active feedback.

## 5.9 Summary: Chlorine Chemistry for 3D NAND

**Strengths:**

1. Versatile: Can etch Si, SiO₂, Si₃N₄ with adjustable selectivity
2. Mature: Decades of process development
3. Scalable: Works from low-AR to ultra-high-AR features
4. Cost-effective: Chlorine gas is inexpensive

**Weaknesses:**

1. SiO₂ etch requires high ion assist (high power) → thermal load
2. Selectivity windows tight; requires dynamic chemistry switching
3. Residue formation in deep trenches; requires ashing
4. Etch rate sensitive to temperature, pressure, power; requires active control

**Modern 3D NAND approach:**

Staged etch with chemistry switching:
- **Phase 1:** SiO₂-selective (lower power, controlled ion assist)
- **Phase 2:** Si-selective (moderate power, Cl₂ + BCl₃)
- **Phase 3:** Si₃N₄-selective (may switch to F-based chemistry)
- **Phase 4:** Ash/residue removal (O₂/Ar plasma)

---

**Key Takeaways:**

1. **Cl· radicals** are primary etch species; produced via electron impact dissociation of Cl₂
2. **Si etch** is mainly neutral-limited; selectivity over SiO₂ achieved by using low-power, neutral-dominated regime
3. **SiO₂ etch** requires high ion assist; selectivity depends on ion/neutral balance
4. **Si₃N₄ etch** is intermediate; often requires chemistry switching for good selectivity
5. **Residue formation** is a major challenge at extreme aspect ratios; post-etch ash is mandatory

---

*Next Chapter: [Chapter 6 - Fluorine-Based Alternatives and Advanced Chemistries](chapter-06-fluorine-alternatives.md)*
