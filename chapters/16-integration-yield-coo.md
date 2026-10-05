# Chapter 16: Integration, Yield & Cost of Ownership

## Overview

The support layer etch is a small step in a long module. It touches 14% of the array area, runs for four minutes, and costs about seven dollars per wafer. Its place in the economics is set by what comes after it: a dip-out that depends on every opening, a dielectric that coats every surface the etch left, and a yield that is lost in clusters rather than cells. This chapter places the etch in the flow, lists what its customers need from it, collects the yield signatures from the earlier chapters, sizes the equipment for a fab starting 150,000 wafers a month, and compares the routes by cost of ownership and by the yield gain each would have to buy.

The conclusion is the same as the one Chapter 14 reached from the mechanics. For a two-support 1b-class array, **S1 is the route of choice**: it costs about $17.5 per wafer for the module, its yield loss is set by defects that exist before the etch, and S2 would have to gain 0.16% of die yield (S2A) or 0.6% (S2D) to pay for itself. S2 and S3 are routes taken when the one-pass mask runs out, not when the cost is lower.

**Learning Objectives:**
- List what the dip-out, the dielectric, and the plate need from the support layer etch
- Compile the yield signatures of S1 and the chapter in which each originates
- Size the etch, wet, and drying equipment for 150,000 wafer starts per month on each route
- Compute the cost of ownership per wafer for S0, S1, S2A, and S2D
- Compute the break-even yield gain of a more expensive route
- Apply a checklist to a new product

---

## 16.1 The Customers

```
What each downstream module needs from the support layer etch:

Customer                  Needs                                            Chapter
─────────────────────────────────────────────────────────────────────────────────────────────────────────
HF dip-out (Book #30)     openings that fill: polymer coverage φ ≤ 0.31      9
                          at the bottom; open area (free area ≥ 830 nm²      10
                          at the middle support); no whiskers                12
Drying (Book #30)         supports intact, with ligament margin ≥ 1.08;      4, 14
                          loss per wall ≤ 2 nm (S1)
ZAZ ALD (Book #33)        a TiN surface with F ≤ 3 at%, oxide ≤ 2.5 nm;      9, 11
                          free area to reach the lower pillar half
Top electrode, plate      the opening closes at the top electrode: no void   1
(Book #32)                under the plate; no seam slots deeper than 10 nm   11
Dielectric clear          nothing: the support layer etch is upstream        —
(Book #33)
Cell array test           capacitance 8.6 fF (± 0.1% from the etch);         11
                          leakage < 1 fA; class-linked weak cells ≤ 14       13
```

---

## 16.2 Queue Times and Hand-Offs

```
Hand-offs (S1; illustrative):
  Interval                                 Limit        Why
  ───────────────────────────────────────────────────────────────────────────────────────
  Support etch chamber → post-etch strip   in situ      polymer on the walls ages and bonds
  Strip → dip-out                          ≤ 4 h        hydrocarbon adsorption raises the contact
                                                        angle on the column walls (Ch. 9)
  Dip-out → ZAZ ALD                        Book #30     TiN surface, capillary condensation
  ACL deposition → support etch             ≤ 24 h       ACL ages; roughness unchanged, adhesion
  Top-support CMP → ACL deposition          ≤ 8 h        hydrated nitride skin (Ch. 2)
```

In S2 the sequence has one more hand-off, between the first dip and the second nitride step. The wafer is dry and its upper half free-standing; the queue before SN2 is limited by the fluorine and carbon that adsorb on the free pillars (4 h) and by the capillary condensation of water in the 17 nm gaps (Book #30, Chapter 16).

---

## 16.3 Yield Signatures

### 16.3.1 Per-Die Failure Modes (S1)

```
Support-layer-etch-related failures per 16 Gb die (S1; illustrative):
  Mode                                    Mechanism                          Per die           Class
  ──────────────────────────────────────────────────────────────────────────────────────────────────────
  Killer cluster, resist/mask defects     footprint ≥ 154 nm, 3+ openings    6.0 × 10⁻³         fatal
  Killer cluster, chamber particles       adders ≥ 154 nm                    1.6 × 10⁻⁴         fatal
  Killer cluster, polymer wetting         φ = 0.21 mean                      2 × 10⁻¹⁰          fatal
                                          φ = 0.35 (excursion)               1.7                fatal
  TiN top loss and seam weak cells        slot depth 8 nm, 7.6% of touched   14 cells           repairable
  F-delayed ZAZ weak cells                nucleation delay at the crescent   1–3 cells          repairable
  Junction stress (touched class)         0.14 C/cm² avalanche stress        not counted        retention tail
  Ligament cracking                       CD excursion; margin 1.08           design margin      cluster
```

### 16.3.2 Yield

```
Cluster yield:   Y = exp(−D_k · A_array) = exp(−0.02 × 0.298) = 99.4%    loss 0.6%
Value of 1% die yield:   900 gross dies × 90% × $8 = $6,500 per wafer;  1% = $65
Value of the cluster loss:   0.59% × $6,500 = $38.6 per wafer
```

The loss is almost entirely from defects that exist before the etch (resist and mask), 0.6%. The etch chamber, the wetting, and the weak cells add little if the controls of Chapters 9 and 15 work. The repairable cells (14 per die) are within the repair resource of a few thousand (Book #30, Chapter 16).

### 16.3.3 Reading a Signature

```
Symptom                                  Likely origin                       Check
─────────────────────────────────────────────────────────────────────────────────────────────
Fails on the 3:1 pattern (touched class)  TiN top, seam, junction stress     TiN witness, flash log, OX time (Ch. 11, 13)
Clusters of 10–50 cells at the wafer edge  polymer wetting at the edge        contact-angle map, strip uniformity (Ch. 9)
Clusters at random positions              particles, resist defects           darkfield map, pre-etch inspection (Ch. 15)
Low C_s on a whole zone                   middle-support CD low; residual     XTEM, OCD, SN2 fall width (Ch. 10, 12)
                                          nitride
Cracks along a row of openings            ligament; CD too large              top CD, trim, dip loss (Ch. 4, 14)
```

---

## 16.4 Equipment at 150,000 Wafer Starts per Month

150,000 starts a month is 1.8 million a year, 205 wafers per hour averaged over the calendar. Platforms run at 85% uptime.

### 16.4.1 Etch

```
Etch platforms (4-chamber CCP):
  Route    Plasma    Overhead    Per-chamber    Platform       Wafers per        Platforms
           time (s)  (s)         time (s)       wafers/h       platform-year     needed
  S0       195       174         369            39.0           290,600           6.2 → 7
  S1       226       174         400            36.0           268,100           6.7 → 7
  S2D      118       308         426            33.8           251,500           7.2 → 8
  S2A      183       308         491            29.3           218,500           8.2 → 9
```

Only S0 and S1 meet the 35 wafers/h limit of Chapter 1; S2D and S2A run at 33.8 and 29.3, which is why they need more platforms. The overhead of S2 is larger (308 s against 174 s) because the wafer visits the etch tool twice (SN1 and SN2), with a transfer, a pump-down, a stabilization and a waferless clean at each, and one post-SN1 treatment.

### 16.4.2 Wet and Drying

```
Wet platform (12-chamber, 120 wafers/h, 893,500 wafers per year):
  S0, S1:   1.8 M wafers → 2.0 platforms → 3    (the second would run at 101%)
  S2:       3.6 M passes → 4.0 platforms → 5

Supercritical CO₂ drying (40 wafers/h per tool, 297,800 per year):
  S0, S1:   6.0 tools → 7
  S2:       12.1 tools → 13
```

---

## 16.5 Cost of Ownership

### 16.5.1 The Etch

```
Etch cost per wafer (platform $6.0 M, 5 years, 85% uptime; illustrative):
                      S0      S1      S2D     S2A
  Depreciation        4.1     4.5     4.8     5.5
  Consumables         1.5     1.7     1.2     1.7
  Gases, power        0.8     0.9     0.5     0.8
  Flash gas           —       0.2     0.3     0.3
  Total               6.4     7.3     6.8     8.2
```

(Book #30's S0 figure of $6.4 is the reference. S1 costs $0.9 more than S0: 31 s of extra plasma and two flashes.)

### 16.5.2 The Module

```
Support open + dip-out + dry (per wafer; HF reclaim; supercritical CO₂ drying):
                                  S0      S1      S2D      S2A
  Etch                            6.4     7.3     6.8      8.2
  Dip-out and rinse/dry           6.0     6.0     10.5     10.5      (two passes: HF 1.5 + 2 × [1.8 + 1.5 + 1.2])
  Supercritical CO₂ drying        4.2     4.2     8.4      8.4       (one pass or two)
  SiCN support film premium       —       —       0.5      0.5
  Lithography premium             —       —       30       —         (EUV or double pattern, layout D)
  Total                           16.6    17.5    56.2     27.6
  Δ vs S1                         −0.9    —       +38.7    +10.1
```

### 16.5.3 The Yield Cost

```
Yield loss from killer clusters (D_k × A_array):
  S1, S2A (ArF-i)      D_k = 0.02/cm²    0.59%    $38.6 per wafer
  S2D (EUV)            D_k = 0.03/cm²    0.89%    $57.9 per wafer   (finer lattice, new tool)

Break-even yield gain over S1:
  S2A   $10.1 / $65 per % =  0.16% of die yield
  S2D   $38.7 / $65 per % =  0.60% of die yield
```

---

## 16.6 What a Better Route Would Have to Buy

S2's gains are in TiN loss (3.2 → 1.3–1.8 nm), junction stress (0.5 times the dose), mask (220 against 300 nm), and cluster tolerance. Their yield value:

```
Value of S2's gains in yield (illustrative):
  TiN and seam weak cells: 14 → 5 per die        repairable: no yield change
  Junction-stress retention tail                  not quantified; unlikely above 0.05%
  Cluster tolerance (vertical HF path)            helps only wetting clusters (2 × 10⁻¹⁰ per die at φ = 0.21): none
  Mask margin                                     no yield value while the mask closes
  Capacitance                                     −1% (S2 sidewall fluorination): negative
```

None of them is worth the 0.16% (S2A) or 0.6% (S2D) that the route would have to gain. For two supports at 1b, S2 is not an economic choice. It becomes the choice when the one-pass mask cannot close: a mold taller than about 2 µm, a third support, or an array whose TiN budget is smaller than 3 nm. At 1d, with three supports, S3 is the only route and its cost is the cost of the technology.

---

## 16.7 New-Product Checklist

```
For a new array, check in this order:
  1. Number of supports and the free span of each (≤ 800 nm at 1b; ≤ 700 nm at 1d).
     Spans over 800 nm or a third support → sequential (S2/S3).
  2. One-pass mask budget: ACL needed = Σ(film / selectivity) + facet allowance.
     If it exceeds 300 nm less 40 nm margin → sequential.
  3. Support film: HF loss per wall ≤ 2 nm (S1), ≤ 1.5 nm (S2); ligament margin ≥ 1.08 on the CD
     after the dip-out (Ch. 4, 14).
  4. Opening lattice: overlap ≤ 20 nm at 3σ; middle-support CD ≥ 40 nm (free area ≥ 830 nm²);
     for sequential routes check the cleared width (Ch. 10) and the pull-in voltage (Ch. 13);
     every pillar touched if V_pull < 10 V.
  5. TiN budget: ≤ 3.5 nm top loss; flash in every nitride step; transients × number of steps.
  6. Polymer at the bottom of the column: ion flush in the strip; φ ≤ 0.31 on a deep-hole test structure.
  7. Metrology: TiN witness pad, deep-hole array, lattice test block; darkfield on every lot.
  8. Class-aware bitmap analysis in the test flow.
```

---

## 16.8 Putting It Together

```
Support layer etch: what each chapter controls
  The film (Ch. 2)                     etch time, HF loss, mask
  The chemistry (Ch. 3)                polymer, selectivity, the transient, the flash
  The lattice (Ch. 4)                  openings, clusters, ligaments, killer defects
  The hardware (Ch. 5–7)               film thickness 0.1 nm; flash; levers; trims
  The signal (Ch. 8)                   endpoint, fault detection
  The clean (Ch. 9)                    wetting, trapped gas
  The profile (Ch. 10)                 CD, free area, S2 aperture image
  The pillars (Ch. 11, 13)             top loss, two classes, charging, pull-in
  The residue (Ch. 12)                 slivers, micromasks, stranded oxide
  The routes (Ch. 14, 16)              S1, S2, S3; cost; break-even
  The measurement (Ch. 15)             the ladder and the bitmap
```

---

## Summary and Key Takeaways

1. **The yield loss is set before the etch.** 0.6% from killer clusters at D_k = 0.02/cm², almost all from resist and mask defects.

2. **The module costs $17.5 per wafer in S1.** Etch $7.3, dip-out and dry $6.0, supercritical drying $4.2.

3. **S2 costs more.** +$10.1 (S2A) or +$38.7 (S2D, with EUV or double patterning) per wafer.

4. **The break-even gain is 0.16% (S2A) or 0.6% (S2D) of die yield.** None of S2's gains is worth that for a two-support 1b array.

5. **150,000 starts a month needs 7 S1 platforms, 8–9 for S2.** Three wet platforms and seven supercritical dryers for S1; five and thirteen for S2.

6. **The decision is made by the mask.** When the one-pass mask closes, use S1; when it cannot, use the sequential route that fits.

---

## Study Questions

1. A fab starts 100,000 wafers per month. How many S1 etch platforms, wet platforms, and supercritical dryers does it need?

2. The SiCN support film premium rises from $0.5 to $2.0 per wafer. What is the new S2A module cost and the break-even yield gain over S1?

3. D_k for S2D falls to 0.015/cm² with a mature EUV process. Recompute its yield loss and the break-even yield gain, including the yield difference with S1.

4. A new product has two supports, a free span of 900 nm, and an ACL budget of 300 nm. Using the checklist, which route does it need? What is the first design change you would ask for?

5. A bitmap shows 120 fails of which 108 on the touched sublattice (90%). Is this class-linked at 3σ? Which modules in the table of Section 16.3.3 does it point to?

6. The flash adds $0.2 per wafer and 8 s of plasma time. Compute its break-even in TiN weak cells per die, if each weak cell costs $0.002 in yield (a fraction of the repair resource).

---

**Back to:** [README](../README.md) · [INDEX](../INDEX.md)

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
