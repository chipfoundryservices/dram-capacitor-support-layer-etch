# Chapter 11: The Pillar Tops — TiN Loss, Two Classes of Cells & Fluorine Uptake

## Overview

A pillar top is a few hundred square nanometres of titanium nitride at the edge of a column of plasma. The support layer etch exposes 38% of its circumference to the plasma for the whole etch, and spares the rest. Its loss is measured in nanometres and its effect on capacitance in a tenth of a percent. The loss does not matter for the average cell. What matters is that it is **unequal**: a pillar that touches an opening loses TiN, takes up fluorine, carries a thicker oxide, and may open its seam, and a pillar that does not touch one does none of that. The array is divided, on a strict pattern, into three cells in four that were etched and one in four that was not.

This chapter quantifies each difference. It shows that the loss of TiN is small, that the edge rounds more than the centre, that about 7.6% of the touched pillars expose an open seam, and that fluorine delays the nucleation of the dielectric. It then converts those effects into a weak-cell budget, and shows that the weak cells fall on the touched sublattice and nowhere else. The pattern is a signature, and the metrology of Chapter 15 uses it.

**Learning Objectives:**
- Compute the exposed TiN geometry of a crescent: top area, arc length, and fraction of the circumference
- Compute the capacitance loss from a given top loss
- Estimate the edge rounding and the field enhancement at the rounded edge
- Compute the fraction of touched pillars whose open seam is exposed
- Tabulate the differences between touched and untouched pillars
- Estimate the weak-cell budget of each route and its class pattern
- Compute the sample size that distinguishes class-linked fails from random fails

---

## 11.1 What Is Exposed

### 11.1.1 The Crescent

Each opening overlaps three pillars. The overlap with one pillar is a crescent of TiN:

```
Crescent geometry, top support (opening 50 nm, pillar 32 nm, centre-to-axis 26 nm):
  Top face of the crescent                 317 nm²   (39% of the pillar top, 804 nm²)
  Overlap depth into the pillar            15 nm
  Half-angle of the arc subtended          68.3°     cos φ = (26² + 16² − 25²)/(2·26·16)
  Arc length of pillar surface in the opening   2 × 1.193 rad × 16 nm = 38.2 nm
  Fraction of the pillar circumference      38%
```

Two surfaces are exposed. The **top face** of the crescent is under the ion flux for the whole etch and loses TiN by sputtering through the polymer film. The **crescent wall**, the arc of pillar surface that forms part of the column wall, sees ions at grazing incidence and the full radical flux, and loses less (specification ≤ 2 nm laterally).

### 11.1.2 How Much Is Lost

From Chapters 3 and 5:

```
TiN pillar-top loss (crescent centre):
  S0   (no flash; 2.36 nm in SN1 + SN2, 2.5 nm in OX + LAND)     ≈ 5.0 nm
  S1   (4 s flash; 0.97 nm in SN, 2.25 nm in OX + LAND)          ≈ 3.2 nm
  S2   (4 s flash; 0.97 nm in SN, no OX or LAND)                 ≈ 1.0 nm
```

---

## 11.2 What the Loss Costs in Capacitance

The capacitance is set by the outer area of the pillar (Book #30). The top loss removes a scallop of TiN from the arc of the pillar in the opening, and the area lost is the arc length times the depth:

```
Area lost = arc length × loss depth
  S0:  38.2 nm × 5.0 nm = 191 nm²      → 191 / (π × 28 × 1410 = 1.24 × 10⁵ nm²) = 0.15%
  S1:  38.2 nm × 3.2 nm = 122 nm²      → 0.10%
  S2:  38.2 nm × 1.0 nm =  36 nm²      → 0.03%
```

The loss is a fraction of a percent of one pillar's capacitance and applies only to the three-quarters of the pillars that touch an opening: an average of 0.11% (S0), 0.07% (S1), 0.02% (S2) across the array. The cell capacitance varies by several percent from other causes, and the top loss is not detectable in the average. **The pillar-top loss is not a capacitance problem.**

---

## 11.3 The Edge

### 11.3.1 Rounding

Ions reflect from the column wall and from the mask facet onto the TiN edge adjacent to the wall. The edge of the crescent therefore loses more than its centre:

```
Loss across the crescent (S1, illustrative):
  Centre of the crescent top         3.2 nm
  Edge adjacent to the column wall   ≈ 2 × centre = 6.4 nm
  Edge radius of curvature           r ≈ loss at the edge ≈ 6 nm
```

### 11.3.2 Field Enhancement

A convex electrode edge of radius r, surrounded by a dielectric of thickness t, has a field relative to a planar electrode of

```
FEF = (t/r) / ln(1 + t/r)        (concentric-cylinder estimate)

  Pillar side wall (r = 14 nm, t = 5.5 nm):   t/r = 0.393     FEF = 1.19   (every cell has this)
  Rounded crescent edge (r = 6 nm):            t/r = 0.917     FEF = 1.41
  Excess at the edge over the pillar wall:                      +18%
```

At a field of 1 MV/cm the extra 18% raises the local leakage by roughly a factor of 4 (a decade per 0.3 MV/cm, illustrative). The affected area is the edge of the crescent, of order 38 nm × 3 nm = 114 nm², 0.09% of the cell's capacitor area. Multiplying the two: 0.09% of the area, ×4 in current density, adds 0.3% to the cell's leakage. It is not a leakage problem for the average cell either.

---

## 11.4 The Seam

### 11.4.1 What the Crescent Reaches

Book #30 (Chapter 2) gives the TiN seam at the pillar centre: closed at the surface in 90% of pillars and open, a few nanometres deep, in 10%. Whether the etch reaches it depends on the overlap depth:

```
Overlap depth into the pillar:   15 nm nominal;   pillar radius 16 nm
  The axis of the pillar is 1 nm beyond the inner edge of a nominal crescent.
  Overlap depth distribution (overlay + CD, 3σ = 5.15 nm → σ = 1.72 nm):
    P(overlap > 16 nm)   28%     the crescent reaches or crosses the axis
    P(overlap > 18 nm)   4.0%
    P(overlap > 20 nm)   0.18%
```

A seam in the pillar is a trace through the axis that ends at two opposite points on the circumference. The trace reaches the plasma if one of its ends lies inside the arc of the crescent, which for a random orientation happens with probability 2 × 38% = 76%.

```
Open-seam pillars attacked per die (S1):
  Touched pillars               1.29 × 10¹⁰
  × open at the surface (10%)   1.29 × 10⁹
  × trace in the crescent (76%) 9.8 × 10⁸  per die   (7.6% of the touched pillars)
```

### 11.4.2 The Slot

An open seam etches faster than the surrounding TiN, because its walls are exposed to the radicals on both sides and the polymer there is thin. At 2.5 times the surrounding rate:

```
Slot depth at the seam = 2.5 × top loss
  S0   12.5 nm      S1   8.0 nm      S2   2.4 nm      (limit ≈ 10 nm)
```

A slot 8–12 nm deep and 2–3 nm wide is closed by the 5.5 nm of ZAZ deposited in the next module, and leaves a void under the dielectric that holds whatever the plasma and the TiN fill left in it (chlorine from the TiCl₄ fill, fluorine from the plasma). Book #30, Chapter 13, treats the electrode chemistry; here the point is only the count: about 10⁹ pillars per die, and the slot depth scaling with the top loss.

---

## 11.5 Two Classes of Cells

### 11.5.1 The Differences

```
Touched (75%) and untouched (25%) pillars after the support layer etch and strip (S1, illustrative):

                                     Touched (crescent)      Untouched
  Pillars per die                    1.29 × 10¹⁰             4.3 × 10⁹
  Top loss at the crescent           3.2 nm (edge 6.4 nm)    0
  Fluorine at the top (XPS)          1.5–3 at%               ≈ 0.5 at%
  TiN oxide on the top               2.0–2.5 nm              1.1–1.6 nm
                                     (ion flush + radicals)  (radicals only: ACL covers the top
                                                              during the ion flush)
  Open seam attacked                 7.6%                    0
  Slot depth where attacked          8 nm                    —
  Capacitance change                 −0.10%                  0
```

The untouched pillars are covered by the carbon mask for the whole plasma exposure, including the ion flush of Chapter 9, which hits the mask, not them. They see only the radical stage of the strip.

### 11.5.2 Fluorine and the Nucleation of the Dielectric

ALD of ZrO₂ nucleates on TiN through the metal-bound surface groups. Fluorine on the surface blocks them. The effect is an incubation delay:

```
Nucleation delay (illustrative):   ≈ 2 cycles per at% F on TiN
  Touched top (2 at% F):    4 cycles delayed
  ZrO₂ growth per cycle:    0.087 nm  (2.6 nm in 30 cycles)
  ZAZ thinner at the crescent:  4 × 0.087 = 0.35 nm   (5.5 → 5.15 nm)
  Leakage increase (a decade per 0.5 nm of thickness):  × 5
```

Again the area is the limit: the crescent top and its edge are 0.1–0.3% of the capacitor area. The leakage multiplier of 5, the edge's 4, and an open seam's 10 multiply to 200 on an affected crescent edge. A cell with a baseline leakage of 0.3 fA, with 0.09% of its area carrying a factor of 200, gains 0.054 fA, still within the 1 fA allocation of the dielectric (Book #33). **None of these defects, alone or compounded, fails a typical cell.** They fail the cells that start near the limit: the weak-cell tail.

### 11.5.3 The Weak-Cell Budget

Book #30 (Chapter 16) counts the seam and top-loss leakage cells of its route at 2 cells per 10⁹, 34 per die. Scaling with the slot depth squared (a deeper slot is a bigger void and a worse pinhole):

```
Seam and top-loss weak cells per die (illustrative):
  Route     Top loss    Slot depth    Scale (depth/12.5)²    Cells per die
  S0        5.0 nm      12.5 nm       1.00                   34   (Book #30)
  S1        3.2 nm      8.0 nm        0.41                   14
  S2        1.0 nm      2.4 nm        0.037                  1.3
```

Another 1–3 cells per die can be added for fluorine-delayed ZAZ in each route, a number small against the repair resource of a few thousand cells and not zero. The relevant figure is not the count but where they lie.

---

## 11.6 The Class Signature

### 11.6.1 A Pattern in the Bitmap

Every one of these mechanisms acts on touched pillars. If 97% of the class-linked fails are on the touched sublattice and the rest are random (with the touched sublattice holding 75% of them), the class-linked fails are distinguishable from a random population:

```
Test:  fraction of failing cells on the touched sublattice
  Random fails:                 75%
  Class-linked fails:           97%
  Standard error at N fails:    √(0.75 × 0.25 / N)

  N fails    Difference/SE (z)
  10         1.6
  20         2.3
  50         3.6
  100        5.1
```

With 50 failing cells of one signature, the touched sublattice can be told from random at 3.6σ. The physical address of each cell is mapped to its pillar's class through the layout (the lattice of Chapter 4, with the actual overlay offset determining the class; it is a function of the cell's position within a 2 × 2 supercell).

### 11.6.2 Why It Matters

A bitmap whose weak cells lie on the 3:1 pattern points at the support layer etch (and the dip-out, Chapter 12), and not at the dielectric, plate, or transistor modules. In a production fab, where a failure may be caused by any of dozens of steps, a signature that identifies the module is worth more than the cells themselves.

---

## 11.7 Reducing the Asymmetry

```
Option                                              Effect
────────────────────────────────────────────────────────────────────────────────────────
Layout C (all pillars touched, Ch. 4)               no two-class pattern; all pillars carry the loss
S1 with a post-etch TiN top touch-up                equalizes tops: adds a step and a CMP-like cost
Dummy openings over untouched pillars               touches all, costs solid fraction (39% → 28%)
Lower the top loss (S1 → S2)                        shrinks the differences themselves
Keep the untouched pillars for monitors             use the untouched class as a built-in control
```

The last row turns the asymmetry into an advantage: one cell in four has not seen the plasma, and its leakage and nucleation behaviour are a built-in reference for what the etch has done to the other three.

---

## Summary and Key Takeaways

1. **The crescent is 38% of the circumference.** A top face of 317 nm² and an arc of 38.2 nm; its loss is 5.0, 3.2, or 1.0 nm in S0, S1, and S2.

2. **The loss is not a capacitance problem.** 0.15%, 0.10%, 0.03% on a touched pillar; 0.11% to 0.02% averaged over the array.

3. **The edge rounds more than the centre.** About 6 nm of radius, a field 18% above the pillar wall, and a local leakage up by a factor of 4 over 0.09% of the area.

4. **7.6% of touched pillars expose an open seam.** About 10⁹ per die; the slot is 12.5, 8, or 2.4 nm deep.

5. **No single defect fails a typical cell.** Compounded, they add 0.05 fA to a 0.3 fA cell; they matter for the weak-cell tail: 34, 14, and 1.3 cells per die for S0, S1, and S2.

6. **The weak cells are on the touched sublattice.** 97% against 75% for random fails; 50 fails distinguish them at 3.6σ.

---

## Study Questions

1. Compute the crescent arc length and the fraction of circumference for an overlap of 18 nm (opening 50 nm, pillar 32 nm, centre-to-axis 26 nm moved by 3 nm toward one pillar). What is the capacitance loss for a top loss of 3.2 nm?

2. The edge radius in S2 is 1.5 nm in a 5.5 nm dielectric. Compute FEF and its excess over the pillar wall, and compare with S1.

3. A pillar has a seam trace of random orientation and an arc of 150° in the crescent. What is the probability that the trace is exposed? How does it change at 180°?

4. A lot shows 1.8 times the normal number of touched-class weak cells. Using the scaling of Section 11.5.3, what change in top loss would explain it? Which levers of Chapter 6 could cause it?

5. A bitmap analysis finds 38 class-linked fails, of which 35 are on the touched sublattice. What is the fraction and the z-value against 75%? Is this evidence of a class-linked mechanism?

6. Layout C touches every pillar. What happens to the class signature, to the number of seam-exposed pillars per die, and to the average capacitance loss, relative to layout A?

---

**Next Chapter:** [Chapter 12: Slivers, Scum & Not-Open Openings — Residue Statistics](./12-slivers-scum-not-open.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
