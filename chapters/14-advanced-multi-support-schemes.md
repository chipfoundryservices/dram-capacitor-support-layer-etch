# Chapter 14: Advanced Schemes — Sequential Opens, Three-Support Molds, HF-Resistant Supports, Pre-Opened Lattices, 4F² & 3D DRAM

## Overview

The one-pass route of S0 and S1 cuts the whole column in a single plasma. It is limited by the mask: 253 nm of a 300 nm carbon mask is spent on a column 920 nm deep, and a taller mold or a third support would exhaust it. The alternative of Book #30 (Section 14.2) is sequential: open the top support, let HF remove the upper oxide, dry the wafer, open the middle support through the top-support openings from above, and dip again. This chapter develops that route, S2, in full, and extends it to three supports (S3).

The earlier chapters have already laid the constraints on it. The dip that removes 650 nm of oxide *vertically* costs the nitride supports an amount set by the oxide-to-nitride selectivity of the HF (Chapter 2). The openings widen, and the ligament margin of Chapter 4 decides whether the lattice survives. The free pillars of the second nitride step charge unevenly and pull in (Chapter 13). The middle-support opening is an image of the aperture, 38 nm wide at 400 eV (Chapter 10). And the free upper half of every pillar is exposed to radicals that fluorinate and oxidize it, which costs capacitance. Each is quantified below. The result is that **S2 is feasible, but only with an HF-resistant support, a lattice that touches every pillar or a reduced ion flux, and an SN2 at 600 eV**, and that it pays for itself only where the one-pass route runs out of mask.

**Learning Objectives:**
- State the HF selectivity a sequential route requires and apply it to a given pair of films
- Compute the nitride loss per wall and the final opening CD after both dips, and the ligament margin
- Estimate the capacitance cost of sidewall fluorination of free-standing pillars
- Assemble the S2 reference (S2D with SiCN supports) and its fallback (S2A) with plasma time, TiN loss, and mask
- Describe S3 for a 1d-class array: spans, pull-in voltage, step sequence, openings per die
- Explain why a pre-opened middle support has not been adopted
- State what changes for 4F² and 3D DRAM, and choose a route for a given array

---

## 14.1 The Sequential Route in Full

```
S2 flow (reference):
  1. ACL open, 220 nm (SiCN supports) or 160 nm (SiN supports); mask retained to the end
  2. FL1 4 s + SN1 (top support open), landing in the upper oxide with a 25% overetch
  3. Post-etch treatment of the top columns (ion flush; shallow, AR 2.4)
  4. Dip 1: HF removes the upper oxide vertically through the openings, down to the middle support
  5. Rinse and dry (free span: 650 nm between the top and middle supports)
  6. FL2 4 s + SN2 (middle support) through the top-support openings, ions at 600 eV, 40% overetch
  7. Post-etch treatment: strip the ACL and the polymer on the free pillars (radicals only)
  8. Dip 2: HF removes the lower oxide
  9. Rinse and dry (all spans free)
```

What S2 saves: the 129 s OX step and the 29 s LAND step of S1, with their share of the TiN loss (2.25 of 3.2 nm) and of the mask (130 nm for OX and 20 nm for LAND, 59% of the 253 nm used). What it adds: a second dip and dry, a plasma step in a free forest, and the consequences below.

---

## 14.2 The HF Constraint

### 14.2.1 The Selectivity Criterion

In S1 the plasma has cut the oxide and the HF only has to move 27–47 nm laterally. In S2 the HF removes the whole 650 nm of upper oxide vertically, and every nanometre of oxide costs the exposed nitride faces a fraction 1/S_HF of a nanometre. With the path h = 635 nm (650 nm less the 15 nm of the SN1 overetch), a 40% overetch, and a loss budget Δ per face:

```
Loss per exposed face:   Δ = h (1 + OE) / S_HF
Required selectivity:    S_HF ≥ h (1 + OE) / Δ_budget = 635 × 1.4 / 3 nm = 296
```

```
Oxide-to-nitride selectivity of the HF (5 wt%, 25 °C):
  Upper oxide      Support        Rate ratio S_HF     Meets 296?
  PE-TEOS (70)     PECVD SiN (1.0)      70            no
  PE-TEOS (70)     SiCN (0.25)          280           marginal
  PSG (300)        PECVD SiN (1.0)      300           yes (just)
  PSG (300)        SiCN (0.25)          1200          yes
  PE-TEOS (70)     SiBN (0.15)          467           yes
```

PSG here is an upper oxide doped with phosphorus (6 wt%) that etches at 300 nm/min in the same 5% HF. Changing the upper oxide changes the mold of Books #29 and #31, and a mold that keeps the PE-TEOS needs the support to resist the HF instead. The criterion covers dip 1 only; dip 2 adds its own loss (Section 14.2.2).

### 14.2.2 Loss, Final CD, and the Ligament

The top support's opening wall is exposed throughout both dips, and the CD after both is what the ligament carries (Chapter 4, Section 4.6):

```
Top-support opening wall: total nitride lost per wall in dip 1 + dip 2 (dip 2: 105 s),
and final opening CD (etched 50 nm), with the ligament margin to a 3.5 GPa fracture strength:

  Upper oxide  Support   Dip 1     Loss/wall   Loss/wall   Total per   Final CD   Ligament
                         time      dip 1       dip 2       wall        (nm)       margin
  PSG          SiN       178 s     2.96 nm     1.75 nm     4.71 nm     59.4       0.99    fails
  PSG          SiCN      178 s     0.74        0.44        1.18        52.4       1.22
  PSG          SiBN      178 s     0.44        0.26        0.71        51.4       1.25
  PE-TEOS      SiN       762 s     12.7        1.75        14.5        78.9       0.36    fails badly
  PE-TEOS      SiCN      762 s     3.17        0.44        3.61        57.2       1.06    marginal
  PE-TEOS      SiBN      762 s     1.91        0.26        2.17        54.3       1.16
```

With ordinary PECVD nitride supports the S2 dips fail the lattice at nominal even in the best case (margin 0.99 with PSG). With SiCN they pass, with margins comparable to S1's 1.18. **S2 therefore requires an HF-resistant support film**, which is the same film that Chapter 2 showed costs a factor of 1.8 in nitride etch time and mask. The one-pass route could not afford that film and S2 can.

The same ligament margin gives S1 its own correction. In S1 the dip loses 1.75 nm per wall and the CD after the dip is 53.6 nm; the ligament analysis of Chapter 4, Section 4.6, is stated for the CD after the dip-out.

---

## 14.3 The Free Pillars: Fluorination and Polymer

### 14.3.1 What the Cavity Does to the Pillars

During SN2 the upper 650 nm of every pillar stands free. The radicals of the nitride step, fluorine and polymer precursors, enter through the 28% open area and are consumed on the pillar surfaces. With a sticking probability of 0.02 on TiN the penetration length in the 17 nm slits between pillars is

```
λ = √(D_K / k_w):   D_K = (34 nm/3) × 606 m/s = 6.9 × 10⁻⁶ m²/s;  k_w = (s v̄/4)(2/17 nm) = 3.6 × 10⁸ s⁻¹
λ = 139 nm
```

The radical dose on a pillar surface falls off exponentially with the distance from the opening plane, e^(−z/139 nm): 100% at the top, 1% at 650 nm. The fluorination and the polymer follow it:

```
Skin of TiFₓ on the free pillar sidewall (self-limiting at 1.5 nm), dose at the top Φ₀ saturation units:
  Φ₀     Mean skin over the 650 nm    Capacitance loss if half the skin dissolves in dip 2   if all of it
  1      0.25 nm                      0.42%                                                    0.83%
  3      0.53                         0.88%                                                    1.75%
  5      0.69                         1.13%                                                    2.26%
  10     0.89                         1.47%                                                    2.95%
```

The capacitance loss is the dissolved skin divided by the pillar radius (14 nm), integrated over the length of the free span, relative to the whole pillar (1410 nm). Φ₀ is the dose at the top of the pillar in units of the dose that saturates the skin; a nitride step of 30 s at full flux is taken as 3–5. For that dose the loss is about **1% of the cell capacitance on every pillar**. Compared with 0.10% on the touched pillars of S1 (Chapter 11), it is ten times larger and it affects all of them.

### 14.3.2 The Polymer and Its Strip

The polymer precursors of the nitride step deposit on the free pillar sidewalls with the same penetration length, so the polymer is concentrated where the strip's radicals also reach: the upper 300–400 nm. The post-etch strip (O₂/N₂ radicals, 200 °C) works on the same length scale and removes it where it lies; the wetting problem of Chapter 9 does not arise for the pillars, because the gaps between them are open to the liquid from above. The cost is oxidation:

```
TiN oxide after a 50 s radical strip at 200 °C:   about 1.4 nm, over the top ≈ 400 nm of each pillar (30% of its length)
```

This TiO₂ is in the capacitor: it dissolves slowly in dilute HF and it is the surface the ZAZ nucleates on. Its effect is of the order of the fluorination, a fraction of a percent, and is carried in the 1% budget above.

### 14.3.3 Reducing It

The levers are the ones of Chapter 6 in reverse: a smaller dose lowers the fluorination, a lower step time lowers both, and a polymer-lean chemistry deposits less. None reduces the 1% to the level of S1. **The sidewall cost of S2 is a structural cost of exposing a free pillar to a nitride plasma.**

---

## 14.4 Assembling S2

### 14.4.1 The Reference and the Fallback

Putting together the constraints of Chapters 10, 13, and 14:

```
S2 reference variants (1b array, illustrative):

                              S2D (reference)                S2A (fallback)
  Support film                SiCN (C 12 at%)                SiCN
  Upper oxide                 PSG (300 nm/min)               PSG
  Lattice                     layout D (every pillar         layout A (75% touched)
                              touched; EUV or double)        ArF-i single exposure
  ACL                         220 nm                         220 nm
  SN1                         76.7 s (incl. 4 s flash)       76.7 s
  SN2 (600 eV)                41.7 s (incl. 4 s flash)       106 s (16% ion flux)
  Plasma time                 118.4 s                        182.7 s
  ΔV between neighbours       ± 1.5 V                        4.1 V
  TiN top loss                1.8 nm                         1.3 nm
  ACL used                    163 nm (57 left of 220)        163 nm
  Dip 1 / dip 2               178 s / 105 s                  178 s / 105 s
  Nitride loss per wall       1.18 nm                        1.18 nm
  Final CD (ligament margin)  52.4 nm (1.22)                 52.4 nm (1.22)
  Middle-support opening      40.5 nm (at 600 eV)            40.5 nm
  Sidewall fluorination       ≈ 1% of C_s                    ≈ 1% of C_s
  Dries                       2                              2
```

The SiCN support makes the nitride steps 1.8 times longer, so S2D's plasma time of 118 s is about 52% of S1's 226 s; the reduced flux of S2A takes it to 183 s, which is nearly S1's. The TiN top loss is 1.8 nm for S2D, between S1's 3.2 nm and the 1.0 nm that the same route reaches with PECVD nitride at 400 eV. The 600 eV SN2 needed for the opening width (Chapter 10) shortens SN2 by 21% and raises its steady TiN rate by 34%.

### 14.4.2 What S2 Buys

```
Comparison with S1 (1b array, two supports):
                         S1               S2D (SiCN, PSG)
  Plasma time            226 s            118 s
  Mask (ACL)             300 nm           220 nm (163 used)
  TiN top loss           3.2 nm           1.8 nm
  Junction stress dose   5.7 × 10⁻¹³ C    3.0 × 10⁻¹³ C  (SN1 77 s + SN2 42 s at 2.5 fA)
  Cluster robustness     p ≤ 1 × 10⁻⁴     p ≥ 2 × 10⁻² (vertical HF path, Ch. 4)
  Sidewall fluorination  none             ≈ 1% of C_s
  Nitride loss/wall      1.75 nm          1.18 nm (SiCN)
  Dips and dries         1 and 1          2 and 2
  Lithography            ArF-i            EUV or double pattern (layout D)
  Mold                   as Book #30      upper oxide changed (PSG)
```

S2 gains on TiN, junction stress, mask, and cluster tolerance. It costs capacitance (1%), a changed mold, a second dip and dry, and a finer lattice. For a 1b-class array with two supports, **S1 remains the reference**: its costs are smaller than S2's, and its mask budget closes. Chapter 16 puts a cost on each line.

---

## 14.5 Three Supports at 1d-Class (S3)

### 14.5.1 The Mold

Book #31's 1d-class array has a 37 nm hexagonal pitch, pillars of 23 nm (gap 14 nm), a 2.10 µm mold, and 24 Gb of cells. With two supports the lower span is 1140 nm, too long. A third support restores the spans:

```
Three-support 1d-class mold (illustrative):
  Top SiN 100 | upper oxide 600 | mid-1 SiN 40 | oxide 600 | mid-2 SiN 40 | lower oxide 700 | stop 20  = 2100 nm
  Free spans after full removal:   600, 600, 700 nm
  Cells per die                    24 × 2³⁰ = 2.58 × 10¹⁰
  Opening lattice                  hexagonal, pitch 74 nm (2 × 37), cell 1176 nm² (6F², F = 14 nm)
  Opening cell                     (√3/2) × 74² = 4742 nm² = 4.03 cells
  Openings per layer per die       6.4 × 10⁹        three layers: 1.9 × 10¹⁰
  Centre-to-pillar-axis distance   37/√3 = 21.4 nm;  inscribed free diameter 2 × (21.4 − 11.5) = 19.7 nm
  Overlap into each pillar         for 40 nm openings: 20 + 11.5 − 21.4 = 10.1 nm
```

### 14.5.2 Why One-Pass Is Out and What S3 Is

A one-pass column through the whole 1900 nm of oxide and three supports at aspect ratio 50 and more would need a carbon mask of about 600 nm (oxide at Ox:ACL ≈ 5 plus the nitrides), a thickness at which the mask open itself is a high-aspect-ratio etch. The sequential route cuts each support in turn through the openings of the one above:

```
S3 sequence:  SN1 → dip 1 (upper oxide) → dry → SN2 (mid-1) → dip 2 (second oxide) → dry
              → SN3 (mid-2) → dip 3 (lower oxide) → dry

  Plasma:  SN1 64.6 s (400 eV), SN2 30.9 s, SN3 30.9 s (600 eV; SiCN, 40 nm supports; 4 s flash each) = 126 s
  Dips:    PSG 600 nm × 1.4 / 300 = 168 s (×2); BPSG lower 700 nm × 1.4 / 600 = 98 s
  Dries:   3
```

### 14.5.3 Pull-In at 1d

The pillars are thinner (23 nm against 28 nm), the gap narrower (14 nm), and the free spans 600 nm. Applying the pull-in formula of Chapter 13:

```
Pull-in voltage (V_pull, free span L, pillar d = 23 nm, gap 14 nm):
  Boundary condition     L = 600 nm    L = 700 nm        (1b reference: 650 nm, d = 28 nm, g = 17 nm)
  Fixed–fixed            8.1 V         5.9 V             12.3 V
  Intermediate           4.7 V         3.4 V             7.1 V
  Pinned–pinned          3.6 V         2.6 V             5.5 V
```

At 1d the pull-in limit is 4.7 V for the intermediate boundary. A ΔV of 4 V, tolerable at 1b, is at the limit. The flux that gives V_eq < 2 V is 8% of the nominal, which would stretch the SN2 and SN3 steps 3-fold. **S3 therefore requires an all-touched lattice** (layout D or its 1d-class equivalent), or an ion-free nitride step. The lattice with every pillar touched is a necessity for the taller arrays, not an option.

---

## 14.6 The Pre-Opened Lattice (P)

The most direct way to avoid etching the middle support in a column of oxide next to TiN is to etch it before the oxide above it and the pillars exist: pattern and open the middle support when it is a bare film on the lower oxide, deposit the upper oxide over it (filling the openings), and then etch the capacitor holes through the stack.

```
P flow (middle support pre-opened):
  Mold to the lower oxide → deposit mid-1 SiN → pattern and etch openings in it (AR ~1, no TiN, no oxide column)
  → deposit upper oxide (fills the openings) → top SiN → holes → TiN fill → CMP
  → SN1 (top support only) → dip (one dip: oxide plugs in the middle-support openings dissolve) → dry
```

The attractions are large: the TiN never sees the middle-support etch; there is no OX, SN2, or LAND; there is one dip and one dry; and the plasma is only SN1 (0.6 nm of TiN loss, ACL 150 nm). Its flaw is in the hole etch. Each capacitor hole near an opening passes through the middle support where one side of it is nitride and the other is the oxide plug:

```
Fraction of the hole cross-section in the oxide plug at the middle support:   15/32 = 47% for the three holes of each opening
Rate ratio, oxide to nitride in the hole-etch chemistry                        ≈ 6 (Book #30, Table 3.2.3)
A 50 nm band in which one side of the hole etches six times more slowly than the other:
   expected lateral drift of the hole bottom                                    ≈ 3–6 nm
Placement budget for the hole (Book #31)                                        ≈ 7.3 nm
```

An estimated 3–6 nm drift consumes most of the whole placement budget for every hole of every opening, for the sake of a saving the dip-out can make in other ways. P has not been adopted and remains a laboratory scheme. It is worth stating because it names the underlying trade of the whole book: the cost of cutting the support next to the pillars is the price of having the pillars present.

---

## 14.7 4F² and 3D DRAM

### 14.7.1 4F² Vertical-Channel DRAM

At 4F² the cell area falls to 784 nm² (F = 14 nm), and Book #30 (Section 14.4) shows that the pillars are about six times more flexible, with spans cut to about 460 nm by three middle supports in a 2.1 µm mold. The support layer etch is S3 with a fourth support: four nitride cuts in sequence, each through the openings of the ones above, in a lattice that must touch every pillar. The statistics of Chapter 4 carry over: the sequential route is robust to clusters (the HF path is vertical), the lattice must have no untouched pillars (Chapter 13), and each added support multiplies the plasma steps, the dips, and the dries.

### 14.7.2 3D DRAM

In a stacked-tier 3D DRAM the capacitors are horizontal and the supports are replaced by the dielectric tiers that bond them. What survives of the support layer etch is the **slit etch** that opens the stack for the lateral release of the sacrificial tier and the nitride-selective lateral etch itself. The radical, ALE, and wet tools of Chapter 7 return in a setting where their reach is not limited by a vertical column: a lateral cavity several tiers thick lets a radical travel its full penetration length. The ligament of a stacked tier is a plate, not a perforated lattice; the corresponding stress analysis uses the tier thickness and the slit pitch.

---

## 14.8 Choosing a Route

```
Route choice (illustrative):
  Array                              Supports   Route          Reason
  1b-class 6F², 1.6 µm               2          S1             mask closes (47 nm margin), smallest cost
  1b-class, mask or TiN-limited      2          S2D (SiCN)     mask 220 nm, TiN 1.7 nm; needs EUV/double lattice
  1b-class, ArF-i only               2          S2A (SiCN)     as S2D, 210 s plasma, ΔV 4 V
  1c/1d-class, 2.1 µm                3          S3 (layout D)  one-pass mask impossible; all-touched lattice required
  4F² vertical-channel               4+         S3-extended    spans of 460 nm; every pillar touched
  3D DRAM                            n/a        slit etch + lateral release  Ch. 7 tools apply in lateral cavities
```

---

## Summary and Key Takeaways

1. **Sequential removal needs an HF selectivity of about 300.** A 635 nm vertical path with a 40% overetch and a 3 nm budget gives S_HF ≥ 296; PE-TEOS with PECVD nitride gives 70.

2. **Ordinary nitride fails the lattice in S2.** With a PSG upper oxide it loses 4.7 nm per wall and the ligament margin is 0.99; with SiCN it loses 1.2 nm and the margin is 1.22.

3. **A free pillar pays 1% of its capacitance.** Fluorine and polymer penetrate 139 nm into the forest; the skin of 0.5–0.7 nm averaged over the span, half of it dissolved in dip 2, is about 1%.

4. **S2D with SiCN is 118 s of plasma and 1.8 nm of TiN.** S2A (ArF-i, reduced flux) is 183 s and 1.3 nm.

5. **S1 remains the 1b reference.** S2 gains on TiN, mask, and cluster tolerance; it loses 1% capacitance, a changed mold, a second dip and dry, and a finer lattice.

6. **S3 is the route for 1d.** Spans of 600–700 nm have pull-in voltages of 2.6–8.1 V; every pillar must be touched.

7. **The pre-opened lattice trades the support etch for hole-etch drift.** 3–6 nm of an expected 7.3 nm placement budget.

---

## Study Questions

1. Compute S_HF required for a 3 nm budget with a 635 nm path and 60% overetch. Which pairs in the table of Section 14.2.1 meet it?

2. For a PSG upper oxide at 400 nm/min and PECVD nitride at 1.0 nm/min, compute the dip 1 time, the loss per wall in both dips, the final CD, and the ligament margin (use K = 4.8, strength 3.5 GPa).

3. Using the SiCN support: SN1 in S2D takes 76.7 s with the 4 s flash. Verify it from the rates of Chapter 3 and the SiCN plasma rate of 0.55. How much ACL does SN1 consume, using the convention of Book #30 (nitride cleared with overetch, divided by the selectivity of 3 and by the film's relative rate)?

4. A dose of Φ₀ = 4 on the free pillars gives a mean skin of 0.6 nm. If 70% of the skin dissolves in dip 2, find the capacitance loss for a 600 nm free span in a 1410 nm pillar of radius 14 nm.

5. At 1d the gap is 14 nm, the pillar 23 nm, and the span 600 nm. Find the pressure at ΔV = 3 V, and the intermediate-boundary deflection from the table of pull-in voltages (take δ = (g/3)(V/V_pull)² as a first approximation). Is the deflection below an eighth of the gap?

6. A vendor proposes P for a 1b-class array. List the three claims it makes, and the one number that you would ask for first, and why.

---

**Next Chapter:** [Chapter 15: Metrology, Inspection & Advanced Process Control](./15-metrology-inspection-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
