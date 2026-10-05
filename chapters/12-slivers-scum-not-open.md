# Chapter 12: Slivers, Scum & Not-Open Openings — Residue Statistics

## Overview

An etch is not finished when the average nitride has cleared. It is finished when the last place that must be clear is clear. In the support layer etch there are three kinds of last place: the corner where the opening wall meets a TiN crescent, the floor of the opening under any film or particle that blocks it, and the wall of the column, where polymer decides whether liquid will enter. This chapter treats the first two. Chapter 9 treated the third.

The result is a division the earlier chapters anticipate. **Slivers are common, small, and mostly harmless.** Every corner of every opening has a fin of unetched nitride whose width the overetch controls and the HF finishes. **Not-open events are rare, large, and fatal in clusters.** They do not come from the Gaussian tail of the clearing time, which is 20 standard deviations away, but from micromasks that cover the floor: particles, polymer blobs, resist defects. The statistics of the first are the statistics of a tail; those of the second are Poisson statistics of defects.

**Learning Objectives:**
- Describe the geometry of the sliver at the crescent corner and the model of rate reduction near TiN
- Compute the sliver width and fin height versus overetch
- Compute the sliver probability per corner and per die from the spread of local overetch
- Choose the overetch from the trade among sliver, time, mask, and landing
- Explain why the Gaussian tail does not produce not-open events
- Build the stranded-oxide budget from its sources and compare it with the yield model of Chapter 4

---

## 12.1 Three Kinds of Residue

```
Residue                      Where                          What it does
─────────────────────────────────────────────────────────────────────────────────────────────
Sliver (fin)                 nitride at the TiN interface   narrows the lobe a few nm²; thinned
                             at each crescent corner        by HF to a whisker
Scum / micromask             on the floor of the opening    blocks the opening if it covers
                             (polymer, particle, B/P film)  the floor: a not-open event
Polymer on the wall          column wall                    wetting, trapped gas (Ch. 9)
```

The interface layers of Chapter 2 (3 nm of oxynitride with boron and phosphorus at the base of the middle support) are not a permanent residue: SiON dissolves in the HF at several nanometres per minute, and boron and phosphorus leave with the BPSG. Residual nitride, which HF removes at 1 nm/min, is what stays.

---

## 12.2 The Corner

### 12.2.1 Geometry

At the middle support the opening is a circle of radius R = 22 nm and each crescent is cut by a pillar of radius r = 15 nm whose axis is d = 26 nm from the opening centre. The circle and the pillar surface meet at two points per crescent. The angle between the radii at an intersection point is

```
cos α = (R² + r² − d²) / (2 R r) = (484 + 225 − 676) / (660) = 0.050   →   α = 87.1°
```

The nitride lies outside both the circle and the pillar. Its wedge at the intersection has an angle of 180° − 87.1° = **92.9°**. The corner is nearly square. It is not acute, and the geometry does not trap products. What sets the sliver is the interface itself: a line along which nitride meets TiN, six of them per opening at each support.

### 12.2.2 Why the Rate Falls Near the TiN

Three effects slow the nitride etch near a TiN wall:

1. **Polymer supply.** TiN consumes none of the polymer that arrives (Chapter 3), so the film on its wall is thick; it feeds polymer to the adjacent nitride surface along the wall.
2. **Fluorine sink.** TiN takes up fluorine as a TiFₓ skin, depleting the radical density within a few nanometres.
3. **Ion deflection.** The pillar is a conductor at a floating potential, and ions passing it are bent by its field (Chapter 13).

A simple form, with the rate relative to the bulk as a function of the distance x from the TiN:

```
f(x) = 1 − (1 − f₀) exp(−x/ℓ),     f₀ = 0.5 at the interface,   ℓ = 4 nm
```

A site at x clears when the overetch has made up the lag: f(x) ≥ 1/(1 + OE). The sliver is the region where f falls short:

```
Sliver width x_s:  f(x_s) = 1/(1 + OE)   →   x_s = ℓ ln[(1 − f₀) / (1 − 1/(1 + OE))]
Fin height at the interface (film thickness T):  h(0) = T [1 − (1 + OE) f₀]
```

---

## 12.3 Sliver Width versus Overetch

```
Sliver width at the interface (f₀ = 0.5, ℓ = 4 nm):
  OE (SN2)    Width x_s     Fin height at x = 0 (T = 50 nm)
  20%         4.4 nm        20 nm
  25%         3.7 nm        19 nm
  30%         3.1 nm        17.5 nm
  40%         2.2 nm        15 nm    ← S0/S1 reference
  60%         1.2 nm        10 nm
  100%        0             0

Sliver width at the top support (SN1, T = 120 nm, OE 25%):    x_s = 3.7 nm, fin height 45 nm
```

The sliver width depends strongly on f₀:

```
Interface rate ratio f₀    0.3     0.4     0.5     0.6     0.7
Width at OE 40%            3.6 nm  3.0 nm  2.2 nm  1.3 nm  0.2 nm
```

Anything that makes the TiN wall richer in polymer or poorer in fluorine, such as a thicker flash film, a cooler wafer, or a lower O₂ flow, lowers f₀ and widens the sliver. The levers of Chapter 6 that did not matter for TiN loss are not free here.

### 12.3.1 Statistics

The local overetch is not the nominal 40%. The clearing time spreads by 1.93% (1σ, from the 5.8% 3σ of Chapter 2) and f₀ by 0.04 (1σ):

```
Sliver statistics per corner (Monte Carlo, 2 × 10⁶ corners, ℓ = 4 nm):
  OE      Mean width    P(width ≥ 2 nm)    P(width ≥ 3 nm)    99.9th percentile
  25%     3.66 nm       99.98%             93%                5.1 nm
  30%     3.09          99.5%              59%                4.3
  40%     2.23          74%                1.7%               3.3     ← reference
  60%     1.14          0.4%               0.0%               2.1
```

At 40% overetch, 1.7% of corners have a sliver of 3 nm or wider, and 74% have one of 2 nm or wider. With six corners per opening and 4.25 × 10⁹ openings, a sliver of 3 nm is a certainty on every die: about 4 × 10⁸ of them. The specification of Chapter 1 therefore reads **the 99.9th percentile of sliver width, not the maximum**: at 3.3 nm it meets the 4 nm limit.

### 12.3.2 What a Sliver Does

```
Area of a sliver (a wedge of 93° apex angle, width w):   A ≈ w² / (2 tan 46.5°) = 0.48 w²
  w = 2.2 nm:   2.3 nm² each,   6 per opening: 14 nm²    (1.5% of the free area of 938 nm²)
  w = 3.0 nm:   4.3 nm² each,  26 nm² per opening        (2.7%)
  w = 3.7 nm:   6.5 nm² each,  39 nm² per opening        (4.2%)
```

A sliver is a few percent of the free area and does not block. In the HF it is attacked on its free faces at 1.0 nm/min:

```
HF in the dip (105 s):  1.75 nm from each free face
  A 2.2 nm sliver at the middle support (one free face): remains ≈ 0.5 nm wide (a whisker)
  A 3.7 nm fin at the top support:                       remains ≈ 2 nm wide, 45 nm tall
```

The whiskers are a source of particles. A whisker 0.5 nm wide and 15 nm tall breaks under the force of the flowing liquid and becomes a nitride flake in the bath. The count is of the order of the sliver count, and the flakes are far smaller than 154 nm and affect the dip-out only by contributing to the particle budget of Chapter 9.

---

## 12.4 Choosing the Overetch

```
Overetch trade (SN2 at 159 nm/min, as in S2, where SN2 carries its own overetch; illustrative):
  OE     SN2 total   Δ time vs 40%   Sliver w   99.9th     Extra ACL    Extra BPSG   Extra TiN
         (s)                                    percentile (nm)         (nm)         (nm)
  25%    23.6        −2.8            3.7 nm     5.1 nm     —            —            —       fails the 4 nm limit
  30%    24.5        −1.9            3.1        4.3        —            —            —       marginal
  40%    26.4        0               2.2        3.3        0            0            0       reference
  60%    30.2        +3.8            1.2        2.1        3.3          7            0.05
  100%   37.7        +11.3           0          —          10           20           0.15
```

The reference is the point at which the 99.9th percentile just meets the 4 nm limit with a margin of 0.7 nm. Further overetch is paid in mask (nitride-equivalent / 3), in BPSG (the SN2 chemistry etches it at 158/1.5 = 105 nm/min, 1.76 nm/s) and in TiN (0.77 nm/min), and each buys less. In S0 and S1 the extra time is carried by LAND (Chapter 3); the table refers to S2.

---

## 12.5 Not-Open Events

### 12.5.1 The Gaussian Tail Is Not the Cause

An opening fails to open when nitride covers the whole floor. For the bulk nitride at the centre to survive, the clearing time of that site would have to exceed the overetch time:

```
Required:  t_site > 1.4 × t_nominal.     Spread of t_site: 1.93% (1σ)
z = (1.4 − 1)/0.0193 = 20.7    →    probability  ≈ 10⁻⁹⁴
```

No Gaussian distribution of rate or thickness produces not-open events. Those that occur are due to **micromasks**: something on the floor that stops the ions and radicals before the nitride is cut.

### 12.5.2 Micromasks

```
Source                     Mechanism                                   Size needed
──────────────────────────────────────────────────────────────────────────────────────────
Particle in the column     blocks the column or covers the floor       ≥ 40 nm in a 50 nm column
Polymer plug               flake or blob of CNₓFᵧ in the column        floor-sized
Resist/mask defect         the hole is not printed or not opened        (the opening is missing)
Thick residue on the       B/P-rich or carbon-rich layer at the          a few nm; usually etched through
  middle support           interface; incomplete SN2 start
SN2 stall                  polymer too thick (d₀ > 5 nm): nitride rate   all openings on a region
                           falls below the oxide rate (Ch. 3 table)
```

The first and the third are Poisson in density; the second is a flake event (Chapter 9); the last is a process excursion that affects a region and is detected by the endpoint's missing fall (Chapter 8).

### 12.5.3 Particle Arithmetic

```
Adders ≥ 30 nm per wafer         10
Adders ≥ 40 nm (cumulative D⁻²)  10 × (30/40)² = 5.6 per wafer
Fraction landing in openings     array coverage 38.5% × opening fraction 28% = 10.8%
Openings blocked per wafer       0.6
Openings tolerated at p = 10⁻⁴   10⁻⁴ × 3.8 × 10¹² per wafer = 3.8 × 10⁸
```

Particles landing in single openings are negligible. What kills is the large particle or the resist defect that blocks a cluster.

---

## 12.6 The Stranded-Oxide Budget

Combining the sources that produce clusters of at least three adjacent failed openings (Chapter 4) with the polymer-wetting clusters of Chapter 9:

```
Killer clusters per die (S1, 105 s dip; die array 0.298 cm²; illustrative):
  Source                              Density or probability                  Clusters per die
  Resist / mask defects               D_k = 0.02 per cm² (Ch. 4)              6.0 × 10⁻³
  Chamber particles ≥ 154 nm          5.4 × 10⁻⁴ per cm² (Ch. 9)              1.6 × 10⁻⁴
  Polymer wetting, mean φ = 0.21      p = 2.9 × 10⁻⁷ per opening              2 × 4.25×10⁹ × p³ = 2 × 10⁻¹⁰
  Polymer wetting, mean φ = 0.30      p = 5.3 × 10⁻⁵                          1.3 × 10⁻³
  Polymer wetting, mean φ = 0.35      p = 5.8 × 10⁻⁴                          1.7
  Total at φ = 0.21                                                           ≈ 6.2 × 10⁻³
```

With the design target of 0.01 clusters per die, the budget is spent almost entirely by **defects that exist before the etch** (the resist and mask), with a tenth of a percent from the chamber and none from wetting, provided the mean polymer coverage stays below 0.30. At φ = 0.35, the wetting term is 1.7 clusters per die, a hundred times the budget, and no other term matters. The dependence is very steep: the wafer map of polymer coverage (Chapter 9) is the control chart that matters, not the mean.

```
Yield:   Y = exp(−0.0062) = 99.4%       loss 0.6%     (matches D_k × A_array in Ch. 4)
```

---

## 12.7 Residue at the Top Support

The top support has the same interface, with OE 25% and T = 120 nm. Its fin is 45 nm tall and 3.7 nm wide at the pillar, in 93% of the corners at 3 nm or wider. After the HF the fin is 2 nm wide and still 45 nm tall. It narrows the top-support opening's free area by about 4% and does not block. It is a reason to run a longer SN1 overetch in S2, where the oxide loss is harmless, than in S0 and S1, where it deepens the column before OX. A longer OE in SN1 costs oxide at 148 nm/min: 8 s more costs 20 nm.

---

## Summary and Key Takeaways

1. **The corner is square.** 87.1° between the radii, a 92.9° nitride wedge; the interface, not the angle, causes the sliver.

2. **The sliver is a fin.** Width 2.2 nm and height 15 nm at the middle support at OE 40%; width 3.7 nm and height 45 nm at the top support at OE 25%.

3. **The width depends on the overetch and on f₀.** From 4.4 nm at 20% to zero at 100%; from 3.6 nm at f₀ = 0.3 to 0.2 nm at 0.7 for OE 40%.

4. **At the reference, 1.7% of corners carry 3 nm or more.** The specification reads the 99.9th percentile: 3.3 nm against 4 nm.

5. **A sliver is 1.5–4% of the free area and does not block.** The HF leaves a whisker; whiskers are a particle source.

6. **Not-open events are micromasks, not tails.** The Gaussian tail is 20.7σ away; the cause is a particle, a polymer plug, or a resist defect.

7. **The stranded-oxide budget is spent before the etch.** 6.0 × 10⁻³ of 6.2 × 10⁻³ clusters per die come from resist and mask defects; a polymer-wetting excursion to φ = 0.35 would give 1.7 per die.

---

## Study Questions

1. Compute the sliver width at OE 35% for f₀ = 0.5 and ℓ = 4 nm, and the fin height at x = 0 for T = 50 nm.

2. A recipe change lowers f₀ from 0.5 to 0.4 at OE 40%. Using the table, by how much do the sliver width and its area (A ≈ 0.48 w²) change?

3. The local clearing time spread is 3% (1σ) instead of 1.93%. With OE nominal 40%, how does the fraction of corners with a sliver ≥ 3 nm change? (Hint: the local OE_eff = (1 + OE)/(1 + e) − 1.)

4. Estimate the number of 3 nm slivers per die at OE 40% (six corners per opening, 4.25 × 10⁹ openings, probability 1.7%). Does it matter for the dip-out? Why does the specification use a percentile?

5. A wetting excursion puts the mean polymer coverage at 0.33 on an edge zone of the wafer. Estimate p (σ = 0.08, failure at φ > 0.61) and the killer clusters per die in the zone with Chapter 4's formula.

6. At what number of openings per die would a Poisson-distributed single-opening failure of probability 5 × 10⁻⁷ produce a triangle cluster rate of 0.01 per die? (Use 2 N p³.)

---

**Next Chapter:** [Chapter 13: Charging, Electrostatics & Free-Standing Pillars in the Plasma](./13-charging-electrostatics-free-pillars.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
