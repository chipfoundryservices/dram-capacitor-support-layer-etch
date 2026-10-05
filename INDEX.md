# Index: Book #34 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 20–28 hours for the complete book; 5–9 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the role of the supports, the nitride film, hydrofluorocarbon chemistry and the polymer-film model, lattice design and opening statistics |
| II | 5–9 | Hardware: CCP chambers, selectivity levers, trim and finishing tools, endpoint, polymer and post-etch clean |
| III | 10–14 | Phenomena: profile and CD, pillar tops and two classes, residue statistics, charging and free pillars, sequential and multi-support schemes |
| IV | 15–16 | Production: metrology, inspection, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The Support Layer & Why It Is Etched](./chapters/01-support-layer-role.md)
**Estimated Time:** 60 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** What do the supports do, how many openings are there, and what passes through them?

**Key Topics:**
- 4.25 × 10⁹ openings per layer per die; 14.4% of the array area is nitride being cut
- The clover: free area 1013 / 938 nm²; 20 / 22 nm inscribed circle; closed by the top electrode
- 75% of pillars touched, 25% never; routes S0, S1, S2, S3, P; the specification sheet

**Critical Equations:** openings = cells/(A_lattice/A_cell); A_lens (crescent); free area = πR² − 3A_lens  
**Study Questions:** 6

---

### Chapter 2: [The Support Film — Nitride Families, Stack, Incoming Surface & Etch Behaviour](./chapters/02-support-film-families.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What film does the etch cut, and what does it ask of the plasma?

**Key Topics:**
- PECVD low-H SiN after the TiN fill: H 14 → 8 at%, HF 1.5 → 1.0 nm/min, plasma rate × 0.81
- Hydrogen: +4% per at% in the plasma, +7% per at% in HF; the soft ends of the middle support
- Incoming CMP skin, TiON, dishing, seams
- SiCN, SiBN, SiON, PEALD: HF loss versus plasma time, TiN loss, and mask

**Critical Equations:** rate ∝ 1 + 0.04 (H − 8); mask = Σ film × OE / (3 × rel. rate)  
**Study Questions:** 6

---

### Chapter 3: [Plasma Chemistry of Nitride Etching Between Metal Pillars](./chapters/03-nitride-plasma-chemistry.md)
**Estimated Time:** 70 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** How does a plasma cut nitride and spare TiN, and why is most of the TiN lost early?

**Key Topics:**
- ΔH: Si₃N₄ −1680, SiO₂ −1020 kJ per Si; TiF₄ sublimes at 284 °C, so fluorine passivates TiN
- Polymer model: d_m = (1 − c_m) d₀; steady SiN:TiN 294; ion energy and distribution width as weak levers
- Transient: 77% of the loss in the first 8.5 s; 4 s flash: 2.36 → 0.97 nm; integral selectivity 93 → 226
- SN2 at aspect ratio 17: 150 nm/min, soft landing

**Critical Equations:** ER = R⁰(E) e^(−d_m/λ); L(t) = (R⁰λ/v_d)[e^(−d_f/λ) − e^(−(d_f + v_d t)/λ)]  
**Study Questions:** 6

---

### Chapter 4: [Lattice Design, Pattern Transfer & Opening Statistics](./chapters/04-lattice-design-opening-statistics.md)
**Estimated Time:** 70 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Research  
**Focus:** How many openings can fail, and what kind of failure strands oxide?

**Key Topics:**
- Five layouts; overlap depth 20.2 nm at 3σ; ligament margin after the dip 1.18
- HF reach 95 nm at 105 s; empty circles 90 / 104 / 119 / 156 nm; p ≤ 1.06 × 10⁻⁴ for triangles
- Killer-defect footprint 154 nm; yield loss 0.6% at D_k = 0.02/cm²; S2 insensitive to clusters
- Ligament stress with edge roughness; the 47–53 nm CD window

**Critical Equations:** R_crit = R + vt/τ; λ = N n pᵏ; σ_peak = σ P/(P − D) · K_hole · K_rough  
**Study Questions:** 6

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [CCP Chambers for the Nitride Lattice Open](./chapters/05-ccp-chambers-nitride-lattice.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Focus:** What does the nitride step ask of a chamber that the oxide step did not?

**Key Topics:**
- Sheath 6.4 mm, ion transit 280 ns; τ_i/τ_RF at 60 MHz, 2 MHz, 400 kHz; IEDF
- Chamber memory: SN2 starts with 0–1.6 nm of polymer; the flash resets it
- Full S1 recipe (226 s); consumable wear: 0.4 nm of film = +27% SiN, +49% TiN
- Edge-ring tilt 1.3 nm per 0.1°; throughput 36.0 wafers/h; HCN abatement

**Critical Equations:** λ_D = 7430 √(T_e/n); τ_i = 3 s √(m/2eV); offset = 770 nm × tan θ  
**Study Questions:** 6

---

### Chapter 6: [Ion Energy, Bias Pulsing & Temperature — The Selectivity Levers](./chapters/06-ion-energy-pulsing-temperature.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment  
**Focus:** Which knobs move the TiN loss, and which only move the rate?

**Key Topics:**
- Energy sweep: 400 → 200 eV saves 14 nm of mask and 0.19 nm of TiN, costs 55% in time
- The width of the distribution does not matter (Jensen); the tailored waveform has no benefit
- Pulsing: f(D) = D + β(1 − D); 10 kHz, 80%; the wafer starts cold; the flash is a soak
- Sensitivity at constant nitride cleared: flat to ± 0.08 nm except the flash (+1.43 nm without)

**Critical Equations:** f(D) = D + β(1 − D); d₀(T) ∝ exp[(E_s/k)(1/T − 1/T_ref)]  
**Study Questions:** 6

---

### Chapter 7: [Radical, Atomic-Layer & Wet Nitride Removal — Trim, Finish & Stencil Routes](./chapters/07-radical-ale-wet-nitride-removal.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment/Research  
**Focus:** What can non-ion tools trim or finish, and how far do they reach?

**Key Topics:**
- Remote NF₃: 10 nm/min, SiN:SiO₂ 12, a 1.5 nm TiF skin; the trim budget is 1.5 nm per side
- Radical dose at 770 nm: 12% (s = 0.005); ion starvation at 35 eV: 14%
- Plasma ALE: 5.5 nm/min at the top, 1.2 nm/min at the middle support
- Hot H₃PO₄: reaches everywhere and trims everything; tool-to-job matrix

**Critical Equations:** λ = 1.155 r/√s; θ₁/e = atan(√(T_i/E)); fraction = 1 − exp(−(θ_a/θ₁/e)²)  
**Study Questions:** 6

---

### Chapter 8: [Endpoint & In-Situ Monitoring of a Thin Nitride in a 50 nm Opening](./chapters/08-endpoint-in-situ-monitoring.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Focus:** What can emission tell about a 50 nm film at the bottom of a column?

**Key Topics:**
- 1.6 sccm of N atoms in 363 sccm; CN at 388.3 nm; escape time 78 ns
- SN1 signal −85% (S/N 280); SN2 −25% (S/N 80); why interferometry fails
- An endpoint cannot shorten the overetch; wafer-to-wafer spread 4.5% → 0.5%
- The flash as a sensor (CF₂ integral); endpoint logic and fault conditions

**Critical Equations:** τ = L²/D_K; D_K = (2r/3) v̄; d_f = 1.6 nm × I_CF2/I_ref  
**Study Questions:** 6

---

### Chapter 9: [Walls, Polymer, Particles & Post-Etch Clean](./chapters/09-walls-polymer-post-etch-clean.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment  
**Focus:** Can the acid get into the column?

**Key Topics:**
- 5 nm of polymer per wafer on the walls; first-wafer effect +9.4% SiN, +16% TiN; seasoning
- Particles: 10 adders ≥ 30 nm → 5 × 10⁻⁴/cm² killers, 40 times under budget
- Cassie coverage: θ ≤ 60° at φ ≤ 0.365; radical-only strip leaves φ = 0.60 at depth
- Ion flush: φ = 0.21; TiN oxide +0.9 nm; failure probability 2.9 × 10⁻⁷ at φ = 0.21

**Critical Equations:** cos θ = φ cos θ_p + (1 − φ) cos θ_s; φ(t) = exp(−Σ t f/τ); P = ½ erfc[(0.61 − μ)/(σ√2)]  
**Study Questions:** 6

---

## Part III: Process Phenomena (Chapters 10–14)

### Chapter 10: [Opening Profile, CD & Pattern Fidelity](./chapters/10-opening-profile-cd-fidelity.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What does the column look like at the middle support, and how much margin is there?

**Key Topics:**
- 44 ± 3.0 nm at the middle support against 40 nm; taper 0.22° per side
- Free area versus CD (30 nm² per nm at the middle support); roughness 2.0 → 1.5 nm
- Overlap at the wafer edge 20.2 nm; landing depth 100 ± 6.5 nm
- S2: the opening is an ion image: 38.4 nm cleared at 400 eV, 40.5 nm at 600 eV

**Critical Equations:** σ_x = H tan θ₁/e /√2; cleared width = w − 2 × 0.4 √2 σ_x  
**Study Questions:** 6

---

### Chapter 11: [The Pillar Tops — TiN Loss, Two Classes of Cells & Fluorine Uptake](./chapters/11-tin-pillar-top-loss-two-classes.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Device  
**Focus:** What does the plasma do to the three pillars of each opening, and what does it do to the fourth?

**Key Topics:**
- Crescent top 317 nm², arc 38.2 nm; capacitance loss 0.10% (S1); edge radius 6 nm, field +18%
- Open seam: 7.6% of touched pillars; slot depth 12.5 / 8 / 2.4 nm
- Touched versus untouched table; F-delayed ZAZ; weak cells 34 / 14 / 1.3 per die
- The class signature: 97% against 75%; 50 fails give z = 3.6

**Critical Equations:** ΔC/C = arc × loss/(π d L); FEF = (t/r)/ln(1 + t/r); z = (f − 0.75)/√(0.75·0.25/N)  
**Study Questions:** 6

---

### Chapter 12: [Slivers, Scum & Not-Open Openings — Residue Statistics](./chapters/12-slivers-scum-not-open.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** What is left behind, and what of it matters?

**Key Topics:**
- 93° nitride wedge; the sliver as a fin: 2.2 nm wide, 15 nm tall at OE 40%
- Monte Carlo: 1.7% of corners ≥ 3 nm; 99.9th percentile 3.3 nm; HF leaves whiskers
- The Gaussian tail is 20.7σ away; not-open events are micromasks
- Stranded-oxide budget: 6.2 × 10⁻³ clusters per die; φ = 0.35 would give 1.7

**Critical Equations:** f(x) = 1 − (1 − f₀)e^(−x/ℓ); x_s = ℓ ln[(1 − f₀)/(1 − 1/(1 + OE))]  
**Study Questions:** 6

---

### Chapter 13: [Charging, Electrostatics & Free-Standing Pillars in the Plasma](./chapters/13-charging-electrostatics-free-pillars.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Research/Process  
**Focus:** How do floating pillars charge, and when do they pull together?

**Key Topics:**
- 2.5 fA into a crescent; 1 fF → 2.5 V/s; clamp at 10 V in 3.9 s; pulsing and the waveform do not help
- Junction stress dose 0.14 C/cm² on the touched class in S1
- Pressure 1.5 MPa at 10 V; pull-in 12.3 / 7.1 / 5.5 V for a 650 nm span
- S2A (flux 16%, ΔV 4 V) versus S2D (every pillar touched); opening stress relaxation 0.04 nm

**Critical Equations:** I = eΓ_i A_c; p = ε₀(ΔV/g)²/2; V_pull² = (g/3)(4g²/9)/(c ε₀ d L⁴/2EI)  
**Study Questions:** 6

---

### Chapter 14: [Advanced Schemes — Sequential Opens, Three-Support Molds, HF-Resistant Supports, Pre-Opened Lattices, 4F² & 3D DRAM](./chapters/14-advanced-multi-support-schemes.md)
**Estimated Time:** 70 min | **Difficulty:** Advanced | **Reading Level:** Integration/Research  
**Focus:** What does a sequential route need, and what does it cost?

**Key Topics:**
- S_HF ≥ 296; PSG + SiN fails the ligament (0.99); SiCN: 1.18 nm per wall, margin 1.22
- Free pillar sidewalls: λ = 139 nm, ≈ 1% of C_s; S2D 118 s / 1.8 nm; S2A 183 s / 1.3 nm
- S3 at 1d-class: 1.9 × 10¹⁰ openings per die, pull-in 2.6–8.1 V, every pillar touched
- Pre-opened lattice (hole drift 3–6 nm); 4F², 3D DRAM; route selection

**Critical Equations:** Δ = h(1 + OE)/S_HF; S_HF ≥ h(1 + OE)/Δ_budget; ΔC/C ≈ (f/r) ∫δ dz/L  
**Study Questions:** 6

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Metrology, Inspection & Advanced Process Control](./chapters/15-metrology-inspection-apc.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** All roles  
**Focus:** Measuring what cannot be seen from above

**Key Topics:**
- The measurands; the middle support from XTEM, OCD (± 1.5 nm), and inference
- Scribe test structures (TiN witness, deep-hole array); killer-defect inspection area 150 cm² at 0.02/cm²
- Virtual metrology for TiN loss (0.12 nm); feed-forward trim; EWMA limits ± 0.15 nm
- The measurement ladder; the class-aware bitmap

**Critical Equations:** A = −ln(0.05)/D_k; z_k = λx_k + (1 − λ)z_{k−1}; limit = Lσ√(λ/(2 − λ))  
**Study Questions:** 6

---

### Chapter 16: [Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management  
**Focus:** Which route, at what cost, for what yield?

**Key Topics:**
- Customers of the etch; queue times; yield signatures per die (S1)
- Equipment at 150,000 starts/month: 7 / 7 / 8 / 9 etch platforms for S0 / S1 / S2D / S2A
- Module cost: $16.6 / $17.5 / $56.2 / $27.6; break-even yield gain 0.16% (S2A), 0.6% (S2D)
- New-product checklist

**Critical Equations:** N = starts/(wph × 8760 × 0.85); break-even = Δ cost/($65 per %)  
**Study Questions:** 6

---

## Appendices

- [Appendix A: Material Properties](./appendices/A-material-properties.md)
- [Appendix B: Chemistry & Thermochemistry Data](./appendices/B-chemistry-thermochemistry-data.md)
- [Appendix C: Standard Procedures](./appendices/C-standard-procedures.md)
- [Appendix D: Process Windows](./appendices/D-process-windows.md)
- [Appendix E: Lattice, Etch & Electrostatics Calculations](./appendices/E-lattice-etch-electrostatics-calculations.md)
- [Appendix F: Metrology Reference](./appendices/F-metrology-reference.md)
- [Appendix G: Troubleshooting Guide](./appendices/G-troubleshooting-guide.md)
- [Glossary](./GLOSSARY.md)

---

## Reading Paths by Role

**Process Engineer (8 h):** Ch. 1 → 2 → 3 → 4 → 9 → 10 → 11 → 12 → App. D, G  
**Equipment Engineer (7 h):** Ch. 1 → 5 → 6 → 7 → 8 → 9 → 15  
**Integration Engineer (8 h):** Ch. 1 → 2 → 4 → 10 → 14 → 16  
**Device Engineer (5 h):** Ch. 1 → 11 → 13 → 16  
**Researcher (8 h):** Ch. 3 → 4 → 7 → 13 → App. E

---

## Study Questions Overview

**Total Study Questions:** 96 (6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Opening counts and areas, crescent and clover geometry, solid fraction, overlap depth, HF reach and killer clusters, ligament stress, polymer-film rates and selectivity, temperature dependence, transient TiN loss and the flash, ARDE and step times, sheath and ion transit, chamber memory, ring tilt, throughput, mask budget, radical attenuation, ion acceptance, ALE cycle times, nitrogen flow and endpoint, particle statistics, Cassie coverage and strip kinetics, wetting failure probability, CD budget, cleared width, capacitance loss, field enhancement, seam exposure, sliver width, Monte Carlo corner statistics, ion current and charging time, electrostatic pressure, pull-in voltage, sidewall fluorination, HF selectivity for sequential routes, inspection area, EWMA control, virtual metrology, equipment sizing, cost of ownership, break-even yield

Examples:
- Compute the number of openings per die for a new array and lattice
- Find the dip time at which a triangle of failed openings is just tolerable
- Predict the TiN loss of a nitride step from the flash time and the step time
- Compute the radical dose at the middle support for a new wall loss probability
- Find the strip duration that brings the polymer coverage at the bottom below 0.31
- Compute the cleared width of the middle-support opening in S2 at a new ion energy
- Compute the pull-in voltage of a free-standing span at a new pitch
- Find the sliver width at a new overetch and a new interface rate ratio
- Design an EWMA chart and compute its limits
- Size the equipment and compute the module cost of a route

---

## How to Use This Index

1. **First time?** Read PREFACE.md, then this INDEX, then Chapter 1.
2. **Focused reading?** Pick your role from the reading paths above.
3. **Reference mode?** Jump to the chapter. Use Appendix G for symptoms and Appendix E for formulas.
4. **Deep dive?** Read Chapters 1–16 in order and work the study questions.

---

**Index Version:** 1.0  
**Last Updated:** 2026-10-05  
**Next:** Begin [Chapter 1: The Support Layer & Why It Is Etched](./chapters/01-support-layer-role.md)
