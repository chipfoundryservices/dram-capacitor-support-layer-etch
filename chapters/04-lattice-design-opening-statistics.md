# Chapter 4: Lattice Design, Pattern Transfer & Opening Statistics

## Overview

Four billion openings per layer is too many to inspect and too many to repair. The lattice that holds them has to work by design: it must tolerate random failures without anyone seeing them, and its design rules must make clustered failures the only thing worth worrying about. This chapter treats the lattice as a design object. It lists the choices, the constraints each one meets, and the lithography that prints them. It then derives the central statistical result of the book: **the lattice forgives single failed openings, pairs, and short rows, and forgives clusters of three only if the dip is long enough**. How long, and at what cost, is a design decision.

The chapter ends with the other side of the design window. Openings that are too large crack the ligaments between them. The upper limit on opening width is set by fracture, the lower limit by access, and the etch controls both.

**Learning Objectives:**
- List the parameters of an opening lattice and the constraints that bound each
- Compare five lattice designs on open fraction, TiN exposure, pillars touched, solid fraction, and free area
- Compute the overlap depth at 3σ from CD and overlay budgets
- Derive the reach of the HF dip and the critical cluster size of failed openings
- Compute the failure probability per opening that a given dip time tolerates
- Explain why correlated failures, not random ones, set the real specification
- Estimate the ligament stress and the CD at which fracture margin vanishes

---

## 4.1 The Lattice as a Design Object

### 4.1.1 Parameters and Constraints

```
Lattice parameters:            Bounded by:
  pitch P                       HF reach (Section 4.4); lithography; fracture
  opening size D                free area at the middle support (≥ 830 nm², D ≥ 40 nm);
                                ligament stress; TiN exposure
  placement on the pillar       overlap depth into pillars; overlay
    lattice
  shape                         pattern fidelity; stiffness along the shape
  number of layers opened       top and middle together; same pattern

Derived quantities:
  open fraction                 π D² / (4 · (√3/2) P²)
  solid fraction after open     1 − (holes) / cell, with the pillar overlap
  overlap depth                 D/2 + r_pillar − (centre-to-axis distance)
  openings per die              cells per die / (cell area of the lattice / 1734 nm²)
```

### 4.1.2 The Placement Rule

Placing an opening on an interstitial site (the centroid of three pillars) puts it 26 nm from each of three pillar axes. A 50 nm opening reaches 25 nm from its centre, a 32 nm pillar 16 nm from its axis, so each overlaps by 25 + 16 − 26 = 15 nm. Moving the opening onto a pillar would expose a whole pillar top to the plasma; moving it away from the interstitial toward a gap between two pillars would trade the crescent of one pillar for another. The interstitial site minimizes the TiN area exposed per unit opening area. Every layout in this chapter uses it.

---

## 4.2 Design Options

### 4.2.1 Five Layouts

The layouts below keep the opening on interstitial sites and vary the pitch, the size, and the orientation of the superlattice. Quantities are computed from the geometry of Chapter 1.

```
Layout (top support, pillars 32 nm, centre-to-axis 26 nm):
                   A (ref)    B          C           D           E
  Pitch P (nm)     90         90         77.9 (√3a)  77.9 (√3a)  135 (3a)
  Orientation      2a         2a         rotated 30° rotated 30° 3a
  Opening D (nm)   50         56         44          50          64
  Open fraction    28.0%      35.1%      28.9%       37.3%       20.4%
  Cells / opening  4.05       4.05       3.03        3.03        9.10
  Openings / die   4.25e9     4.25e9     5.66e9      5.66e9      1.89e9
  Overlap depth    15 nm      18 nm      12 nm       15 nm       22 nm
  Pillars touched  75%        75%        100%        100%        33%
  Solid fraction   39.2%      36.3%      37.6%       34.4%       43.7%
  Farthest oxide
    from edge      27 nm      24 nm      23 nm       20 nm       46 nm
  Lithography      ArF-i      ArF-i      EUV or      EUV or      ArF-i
                   single     single     double      double      single
```

### 4.2.2 Reading the Table

**A is the reference** and a compromise. At 90 nm hexagonal pitch it is close to the limit of single-exposure ArF immersion for hole arrays. It exposes 25% fewer pillars to plasma than a lattice that touched them all, and its 28% open fraction leaves 39% of the sheet as solid nitride.

**B (larger openings, same pitch)** adds only 97 nm² of free area at the top support (1110 against 1013 nm²), cuts the solid fraction by 3 points, and raises the overlap depth by 3 nm. It exposes more TiN and weakens the lattice for a small gain in access.

**C (a rotated, finer lattice)** is different in kind. Every pillar is touched exactly once, so there are no untouched cells and no two-class pattern (Chapter 11). There are 33% more openings, so the lattice is more redundant (Section 4.4). Its cost is lithographic: a 78 nm hexagonal pitch of 44 nm holes is below the single-exposure limit and needs EUV or a double pattern, with the overlay penalty that follows. The smaller opening (44 nm at the top, about 38 nm at the middle support, free area 778 nm²) fails the 40 nm specification of Chapter 1.

**D** repairs C's free area at the cost of a 34% solid fraction and 37% open area.

**E (a coarse lattice)** touches only a third of the pillars and halves the openings per die, which eases lithography and the etch count. The farthest oxide is 46 nm from an opening edge, so the dip must run 70% longer to clear the same oxide, and the overlap depth of 22 nm exceeds the 20 nm limit.

No layout wins on every line. A holds all the lines in the specification at once, which is why it is the reference.

---

## 4.3 Lithography, Mask & Placement

### 4.3.1 The Mask Stack

```
Support-open mask (reference, Book #30):
  ACL (amorphous carbon)    300 nm
  SiON cap                  25 nm
  BARC + resist             ArF-i, single exposure
  Resist CD                 ≈ 52 nm; SiON open (CF₄/CHF₃), ACL open (O₂/COS or N₂/H₂)
  ACL CD after open         50 nm (target) ± 2.5 nm (3σ)
```

The ACL is deposited on the planarized pillar array, so the pattern is printed on a topography-free surface. The ACL open is a carbon etch, and its CD bias and sidewall angle set the shape that the nitride etch inherits (Chapter 10).

### 4.3.2 Placement Error and the Crescent

The opening is placed against the pillar lattice, which was itself formed by a double-patterned honeycomb. The overlap depth into the nearest pillar changes with overlay δ and CD error:

```
Overlap depth into the nearest pillar:  15 + δ + ΔCD/2   (nm)

  Overlay (mean + 3σ)          ± 5 nm
  CD (3σ)                      ± 2.5 nm   → radius ± 1.25 nm
  Combined (root sum of squares) √(5² + 1.25²) = 5.15 nm
  Overlap depth at 3σ          15 + 5.15 = 20.2 nm      (specification: ≤ 20 nm)
```

At 3σ the reference sits on its limit. Every nanometre of overlap depth is crescent area exposed to the plasma and nitride removed from one side of the pillar's support collar, so the margin on this line is the margin on both the TiN budget (Chapter 11) and the collar (Chapter 14).

---

## 4.4 Redundancy and Reach: Opening Statistics

### 4.4.1 How HF Gets Through a Missing Opening

The dip-out of Book #30 etches the upper oxide laterally from each column wall. A column that is missing, because its SN1 opening failed, leaves oxide that the neighbouring columns must reach.

```
Lateral reach of the HF dip (Book #30 numbers):
  PE-TEOS rate                 70 nm/min
  Reference dip                105 s
  Path length etched           70 nm/min × 105/60 = 122.5 nm
  Path tortuosity              47 nm worst path / 27 nm straight = 1.74
    (conservative, multiplicative)
  Euclidean reach from an opening edge   122.5 / 1.74 = 70.4 nm
  Reach from an opening centre            25 + 70.4 = 95.4 nm   ≡ R_crit
```

The oxide beneath a point is cleared if the point lies within R_crit of the centre of some working opening. In the intact lattice the farthest point (the triangle centroid between three openings) is P/√3 = 52 nm away, comfortably within R_crit. When openings fail, the farthest point recedes from the working openings, and the largest circle free of working openings has a radius R_e.

### 4.4.2 The Largest Empty Circle

The radius R_e of the largest circle that contains no working opening, for failed clusters of k adjacent openings (all arrangements of connected clusters on the hexagonal lattice, computed by enumeration):

```
Failed cluster                        Radius of largest empty circle R_e (nm)
  none (intact lattice)                52
  1 opening                            90.0
  2 adjacent                           90.0
  3 in a line                          90.0
  3 in a triangle                      103.9
  4 in a rhombus                       119.1
  Largest of any 5 adjacent            121.2
  Largest of any 6 adjacent            137.5
  7 (a hexagon with its centre)        155.9
```

A single failed opening puts the farthest oxide point at 90 nm, five-eighths of the way from the working neighbours to the next failure. A pair and a line of three do the same. The first cluster that exceeds the reach of the reference dip (95.4 nm) is the **triangle of three mutually adjacent failures**.

### 4.4.3 Dip Time Buys Cluster Tolerance

The reach grows with dip time, and so does the cluster size that can be tolerated. A cluster is *killer* if R_e exceeds R_crit(t), where R_crit(t) = 25 + (70 · t/60)/1.74 nm:

```
Dip      R_crit   Smallest cluster   Distinct    Failure probability per opening
time     (nm)     that is a killer   shapes      for 0.01 killer clusters per die
                                                 (independent failures)
  97 s   90       any single opening   1         —   (a single failure uses all the margin)
 105 s   95       triangle (k = 3)     2         1.1 × 10⁻⁴      ← reference
 120 s   105      rhombus (k = 4)      3         9.4 × 10⁻⁴
 150 s   126      k = 6                8         8.2 × 10⁻³
 180 s   146      hexagon (k = 7)      1         2.2 × 10⁻²
```

The failure probability is found from the expected number of killer clusters per die:

```
λ = N_sites × (distinct killer shapes) × pᵏ ≤ 0.01
  N_sites = 4.25 × 10⁹ (top support, one per opening)
  k = 3, 2 shapes:   p ≤ (0.01 / (2 × 4.25 × 10⁹))^(1/3) = 1.06 × 10⁻⁴
  k = 4, 3 shapes:   p ≤ (0.01 / (3 × 4.25 × 10⁹))^(1/4) = 9.4 × 10⁻⁴
```

Four things follow:

1. **The reference dip is sized for single failures.** A single missing opening needs 97 s; the dip is 105 s. The 8% margin is what remains for the rate variation the dip must also absorb.
2. **Cluster tolerance is expensive.** Each extra 15 s of dip raises R_crit by about 10 nm, and costs about 0.25 nm of nitride on every exposed face (1.0 nm/min). Raising the tolerance from triangles to rhombi costs 15 s and 0.25 nm per face.
3. **Random failure rates of about 10⁻⁴ are tolerable.** A failed opening per ten thousand costs nothing if the failures are independent. Four hundred thousand openings per die can fail in a random pattern without a single stranded pocket of oxide.
4. **The middle support is not the critical layer.** The lower oxide is BPSG at 600 nm/min and has a path surplus of 105 s × 600 − 662 nm = 388 nm, a lateral reach of 223 nm, so R_crit at the middle support is 248 nm. Only a cluster of about 19 failed openings strands oxide there. The binding layer is the top support, which sits above the slow PE-TEOS.

### 4.4.4 S2 Reverses the Picture

In S2 the HF etches the upper oxide **vertically** from the openings. The front must travel 650 nm down, so the dip time is set by a path of about 635 nm, and a lateral offset to the nearest working opening adds almost nothing:

```
S2 dip 1 path to the deep corner = √(ρ² + h²),   h = 635 nm,  ρ = R_e − 25
  ρ = 65 nm (single failed opening)   path 638 nm   +0.5%
  ρ = 94 nm (rhombus)                 path 642 nm   +1.1%
  ρ = 131 nm (hexagon)                path 648 nm   +2.1%
  ρ = 200 nm                          path 666 nm   +4.8%
```

S2 tolerates clusters of seven failed openings at a cost of 2% in dip time. Where S0 and S1 are lateral-path-limited and sensitive to cluster failures, S2 is vertical-path-limited and insensitive to them. That robustness is one of the arguments for S2 (Chapter 14), and it is paid for in HF exposure (Chapter 14), a second dry, and TiN exposure on the free pillars (Chapter 13).

---

## 4.5 Correlated Failures: What Actually Kills

### 4.5.1 Why Independence Fails

The calculation above assumes failures are independent. They are not. A particle on the ACL, a missing hole in the resist, a bubble in the BARC, a local etch stop, or a spatial pocket of thick polymer each affects *neighbouring* openings together. A killer cluster is therefore not three coincident random events; it is one event with a footprint.

```
Footprint needed to kill (reference lattice):
  Three adjacent openings (triangle)     centres 52 nm from the centroid, radii 25 nm
  Smallest covering circle               radius 52 + 25 = 77 nm → diameter 154 nm
```

A particle 154 nm across, sitting on the ACL or in the resist when the pattern is transferred, covers three openings. Smaller particles take out one, or two, and are forgiven. Larger particles take out larger clusters: a hexagon of seven openings is covered by a circle of radius 90 + 25 = 115 nm, a 230 nm particle.

### 4.5.2 Yield from Killer Defects

```
Array area per die                       17.18 × 10⁹ cells × 1734 nm² = 0.298 cm²
Poisson yield   Y = exp(−D_k · A_array)

  Killer-defect density D_k    Yield loss
  0.005 /cm²                   0.15%
  0.01                         0.30%
  0.02                         0.59%
  0.05                         1.5%
```

A killer-particle density of 0.02/cm² (particles above 154 nm on the patterned ACL, plus the footprint-equivalent of resist and mask defects) costs 0.6% die yield, comparable to the other mold-etch losses of Book #30 (Chapter 16: 1.4%). The specification is on defects, not on opening rates: killer clusters at less than 0.01 per die, and the defect density that follows from it.

### 4.5.3 The Other Source of Stranded Oxide

A plasma not-open opening is one cause of stranded oxide. The second is a column that is open but will not fill with liquid, because polymer residue makes its walls hydrophobic (Book #30, Section 4.5). A trapped-gas column behaves like a failed opening for the dip, and a polymer-contaminated region of the wafer produces trapped-gas columns in clusters. Chapter 9 shows how the post-etch clean controls it, and Chapter 12 combines the two sources.

---

## 4.6 Ligaments, Roughness & the Upper CD Limit

### 4.6.1 A Bounding Estimate

The lower limit on opening width is access: the free area of the clover (Section 1.2.3), and the minimum of 40 nm at the middle support (free area 829 nm²). The upper limit is set by the ligaments between openings. After the dip-out each support is a perforated sheet in tension. A bounding estimate assumes the film keeps its deposition stress of +250 MPa and concentrates it into the net section between openings:

```
Net-section stress between neighbouring openings (top support):
  Ligament width            P − D = 90 − 50 = 40 nm
  Net stress                σ_net = σ × P/(P − D) = 250 × 90/40 = 562 MPa
  Hole concentration        K_hole ≈ 2 (equibiaxial tension around a circular hole)
  Edge roughness            K_rough ≈ 1 + 2√(a/ρ) = 2.4  (a = 1.5 nm deep, ρ = 3 nm tip radius)
  Peak stress at the edge   562 × 2 × 2.4 ≈ 2.7 GPa

  Fracture strength of H-rich PECVD SiN (thin film)   ≈ 3–4 GPa
```

```
Opening CD (nm)   Ligament (nm)   σ_net (MPa)   Peak (GPa)   Margin to 3.5 GPa
  50              40              562           2.7          1.3
  53              37              608           2.9          1.2
  55              35              643           3.1          1.1
  56              34              662           3.2          1.1
```

This is an upper bound: the pillars, bonded to the sheet and anchored at the bottom stop, share the load, and the sheet relaxes where it is free. It is nevertheless informative. The margin falls below 1.2 for CDs above 53 nm, and *edge roughness is a multiplier of the same size as the hole itself*. A support whose openings print 5 nm too large and etch with 3 nm of striation is a cracked support. Book #30 (Chapter 11) treats the lattice-level failure; this book controls the two inputs, CD and edge roughness, from the etch side (Chapter 10).

### 4.6.2 The Design Window

```
Opening CD at the top-support top (reference, 3σ):
  Lower limit   ≈ 47 nm   HF access and free area (Section 1.2.3); gives ≥ 41 nm at the middle support
  Target        50 nm     (± 2.5 nm litho + ± 1.0 nm etch bias, root sum of squares: ± 2.7 nm)
  Upper limit   ≈ 53 nm   ligament fracture margin (Section 4.6.1); overlap depth
                          at 3σ (Section 4.3.2) already at the 20 nm limit
```

The window is 6 nm wide, and the process uses ± 2.7 nm of it. There is no room for a second error source.

---

## 4.7 Design-for-Etch Rules

```
Rule                                                     Source
─────────────────────────────────────────────────────────────────────────────────────
1. Place openings on interstitial sites                  minimum TiN exposure
2. Keep the overlap depth at 3σ ≤ 20 nm                  TiN budget; collar
3. Keep opening CD between 47 and 53 nm at the top       access; ligament fracture
4. Keep the middle-support opening ≥ 40 nm               free area ≥ 830 nm²; HF and ALD access
5. Size the dip for the cluster you expect, not the      reach table (§4.4.3)
   one you hope for; tolerance costs 0.25 nm per 15 s
6. Specify killer-defect density, not opening yield      correlated failures (§4.5)
7. Control striation: a 1.5 nm notch costs 2.4× stress   ligament margin (§4.6)
8. In S2, expect cluster robustness for free             vertical path (§4.4.4)
```

---

## Summary and Key Takeaways

1. **The lattice is a design object with a six-nanometre window.** CD from 47 to 53 nm at the top: access below, ligament fracture above.

2. **A single failed opening is forgiven; a triangle is not, at the reference dip.** The largest empty circle grows from 52 nm (intact) to 90 nm (one, two, or three in a line) to 104 nm (triangle), against a reach of 95 nm at 105 s.

3. **Dip time buys cluster tolerance at 0.25 nm of nitride per 15 s.** Random failure rates of 10⁻⁴ are tolerated at 105 s, 10⁻³ at 120 s, 10⁻² at 180 s, if failures are independent.

4. **Failures are not independent.** A killer defect is a particle or resist defect 154 nm across; yield follows D_k × 0.298 cm².

5. **The top support is the critical layer.** The lower oxide's reach is 223 nm; it takes about 19 failed middle-support openings to strand it.

6. **S2 reverses the sensitivity.** Vertical HF paths add 2% for a hexagon of failures.

7. **Edge roughness multiplies the stress.** A 1.5 nm notch costs a factor of 2.4 at the hole edge; at CD 55 nm the fracture margin is 1.1.

---

## Study Questions

1. A new resist process adds 1 nm (3σ) of CD variation. Recompute the overlap depth at 3σ using the root-sum-square form of Section 4.3.2. Does the line remain inside 20 nm?

2. Three mutually adjacent openings on a hexagonal lattice of pitch P fail. Show that the centre of the largest empty circle is the centroid of the failed triangle and that its radius is 2P/√3 (hint: the centroid lies P/(2√3) from each edge, and the nearest working opening lies one triangle height, P√3/2, beyond the edge). Check against 103.9 nm in Section 4.4.2.

3. A dip of 135 s is adopted. Find R_crit, the smallest killer cluster, and the independent-failure probability that gives 0.01 killer clusters per die. Estimate the extra nitride loss per face against the 105 s reference.

4. Layout C has pitch 77.9 nm and openings of 44 nm. Using the reach formula, find the dip time at which a triangle of failed openings is just tolerable. Compare with the reference and say what each choice buys.

5. A lot shows a killer-particle density of 0.04/cm² on the patterned ACL. What is the yield loss? If the cause is a particle population with diameters distributed as D⁻³ above 100 nm, what fraction of the particles above 100 nm is above 154 nm?

6. Using the stress model of Section 4.6.1, find the opening CD at which the peak stress reaches 3.5 GPa for edge roughness of K_rough = 2.4, and the CD for K_rough = 3.0. What does that say about the value of an etch step that smooths the opening edge by 1 nm?

---

**Next Chapter:** [Chapter 5: CCP Chambers for the Nitride Lattice Open](./05-ccp-chambers-nitride-lattice.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
