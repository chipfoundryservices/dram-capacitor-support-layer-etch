# Chapter 9: Walls, Polymer, Particles & Post-Etch Clean

## Overview

The support layer etch ends with every surface it touched covered in fluorocarbon: the chamber walls, the upper electrode, the wafer's mask, and, down a column 770 nm deep, the walls of every opening. Two clean-ups follow. The first, of the chamber, decides whether the next wafer sees the same polymer film as the last. The second, of the wafer, decides whether hydrofluoric acid can enter the openings at all.

The second is the subject that matters. A fluorocarbon film is hydrophobic. If it covers more than about a third of the wall of an opening, liquid does not fill it reliably, trapped gas keeps the oxide beneath it, and a cluster of cells is lost (Book #30, Chapter 4). The post-etch strip has to remove the polymer from the bottom of a 50 nm column. The result of Chapter 7 applies to it too: **oxygen radicals reach the bottom of the column at a dose of a few percent to a few tens of percent of that at the top**. A radical-only strip cleans the top of the column and leaves the bottom coated. This chapter works through that result and the ion-assisted flush that solves it.

**Learning Objectives:**
- Account for the polymer on walls, wafer, and exhaust, and set the clean and maintenance intervals
- Explain the first-wafer effect after a clean and the seasoning that removes it
- Relate the particle specification to the killer-defect budget of Chapter 4
- Compute the water contact angle from the polymer coverage of a wall
- Compute the polymer coverage at the middle support after a strip of given type and duration
- Describe TiN oxidation and fluorine on the pillar tops and balance them against wetting
- Convert a mean coverage into a probability that a column does not fill

---

## 9.1 Where the Polymer Goes

### 9.1.1 Inventory

```
Polymer per wafer (S1, illustrative):
  Surface                           Deposited      Cleaned by
  ──────────────────────────────────────────────────────────────────────────────
  Chamber walls, electrode, ring    5.0 nm         waferless clean (per wafer)
    SN1 + SN2                       1.0 nm
    OX                              3.0 nm
    LAND                            1.0 nm
  Wafer: ACL top and mask edge      thick (consumed with the ACL)
  Wafer: TiN pillar tops            3.4 nm steady     post-etch treatment (§9.5)
  Wafer: opening walls              1–2 nm (oxide), 2 nm (nitride)    post-etch treatment
  Exhaust / foreline                CN-containing polymer, grams per month
```

### 9.1.2 The Exhaust

The nitride steps send HCN and cyanogen into the foreline (Chapter 3). Below 80 °C they polymerize on foreline walls and in the pump as a brown paracyanogen film. The forelines are heated to 80–100 °C and purged with nitrogen, the pump oil and purge are matched to HCN service, and the abatement (Chapter 5) is sized for the HCN and the PFC load together.

---

## 9.2 Cleaning and Conditioning the Chamber

### 9.2.1 Waferless Clean and What It Leaves

After each wafer (or each lot), an O₂/Ar plasma with a cover wafer removes the carbon from the walls in about 60 s. Oxygen cleans carbon and leaves fluorine, bound to the Y₂O₃ coating as YOF. A fraction escapes in the next etch:

```
Wall condition after a waferless clean (illustrative):
  Residual polymer             0.05 nm per wafer cycle (accumulates)
  After 13,500 wafers (1500 RF-hours at 9 wafers/h per chamber): 675 nm
  Limit before flaking         ≈ 1 µm  →  wet clean at ≈ 1500 RF-hours (with margin)
```

### 9.2.2 The First-Wafer Effect

The first wafer after a clean sees walls that have lost their polymer and carry fluorine, so the gas has a lower C/F ratio and the polymer film on TiN is thinner:

```
First wafer after a clean (illustrative):
  d₀                           3.25 nm  (reference 3.40 nm)
  SiN rate                     +9.4%
  TiN rate                     +16%
  Flash film                   1.6 nm × 0.96 = 1.5 nm
```

A 9% faster nitride step and a 16% faster TiN step are modest, and the flash masks most of the effect on the TiN loss. The remedy is to **season** the chamber: a CH₃F/Ar deposition of 10 s after the clean, with a cover wafer, that coats the walls with the same polymer the process makes. Two production wafers of the same recipe do the same job. Seasoning raises the time between wafers by 10 s and brings the first-wafer rate within 2% of the fleet (the matching limit of Chapter 5).

### 9.2.3 The Wet Clean

At about 1500 RF-hours the liners are wet cleaned and recoated. The Y₂O₃ and YOF coatings are inspected for loss, since a worn coating exposes aluminium, which forms AlF₃ and is a particle source. The silicon parts of Chapter 5 follow their own schedule.

---

## 9.3 Particles

### 9.3.1 Sources

```
Particle sources in the support layer etch chamber:
  Polymer flakes from walls and electrode        thick CNₓFᵧ films above ≈ 1 µm; the OX step is the main contributor
  Y₂O₃ / YOF spall                               coating wear, thermal cycling
  Mask fragments (ACL)                           facet erosion, stripping
  Pump back-streaming                            CN polymer in a cold foreline
```

### 9.3.2 How Many Matter

Chapter 4 set the budget for killer particles: a particle of 154 nm or more, on the patterned ACL, covers three openings. With a killer-defect density of 0.02 per cm² the yield loss is 0.6%. The chamber specification of 10 adders of 30 nm or more per wafer is much tighter than that:

```
Particle size distribution: cumulative ∝ D⁻²  (differential D⁻³)
  Fraction of adders ≥ 30 nm that are ≥ 154 nm:   (30/154)² = 3.8%
  Adders ≥ 154 nm per wafer at 10 adders ≥ 30 nm:  0.38
  Equivalent killer density (706.9 cm²):          5.4 × 10⁻⁴ per cm²   (40 times below the 0.02 budget)
```

At the 10-adder specification the chamber contributes about 0.4 killer particles per wafer and a yield loss of 0.016%. **Particles from the etch chamber are not the limiting source of killer clusters.** Resist and mask defects, which print or block openings before the etch, are (Chapter 12). The adder specification is kept for other reasons: particles under 154 nm still block single openings and trap residual oxide, and a tight specification is the only guard against flake events.

---

## 9.4 The Polymer in the Column

### 9.4.1 Why It Matters

After the etch, the column walls carry the polymer that deposited in the last steps: 1–2 nm on oxide and 2 nm on nitride. Book #30 (Section 4.5) shows what that does: a column whose walls are hydrophobic does not fill, the air in it dissolves slowly, and the oxide around its four pillars stays.

```
Wetting of a pore (50 nm wide): spontaneous filling requires cos θ > 0 on its walls.
  Polymer (CFₓ, aged)        θ ≈ 110°
  Clean oxide or nitride     θ ≈ 10° after the strip and a dilute-HF pre-wet
```

### 9.4.2 Coverage and Contact Angle

A wall that carries polymer over a fraction φ of its area, and bare surface over the rest, has an apparent angle given by the Cassie relation:

```
cos θ = φ cos θ_p + (1 − φ) cos θ_s,    θ_p = 110°, θ_s = 10°

φ       cos θ    θ
0       0.985    10°
0.10    0.852    32°
0.21    0.706    45°
0.35    0.520    59°
0.50    0.321    71°
0.61    0.175    80°
0.74    0.003    90°
1.00   −0.342    110°
```

Two thresholds follow. **The limit of spontaneous filling is 74%**: above it the pore does not fill at all. But a pore that fills does so slowly and traps gas unless the contact angle is well below 90°, and for reliable filling in a few seconds the target is θ below 60°, a coverage of **φ ≤ 0.365** (at φ = 0.61, θ = 80°, the pore fills only marginally).

---

## 9.5 The Strip and Its Reach

### 9.5.1 Polymer Removal Kinetics

An oxygen radical removes polymer by oxidation, and an ion-assisted flush removes it by oxidation and sputtering. Take first-order removal of the polymer coverage with time constants at the top of the column:

```
φ(t) = exp(−t/τ),   τ_rad = 12 s (radicals, 200 °C),   τ_ion = 3 s (ion-assisted, 100 eV O⁺/Ar⁺)
```

At the bottom of the column the rates are reduced by the dose that arrives there. For radicals it is the dose of Chapter 7 (12% at 770 nm for a wall loss probability s = 0.005, 1.5% for s = 0.02); for ions, the fraction that reaches the bottom: 35% at 100 eV (Chapter 7).

### 9.5.2 Coverage at the Middle Support

```
Polymer coverage φ and apparent contact angle at the middle support (770 nm):

Strip                                                    φ       θ
Radical only, 50 s, s = 0.005 (12% dose)                 0.60    79°      marginal
Radical only, 50 s, s = 0.02 (1.5% dose)                 0.94    105°     does not fill
10 s ion flush (100 eV) + 40 s radical, s = 0.005        0.21    45°      reliable
10 s ion flush + 40 s radical, s = 0.02                  0.30    54°      reliable
10 s ion flush alone                                     0.31    55°      reliable
15 s ion flush + 35 s radical, s = 0.005                 0.12    35°      margin

At the top of the column, radical only, 50 s:  φ = exp(−50/12) = 0.016  (clean)
```

The radical-only strip is, by this model, effective at the top and ineffective at the bottom. To bring φ at the bottom to 0.35 with radicals alone would take 102 s for s = 0.005 and 834 s for s = 0.02, which is not available in the cycle time of the chamber. **The ion flush is what makes the strip work**, because 35% of 100 eV ions reach the bottom, against 1.5–12% of the radicals.

### 9.5.3 The S1 Post-Etch Treatment

```
Post-etch treatment (inside the 174 s overhead; the 50 s "ACL strip"):
  Stage 1   10 s    O₂/Ar, bias 100 eV (ion-assisted flush); removes polymer to the bottom of the column
  Stage 2   40 s    O₂/N₂ downstream plasma, 200 °C; strips the remaining ACL (47 nm at the thinnest
                    point, up to about 100 nm elsewhere) and finishes the top of the column
  Then      5–10 s  dilute-HF pre-wet, or DI with surfactant, at the start of the dip (Book #30)
```

The 47 nm margin of Chapter 1 is the thinnest ACL left over the lattice, so the 40 s stage strips it with room to spare.

---

## 9.6 What the Strip Does to the Pillars

### 9.6.1 TiN Oxidation

Oxygen oxidizes the exposed TiN. Growth is logarithmic:

```
Oxide thickness on TiN (illustrative):  δ(t) = 0.5 + 0.35 ln(1 + t/10 s) nm at 150 °C;  × 1.4 at 250 °C
  50 s at 150 °C: 1.13 nm      50 s at 250 °C: 1.58 nm
Ion-assisted flush (crescent tops only; ions go straight down): additional ≈ 0.9 nm
```

The crescent tops therefore carry about 2.0 nm of TiO₂ after the S1 strip; the side surfaces of the pillars, which see only the radicals, carry about 1.1–1.6 nm. TiO₂ dissolves slowly in dilute HF, and the oxidized surface is the starting point for the dielectric of Book #33 and for the surface chemistry of Book #30, Chapter 13. The strip is a deliberate exchange: a 0.9 nm increase of the oxide on the crescent tops (the TiN crescents are 48% of the area of each opening) for a column that fills.

### 9.6.2 Fluorine

The polymer carries the fluorine to the surface. Removing the polymer removes most of it:

```
F on TiN (XPS), at the pillar top:
  After etch (before strip)    8–12 at%   (in the polymer and the TiFₓ skin)
  After radical-only strip     3–5 at%
  After ion flush + radical    1.5–3 at%  (specification ≤ 3 at%)
```

### 9.6.3 Queue Time

An etched and stripped wafer has an energetic, partly fluorinated surface and a hydrophilic oxide that adsorbs water. The queue before the dip is limited to 4 h in a nitrogen-purged FOUP; beyond that the contact angle on the column walls rises as hydrocarbons adsorb, and the pre-wet must be lengthened.

---

## 9.7 From Coverage to Failure Probability

Polymer coverage is not uniform. It varies from column to column and across the wafer with the polymer film, the ion flux, and the column depth. For a normal distribution of φ with σ = 0.08 about the mean, a column fails to fill when φ exceeds 0.61 (θ = 80°):

```
Mean φ at the middle support   z = (0.61 − μ)/0.08    P(column fails to fill)
0.15                           5.75                     4.5 × 10⁻⁹
0.21  (ion flush + radical)    5.00                     2.9 × 10⁻⁷
0.25                           4.50                     3.4 × 10⁻⁶
0.30                           3.88                     5.3 × 10⁻⁵
0.35                           3.25                     5.8 × 10⁻⁴
0.40                           2.62                     4.3 × 10⁻³
0.50  (radical only)           1.37                     8.5 × 10⁻²
```

Compare with Chapter 4: random opening failures of 10⁻⁴ are tolerable if independent. The mean coverage at which the column-fill failure reaches 10⁻⁴ is φ ≈ 0.31. A strip that brings the mean at the bottom to 0.21 gives a margin of 350 in failure probability. The radical-only strip, at 0.5 or 0.6, is orders of magnitude outside it. Coverage variations are correlated across the wafer (the polymer film is thicker at the edge, for example), so the failures cluster, and the real specification is on the wafer map of coverage rather than on its mean (Chapter 12).

---

## Summary and Key Takeaways

1. **The chamber makes 5 nm of polymer per wafer on its walls.** A waferless clean takes most of it; 0.05 nm per wafer accumulates, and 1500 RF-hours between wet cleans keeps it under a micrometre.

2. **The first wafer is different.** A cleaned chamber has thinner polymer: +9.4% SiN rate and +16% TiN rate. A 10 s seasoning removes it.

3. **Etch-chamber particles are not the killers.** At 10 adders of 30 nm or more per wafer, about 0.4 are 154 nm or larger: 5 × 10⁻⁴ per cm², 40 times under budget.

4. **The column needs wetting.** Polymer coverage above 0.365 gives contact angles above 60° and unreliable filling; above 0.74 the column does not fill.

5. **Radicals do not clean the bottom.** A 50 s radical strip leaves 60% coverage at the middle support (s = 0.005) or 94% (s = 0.02).

6. **An ion flush does.** 10 s at 100 eV brings the bottom to 0.21–0.30 coverage, and costs about 0.9 nm of extra oxide on the crescent tops.

7. **Failure probability is steep in coverage.** 3 × 10⁻⁷ at φ = 0.21, 5.8 × 10⁻⁴ at 0.35, 8.5 × 10⁻² at 0.5.

---

## Study Questions

1. Compute the angle for φ = 0.30 and the coverage at which θ = 45°. Explain why a flat witness wafer, which shows θ = 15° after the strip, can be misleading about the bottom of the column.

2. After a strip, a witness shows φ = 0.02 at the wafer top. What does the model give for φ at the middle support if the strip was radicals only (τ = 12 s) for 50 s with a dose of 12% at 770 nm? Is the witness evidence of a good column?

3. The ion flush is shortened to 6 s. Compute φ at the middle support (35% ion fraction, s = 0.005 radicals for 40 s) and the failure probability for σ = 0.08.

4. A wafer queues for 10 h and the apparent polymer coverage rises by 0.15 at the bottom. If the mean was 0.21, what is the new failure probability? What would you change in the pre-wet?

5. A chamber with a 1.0 µm limit on wall polymer deposits 0.07 nm per wafer net after the clean. How many wafers, and how many RF-hours at 9 wafers/h, is the wet-clean interval?

6. At 10 adders ≥ 30 nm per wafer and a D⁻³ distribution, how many adders of 100 nm or more are there per wafer? If each blocks one opening, how does that compare with the 4.25 × 10⁵ failed openings per die that the lattice tolerates at p = 10⁻⁴ (Chapter 4)?

---

**Next Chapter:** [Chapter 10: Opening Profile, CD & Pattern Fidelity](./10-opening-profile-cd-fidelity.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
