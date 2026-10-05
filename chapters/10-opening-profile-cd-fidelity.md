# Chapter 10: Opening Profile, CD & Pattern Fidelity

## Overview

The mask prints a circle 50 nm across. What the etch delivers at the bottom of the column is not that circle. It is a column that tapers by a few nanometres over 770 nm, has a notch or a step where nitride meets oxide, carries the striations of the carbon mask, shifts sideways by a fraction of a nanometre per tenth of a degree of ion tilt, and is a clover, not a circle, because a third of its wall is titanium nitride. At the middle support, where the column is narrowest and the lower oxide must be reached, the budget is thin: **a 44 nm opening against a 40 nm limit, with 3 nm of 3σ spread**.

This chapter follows the pattern from the mask to the middle support. It builds the CD budget at each level, shows how the top, the interface, and the bottom each contribute, and then asks how much of the opening is available to a liquid or a gas: the free area of the clover. It ends with the S2 problem that has no counterpart in S0 or S1: the opening at the middle support in a free cavity is defined by ion trajectories, not by walls, and at 400 eV it is 38 nm wide.

**Learning Objectives:**
- Build the CD budget at the top and the middle support from its contributions
- Compute the taper angle from the CD change over depth
- Explain the step at the nitride–oxide interface and what it does to the wall
- Convert an etched CD into the free area of the clover and its sensitivity to CD
- Compute the effect of tilt and overlay on the overlap depth at the middle support
- Estimate the roughness transferred to the nitride wall and its consequence for the ligament
- Compute the cleared width of the middle-support opening in S2 from the ion angular spread

---

## 10.1 The Column from Mask to Landing

### 10.1.1 CD Through the Stack

```
Support-open column, S0/S1 (reference; Book #30 Table 3.1.1 extended):
  Film             Depth (nm)    Column CD at the bottom of the film (nm)   Wall
  ACL mask         −300 → 0      50 (target ± 2.5)                          ACL
  Top SiN          0 → 120       49.2                                        SiN + 3 TiN crescents
  Upper oxide      120 → 770     45.0                                        SiO₂ + 3 TiN crescents
  Middle SiN       770 → 820     44.0                                        SiN + 3 TiN crescents
  Landing (BPSG)   820 → 920     43.0                                        BPSG + 3 TiN crescents

  Taper per side:  (50 − 44) / 2 = 3 nm over 770 nm  →  atan(3/770) = 0.22°
```

The column narrows by 6 nm in diameter over its 770 nm to the middle support. The taper comes from the polymer film that builds on the wall as ions are lost to it: the deeper the point, the fewer the ions and the thicker the passivation. The slope is gentle, but the budget it eats is the one that matters: the middle-support CD, which must stay at or above 40 nm.

### 10.1.2 The Budget at the Middle Support

```
Middle-support CD (S1, 3σ):
  Mean:  50 − 6 (taper) = 44 nm
  Contributions (each 3σ):
    Litho and ACL open (CD at the mask)   ± 2.5 nm
    ACL transfer into the nitride (bias)  ± 1.0 nm
    Taper (depth and polymer variation)   ± 1.0 nm
    Etch bias in SN2 at AR 17             ± 0.8 nm
  Combined (root sum of squares)          ± 3.0 nm
  Lower bound                             44.0 − 3.0 = 41.0 nm   (limit 40 nm)
```

The margin is 1.0 nm. The top-support CD has 0.3 nm to each edge of its 47–53 nm window (Chapter 4), so the lattice is tight at both levels, and every other result in this chapter is read against these two margins.

---

## 10.2 What Shapes the Wall

### 10.2.1 The Taper

A fluorocarbon film grows on the column wall wherever ions do not remove it. The rate of film growth is nearly constant with depth; the ion flux at the wall falls as the aspect ratio rises. The net result is a wall that is thicker in polymer, and a column that is narrower, at depth. A steeper taper means more polymer or fewer ions at the wall.

```
Taper sensitivity (S1; illustrative):
  More polymer (d₀ +0.3 nm)      taper +0.04° → CD at the middle support −0.5 nm
  Cooler wafer (−5 K)            polymer on the wall +10% → −0.4 nm
  Higher ion energy (+100 eV)    taper −0.02° → +0.3 nm
```

The wall effects are small compared with the 3σ budget but they are systematic, and they move together with the settings of Chapter 6. The ion-driven recipe levers that look free for TiN (Section 6.6) are not free here: a thicker polymer film, a cooler wafer, or lower energy narrow the column.

### 10.2.2 The Nitride–Oxide Interface

SN1 stops on oxide, with a 20 nm overetch (Chapter 3). The nitride wall of the top support is then exposed to the OX chemistry for 129 s. In that chemistry the nitride wall etches laterally at about 0.3 nm/min by radicals (F-poor, C₄F₆), a few tenths of a nanometre. The oxide wall sees ions and polymer and tapers. The result is a kink at the interface:

```
Wall profile at the interface (illustrative):
  Top SiN base (z = 120 nm):     CD 49.2 nm, wall recessed 0.6 nm by lateral radical etch
  Oxide wall at z = 140 nm:      CD 48.8 nm
  Net step:                      ≈ 0.6 nm of nitride set back relative to the oxide wall
```

The step is below a nanometre and is not a CD problem. It is a **residue site**: polymer collects at the concave corner and the HF later etches the oxide and the nitride at different rates there (Chapter 12).

### 10.2.3 Bowing

Bowing, a widening at mid-depth, is the signature of ions scattering from the wall. At 600 eV in a column of aspect ratio 17 with a narrow-angle distribution, the effect is below measurement (< 0.5 nm). It becomes a concern above AR 25 and in Book #31's 2.1 µm molds.

---

## 10.3 The Clover and the Free Area

### 10.3.1 From CD to Area

The opening is a circle minus three crescents. The area available to a liquid or a gas is the circle's area less the TiN crescents. It is not the circle's area, and it responds to CD differently:

```
Free area of the clover (computed from the circle–crescent geometry of Chapter 1):

  Top support (pillar 32 nm, centre-to-axis 26 nm)
    CD (nm)     Circle (nm²)    Crescents (nm²)    Free (nm²)    Equivalent diameter    Overlap depth
    47          1735            810                925           34.3 nm                13.5 nm
    50          1963            951                1013          35.9                   15.0
    53          2206            1096               1110          37.6                   16.5

  Middle support (pillar 30 nm)
    CD (nm)     Circle (nm²)    Crescents (nm²)    Free (nm²)    Equivalent diameter    Overlap depth
    38          1134            356                778           31.5 nm                8.0 nm
    40          1257            428                829           32.5                   9.0
    41          1320            465                855           33.0                   9.5
    44          1521            582                938           34.6                   11.0
    47          1735            708                1027          36.2                   12.5
```

A change of 1 nm in the CD at the middle support changes the free area by 30 nm², or 3.2%. A 4 nm CD margin (44 against 40) is 109 nm² of free area, 12%. The crescents grow faster than the circle as the opening widens: a 6% wider circle at the top support (50 to 53 nm) adds 15% to the crescent area and only 9.6% to the free area.

### 10.3.2 The Equivalent Diameter

The equivalent diameter of the clover's free area (the diameter of a circle of equal area) is 35.9 nm at the top support and 34.6 nm at the middle. The inscribed free diameter, between the three pillars, is 20 nm and 22 nm (Chapter 1) and does not depend on the CD. The opening grows by adding lobes toward the gaps between pillars and by widening them, not by widening the central channel.

---

## 10.4 Pattern Fidelity: Roughness and Striation

### 10.4.1 What the Mask Delivers

The ACL open, in O₂/COS or N₂/H₂, leaves a wall with striations: vertical grooves of 2 nm amplitude (peak to peak, 3σ) and 10–15 nm period. They are imprinted by the resist roughness and by the sidewall polymer of the carbon etch. The nitride etch transfers them to the wall:

```
Roughness transfer (3σ amplitude, illustrative):
  ACL after open               2.0 nm
  SN1 (polymer smoothing)      × 0.75   → 1.5 nm at the top-support wall
  OX (ion-driven, no smoothing) × 1.0   → 1.5 nm on the oxide wall
  SN2                          × 0.9    → 1.4 nm on the middle-support wall
```

The top-support wall, the one that carries the net-section stress, is left with 1.5 nm of roughness. That is the value used for the edge-roughness concentration in Chapter 4 (K_rough = 2.4 for a 1.5 nm notch with a 3 nm tip radius). A change from 1.5 to 2.0 nm of amplitude, with the same tip radius, raises K_rough to 2.6 and moves the CD at which the margin reaches 1.0 from 59 nm to 57 nm (Chapter 4, Question 6).

### 10.4.2 The Role of the Flash

The polymer flash of Chapter 3 deposits 1.6 nm of film on the walls before the etch begins. Polymer deposits faster in concave notches than on peaks (a conformal film fills a groove), and the flash therefore reduces the roughness the nitride sees at the start of SN1. Its smoothing effect is part of the 0.75 factor in the transfer above and is not controlled separately.

---

## 10.5 Placement: Tilt and Overlay at the Middle Support

### 10.5.1 The Overlap Depth at the Middle Support

At the middle support the pillar is thinner (30 nm), the column narrower (44 nm), and the overlap depth into each pillar is 44/2 + 15 − 26 = 11 nm. Overlay moves the whole column and tilt moves its bottom:

```
Overlap depth at the middle support, nearest pillar:
  Nominal                                       11.0 nm
  + overlay (mean + 3σ, RSS with CD)             +5.2 nm
  + tilt offset at the middle support
    (770 nm × tan θ; spec 0.3° → 4.0 nm)         +4.0 nm
  Worst case at 3σ at the wafer edge             ≈ 20.2 nm
```

The edge of the wafer has the largest tilt (Chapter 5, Section 5.5.2) and sits at the limit of 20 nm. An offset toward one pillar widens its crescent at the middle support and narrows the opposite side of the opening, where the nitride wall approaches the opposite pillar pair: free area is nearly conserved but its distribution is not.

### 10.5.2 Landing Depth

The landing depth into BPSG, which must lie between 50 and 150 nm (Chapter 1), is set by the LAND time and the arrival time of the nitride clear:

```
Landing depth into BPSG (S1):
  LAND 29 s at 246 nm/min; the BPSG etches for about 25 s of it (the first ≈ 4 s clear the nitride):
  Nominal depth                                    ≈ 100 nm
  Spread (3σ):
    LAND rate (± 3%)                               ± 3 nm
    SN2 clearing time (± 5.8% of 20 s = 1.2 s)     ± 5 nm
    ARDE and thickness of the middle support       ± 3 nm
  Combined (RSS)                                   ± 6.5 nm
  Window                                           50–150 nm  (margin ± 50 nm, 7.7 times the 3σ spread)
```

The landing depth is the best-controlled dimension in the column, and the window is wide. What it does not control is the nitride sliver in the corner, which the depth distribution cannot see (Chapter 12).

---

## 10.6 The Opening in S2: Defined by Ions, Not by Walls

### 10.6.1 A Cavity Has No Walls

In S2 the middle support is etched through the openings of the top support, with the upper oxide gone. The ions that reach the middle support pass through a 50 nm aperture 650 nm above it. There is no wall to guide them. The opening they cut is the **image of the aperture**, blurred by the ion angular spread:

```
Ion angular spread (T_i = 0.2 eV):  θ₁/e = atan(√(T_i / E))
  E = 400 eV:  1.28°    lateral blur at 650 nm:  σ_x = 650 nm × tan(θ₁/e) / √2 = 10.3 nm
```

The dose across the aperture image is a top-hat of width 50 nm convolved with a Gaussian of σ_x. To clear the nitride everywhere, including the 40% overetch, the dose at the edge must reach 1/1.4 = 71% of the centre dose.

```
Cleared width (dose ≥ 71%):   50 nm − 2δ,   δ = 0.4 √2 σ_x       (erf(0.4) = 0.428 = 2 × 0.714 − 1)

  Ion energy (eV)   θ₁/e    σ_x (nm)    δ (nm)    Cleared width at the middle support
  300               1.48°    11.9        6.7       36.6 nm
  400               1.28°    10.3        5.8       38.4 nm
  600               1.05°    8.4         4.7       40.5 nm
  800               0.91°    7.3         4.1       41.8 nm
  1000              0.81°    6.5         3.7       42.6 nm
```

At 400 eV the opening in S2 is **38.4 nm wide, below the 40 nm limit**. Raising the energy to 600 eV restores it, at the cost of a steady TiN rate 34% higher (Chapter 3 table) and a mask rate 37% higher (Chapter 6). Alternatively the top opening can be enlarged by 2 nm (to 52 nm), but the top-support window is only 47–53 nm and S2's CD budget (± 2.7 nm) would then exceed the upper limit of the lattice (Chapter 4, Section 4.6.2).

### 10.6.2 The Trade

```
S2 middle-support opening: ways to reach 40 nm

  Raise SN2 ion energy to 600 eV          +2.1 nm   TiN steady rate +34%, ACL rate +37%, free-pillar charging (Ch. 13)
  Lower T_i (colder ion source)           —         not available at 25 mTorr
  Enlarge the top opening to 52 nm        +2 nm     leaves ± 1 nm of the 47–53 window for the budget
  Radical trim of the middle support      ✘         12% dose at depth (Ch. 7)
  Use ALE cycles for the edge             +edge     26 minutes total (Ch. 7)
```

The one that works is energy. A route that is attractive for its TiN loss (Chapters 3 and 6) is limited here by an optical-style resolution argument: the aperture-to-target distance, 650 nm, against the ion divergence. It is one of the reasons the S2 reference of Chapter 14 runs SN2 at 600 eV.

---

## Summary and Key Takeaways

1. **The middle-support CD has a 1.0 nm margin.** 44 nm nominal, ± 3.0 nm (3σ), against a 40 nm limit.

2. **The column tapers 0.22° per side.** 50 nm at the mask, 44 nm at the middle support; thicker polymer and a cooler wafer narrow it.

3. **The free area is a clover.** 1013 nm² at the top support and 938 nm² at the middle; 1 nm of CD at the middle is 30 nm² (3.2%).

4. **Roughness is a stress multiplier.** 2.0 nm in the mask becomes 1.5 nm in the top-support wall, with a K_rough of 2.4.

5. **The overlap depth at the wafer edge reaches its limit.** 11 nm + 5.2 nm (overlay and CD) + 4.0 nm (tilt) = 20.2 nm.

6. **The landing depth is well controlled.** 100 ± 6.5 nm in a window of 50–150 nm; it cannot see slivers.

7. **In S2 the opening is an ion image.** 650 nm of free flight at 400 eV blurs the 50 nm aperture to a cleared width of 38.4 nm; 600 eV restores 40.5 nm.

---

## Study Questions

1. A taper of 0.26° per side replaces 0.22°. Recompute the CD at the middle support and the margin to 40 nm for the same top CD and RSS budget.

2. Find the free area at the top support for a CD of 51 nm, using the circle and crescent areas of Section 10.3.1 (interpolate), and the change in free area per nm of CD at the top support.

3. Compute the overlap depth at the middle support for an overlay of +5.2 nm and a tilt of 0.5° at the wafer edge. Is the 20 nm limit met?

4. Compute σ_x, δ, and the cleared width for S2 at 500 eV (T_i = 0.2 eV, cavity height 650 nm). Repeat for a cavity height of 500 nm.

5. A top opening at 52 nm is proposed for S2. Using the taper of the top support only (0.4 nm per side over 120 nm), find the aperture CD at the bottom of the top support, and the cleared width at the middle support at 400 eV. Does it meet 40 nm?

6. The ACL striation amplitude rises from 2.0 to 2.6 nm. Recompute the top-support wall roughness and K_rough (a = amplitude of the notch, ρ = 3 nm), and the net-section stress at a CD of 50 nm using Chapter 4's form.

---

**Next Chapter:** [Chapter 11: The Pillar Tops — TiN Loss, Two Classes of Cells & Fluorine Uptake](./11-tin-pillar-top-loss-two-classes.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
