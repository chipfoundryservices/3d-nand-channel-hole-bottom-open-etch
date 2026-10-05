# Chapter 7: Mixed Cl/F Chemistries and Selectivity Switching

## 7.1 Rationale for Selectivity Switching

Traditional deep trench etches used a single chemistry for the entire process. But 3D NAND's complexity requires **multiple material etch phases**, each optimized for different selectivity requirements:

**Layer sequence in 176-layer 3D NAND:**

```
Polysilicon word lines (30 nm each × 176 layers)
├─ interspersed with
SiO₂ sacrificial layers (20-30 nm each)
├─ with
Si₃N₄ liners (5-10 nm) sandwiching
Charge trap layers
```

**Selectivity requirements:**

1. **Etching through stacked oxide:** Need SiO₂ etch >> Si etch (protect word lines) → F-based chemistry
2. **Etching polysilicon word lines:** Need Si etch >> SiO₂ etch (protect sacrificial) → Cl-based chemistry
3. **Approaching nitride/etch stop:** Need different chemistry → mixed or F-based for oxide specificity

**Single chemistry cannot satisfy all requirements** → Dynamic switching needed.

## 7.2 Multi-Stage Process Sequences

### 7.2.1 Typical 5-Stage Etch Sequence (176-layer example)

**Stage 1: Initial SiO₂ Removal (2-3 minutes)**
- Chemistry: C₄F₆ + 40% Ar
- Pressure: 30-40 Pa
- Power: 4-5 kW, Bias: 80-100 V
- Goal: Etch first ~1 μm of SiO₂ (top ~10-15 sacrificial layers)
- Selectivity: SiO₂/Si > 15:1 (protect top word line)

**Stage 2: Polysilicon Etch (3-4 minutes)**
- Chemistry: Cl₂ + 30% BCl₃
- Pressure: 50-70 Pa
- Power: 5-7 kW, Bias: 120-150 V
- Goal: Etch all polysilicon word lines (~30-35 nm each × 176)
- Selectivity: Si/SiO₂ > 10:1 (protect sacrificial oxide)
- **Challenge:** High current density; tight temp control needed

**Stage 3: Middle SiO₂ Removal (3-4 minutes)**
- Chemistry: C₄F₆ + Ar (or mixed Cl₂/C₄F₆)
- Pressure: 40-60 Pa
- Power: 4-5 kW, Bias: 100-120 V
- Goal: Etch remaining sacrificial SiO₂
- Selectivity: SiO₂/Si₃N₄ (protects nitride liners)

**Stage 4: Final Approach to Etch Stop (1-2 minutes)**
- Chemistry: Cl₂ (conservative, low power)
- Pressure: 60-80 Pa
- Power: 2-3 kW, Bias: 80-100 V
- Goal: Reach tungsten etch stop
- Selectivity: Si/W >> 100:1 (stop on tungsten)
- **Critical:** Avoid tungsten over-etch; process sensor must detect endpoint

**Stage 5: In-Situ Ash/Residue Removal (5-10 minutes)**
- Chemistry: O₂/Ar plasma (different chamber or same chamber with separate gas)
- Power: 2-3 kW
- Temperature: 80-100°C (higher temp helps residue removal)
- Goal: Remove SiOxCly deposits, polymerized residue
- **Essential:** High-AR holes cannot function with residue at bottom

**Total time:** ~35-50 minutes per wafer

### 7.2.2 Chemistry Transitions

**Between-stage transitions (~30-60 seconds per transition):**

1. **Gas switchover:** Close Cl₂/BCl₃ valve; open C₄F₆/Ar valve (or vice versa)
2. **Pump-down/stabilization:** Allow chamber to re-equilibrate to new chemistry
3. **Power/pressure adjustment:** Ramp RF power and pressure to new setpoints
4. **Delay:** ~20-30 s for chamber to stabilize before resuming etch

**Careful timing needed:**

- Too fast → incomplete previous etch phase → defects
- Too slow → wafer temperature drifts; overlapped phases cause selectivity loss

## 7.3 Chemistry Mixing Strategies

### 7.3.1 In-Situ Mixing (Single Chemistry Sequence)

**Approach:** Mix Cl₂ and C₄F₆ continuously; tune selectivity by power/pressure only

**Example:** 50% Cl₂ + 50% C₄F₆

- **Low power (2-3 kW):** F-radical dominated → SiO₂-selective
- **High power (6-8 kW):** Cl-radical and ion-assist dominated → Si-selective

**Advantage:** Single gas system; fewer transitions

**Disadvantage:** Selectivity range is smaller; less material-specific optimization

### 7.3.2 Sequential Chemistry (Staged Switching)

**Approach:** Complete etch with one chemistry, then switch to another

**Example (as outlined in 7.2.1):**
- Stage 1-3: Mix C₄F₆/Ar and Cl₂/BCl₃ in distinct phases
- Clear gas switchover between stages

**Advantage:** Maximum selectivity control for each phase

**Disadvantage:** Longer total time; more complex gas handling

## 7.4 Endpoint Detection Across Chemistry Phases

### 7.4.1 OES Spectroscopy for Phase Detection

**Optical Emission Spectroscopy (OES)** monitors plasma light emission:

**Key spectral features:**

| Chemistry | Dominant Lines | Purpose |
|-----------|---------|---------|
| Cl₂/BCl₃ | Cl (837.6 nm) | Detect Cl plasma presence |
| C₄F₆/Ar | F (703.0 nm), C (193.0 nm) | Detect F and C emission |
| O₂/Ar (ash) | O (776 nm), Ar (751 nm) | Detect ash phase |

**Material transition detection:**

- **Poly→SiO₂ transition:** Cl emission increases (assuming Si-selective Cl phase going to SiO₂-etch phase)
- **SiO₂→Si₃N₄ transition:** Spectral signature change; possibly Cl emission drops as selectivity changes
- **Si/SiO₂→Tungsten approach:** Unique spectral feature (W may have characteristic emission, or disappearance of other elements)

**Endpoint setting:**

Operators manually set OES threshold for each transition based on test runs. Challenge: threshold may drift due to:
- Chamber wall condition changes
- Electrode erosion
- Workload-dependent effects

### 7.4.2 Pressure-Based Endpoint (Secondary)

**Alternative/supplementary method:** Monitor chamber pressure change

- **Etch rate change** → byproduct generation rate changes → pressure may shift slightly
- Less reliable than OES; susceptible to pump variations

## 7.5 Practical Challenges and Solutions

### 7.5.1 Selectivity Loss at High Aspect Ratios

**Problem:** Selectivity measured at low AR (test structures) differs significantly from high-AR production holes.

**Reason:** In high-AR holes, neutral transport is depletion-limited → ion-assist becomes critical → changes selectivity ratio.

**Example:**
- Measured selectivity SiO₂/Si: 15:1 at 10:1 AR test structure
- Actual production (150:1 AR): ~5-8:1 in high-AR holes, ~15:1 in low-AR holes
- **Result:** Loading effects; etch uniformity degrades

**Solution:** Use **ARDE feedback** (Chapter 14) to adjust process parameters in real-time based on estimated AR

### 7.5.2 Temperature Drift During Extended Etch

**Problem:** Extended etch cycles (40+ minutes) allow thermal drift even with cooling

**Scenario:**
- Chamber walls heat up over time → radiant heat to wafer increases
- Coolant temperature rises slightly
- Wafer temp creeps up 10-15°C over a 50-minute etch

**Effect:** Etch rate increases 20-40% by end of etch → depth uniformity suffers

**Solutions:**
1. Periodic power adjustment: Reduce RF power in later stages to maintain constant etch rate
2. Improved chamber thermal management: Larger thermal mass; better coolant control
3. Process staging: Insert ash/cool-down periods between etch phases

### 7.5.3 Residue Accumulation Between Stages

**Problem:** Byproducts from Cl₂ phase (SiCl₄) can condense during transition to cooler F-phase

**Result:** Residue builds up; ash step effectiveness decreases

**Solution:** Brief purge cycle between phases; inject inert gas (Ar/N₂) to sweep chamber and prevent residue settling

### 7.5.4 Tungsten Etch Stop Consistency

**Challenge:** Detecting when etch reaches tungsten is critical; over-etch causes resistance increase

**Variation sources:**
- Tungsten layer thickness varies wafer-to-wafer (±10-20 nm typical)
- Chamber drift causes etch rate variation → endpoint timing shifts

**Solutions:**
1. Tight OES threshold setting with frequent recalibration
2. Backup endpoint detection (e.g., pressure rise when reaching etch stop)
3. Conservative final approach: Use very low power in final 2-3 minutes to limit over-etch

## 7.6 Industry Adoption (2024-2026)

**By technology node:**

- **96-layer (phasing out):** 60% use chlorine-only; 40% use staged Cl/F
- **176-layer (mainstream):** 30% staged Cl/F; 50% mixed Cl/F throughout; 20% F-dominant
- **200+ layer (emerging):** 80%+ use multi-stage Cl/F strategies; highest layers pushing F-dominant

**Trend:** Increasing complexity and frequent chemistry switching as aspect ratios exceed 200:1

## 7.7 Future Directions

**Next-generation chemistry advances (2027-2030):**

1. **AI-assisted process optimization:** Machine learning to predict optimal chemistry transitions for each wafer
2. **Adaptive selectivity:** Real-time plasma parameter adjustment based on OES feedback
3. **Alternative chemistries:** Bromine-based (Br₂) or iodine-based (I₂) systems; exploring for next-gen selectivity requirements
4. **Remote plasma chemistry:** Pre-activate radicals in separate chamber → deliver controlled radical flux → better uniformity potential

---

**Key Takeaways:**

1. **Selectivity switching** is mandatory for 3D NAND; no single chemistry meets all requirements
2. **Typical 5-stage sequence:** oxide etch → poly etch → oxide etch → final approach → ash
3. **OES endpoint detection** is critical; spectral signatures guide phase transitions
4. **ARDE effects** degrade selectivity at high aspect ratios; feedback correction essential
5. **Process complexity** increases significantly above 176 layers; future scaling will demand advanced control

---

*Next Chapter: [Chapter 8 - Byproduct Chemistry and Residue Formation in Deep Trenches](chapter-08-residue-chemistry.md)*
