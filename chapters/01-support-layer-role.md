# Chapter 1: The Support Layer & Why It Is Etched

## Overview

A TiN pillar 1.6 µm tall and 28 nm wide cannot stand alone through a wet process. Capillary forces in the last rinse bend it toward its neighbour, and two pillars that touch are two dead cells. The industry's answer is a **support layer**: a thin silicon nitride sheet, laid into the mold at two heights, that ties every pillar to its neighbours and cuts the free span of each from 1.6 µm to under 800 nm. In the reference array the top support is 120 nm thick and the middle support 50 nm. A third film, the 20 nm bottom stop, protects the landing pads and is never opened.

A solid sheet would hold the pillars and imprison the mold. The oxide around the pillars is the thing that must be removed, and hydrofluoric acid can reach it only through holes in the sheet. So the support layer must be **perforated**: about 4.2 billion openings per layer on a 16 Gb die, each 50 nm wide, each placed between pillars on a 90 nm hexagonal lattice. Cutting them is the **support layer etch**, the subject of this book.

Book #30 (*DRAM Capacitor Mold Etch*) treats the support open as the first half of a module that ends with the HF dip-out, and takes the supports mainly as a mechanical skeleton. This book takes the other view. The support layer is a **film to be etched**: a nitride of particular composition, patterned by a mask with a particular placement error, cut by a plasma that must spare titanium nitride on one side of the opening and silicon oxide at the bottom, and left permanently in the finished capacitor with whatever the etch did to its edges. Where Book #30 asks how many pillars the lattice holds, this book asks how many openings fail, why, and how anyone would know.

This chapter explains what the support layers do, why every later process depends on the openings, where the etch sits in the flow, the routes by which it can be done, and the specification sheet the rest of the book works against.

**Learning Objectives:**
- Explain the mechanical and process roles of the top and middle supports
- Count the openings per die and per wafer and the area of nitride that must be removed
- Trace every liquid, vapor, and precursor that passes through an opening, and the opening's size after each coating
- Place the support layer etch in the capacitor flow and distinguish the routes S0, S1, and S2
- Explain why one pillar in four never sees the plasma
- Read the specification sheet and the failure each line protects against

---

## 1.1 What the Support Layers Do

### 1.1.1 The Pillar Without Support

```
Reference pillar and mold (Books #29, #30):

  TiN pillar            32 nm top / 28 nm average / 24 nm bottom, 1.60 µm tall
  Young's modulus       ≈ 400 GPa
  Gap to neighbour      17 nm (45 nm hexagonal pitch)
  Aspect ratio          1600 / 28 ≈ 57 : 1

  Mold                  Top SiN support       120 nm
                        Upper PE-TEOS         650 nm
                        Middle SiN support     50 nm
                        Lower BPSG            760 nm
                        Bottom SiN stop        20 nm
```

After the mold is gone, a pillar clamped at its base and free along its length bends easily. A pillar of this size with a free span of 1.6 µm is between 9 and 20 times more compliant than one with a free span of 760 nm: (1600/760)³ = 9.3 for a tip load and (1600/760)⁴ = 19.6 for a distributed one. Book #30, Chapter 10, develops the mechanics. The result that matters here is the **design rule**: the supports must cut every free span below about 800 nm, and they must still be there, intact and attached to every pillar, after minutes of hydrofluoric acid.

### 1.1.2 What a Support Is

```
Support layers (reference, as deposited):
                    Top support     Middle support    Bottom stop
  Thickness         120 nm          50 nm             20 nm
  Film              PECVD low-H SiN PECVD low-H SiN   LPCVD SiN
  Stress            +250 MPa        +250 MPa          +1.0 GPa
  Opened by         this book       this book         never
```

The top support sits at the pillar tops and is flush with them after top isolation. The middle support divides the pillar into a 770 nm upper span and an 810 nm lower span. Each is a nitride sheet through which the pillars pass, bonded to the TiN by adhesion and by the metal deposited against the hole wall.

### 1.1.3 The Support as a Perforated Plate

After the opening, each support is a perforated plate with two kinds of holes: the pillars, which pass through it, and the openings, which do not. Book #30, Chapter 2, gives the solid fractions: 39% for the top support and about 46% for the middle. They are re-derived from geometry in Chapter 4 of this book, together with the stress concentrations the openings create and the strength they leave.

```
One opening cell (hexagonal, pitch 90 nm), top support:
  Area                              7015 nm²   (= 4.05 cells of 1734 nm²)
  Pillars (32 nm) in the cell       4.05 × 804 = 3256 nm²
  Opening (50 nm circle)            1963 nm²
  Overlap of opening with 3 pillars 3 × 317 = 951 nm²
  Holes in the sheet (union)        3256 + 1963 − 951 = 4268 nm²
  Solid nitride                     2747 nm²  → 39%
```

---

## 1.2 The Opening Is the Only Door

### 1.2.1 Counting the Doors

```
Openings (16 Gb die, reference lattice):
  Cells per die                        16 × 2³⁰ = 1.718 × 10¹⁰
  Cells per opening                    7015 / 1734 = 4.045
  Openings per support layer per die   1.718 × 10¹⁰ / 4.045 = 4.25 × 10⁹
  Openings per cm² of array            10¹⁴ nm²/cm² / 7015 nm² = 1.43 × 10¹⁰
  Nitride cut per opening (top)        1963 − 951 = 1012 nm²  (the rest is TiN)
  Nitride plan area cut per die        4.25 × 10⁹ × 1012 nm² = 0.043 cm²
  Fraction of array area that is nitride being cut   1012 / 7015 = 14.4%
```

A 300 mm wafer carries about 900 gross dies, so one support layer on one wafer is cut with about 3.8 × 10¹² openings. There is no repair for a support opening; the lattice itself must be forgiving, and Chapter 4 shows how forgiving it is.

### 1.2.2 What Passes Through

Every process that touches the pillars after the support layer is cut goes through these openings:

```
Who uses the door (in flow order):
  1. Etch plasma          ions, radicals, polymer precursors            this book
  2. Strip and clean      O₂ or N₂/H₂ radicals, rinse                    Ch. 9
  3. HF dip-out           5 wt% HF in, H₂SiF₆ and H₃BO₃ out              Book #30
  4. Rinse and dry        DI water, IPA, or supercritical CO₂            Book #30
  5. High-k ALD           Zr and Al precursors, ozone                    Book #33
  6. Top electrode        TiCl₄ and NH₃ (or ALD TiN)                     Book #32
  7. Plate fill           SiGe and W CVD precursors                      Book #32
```

An opening that is partly closed by residue, undersized by taper, or later narrowed by every conformal film does not merely slow one step. It passes the problem to the next.

### 1.2.3 The Door Gets Smaller

Every conformal film grows on the opening wall as well as on the pillars. Starting from the opening at the top and middle supports:

```
Opening width at each stage (reference S0 numbers, illustrative):
                                          Top support     Middle support
  Etched (after strip)                      50.0 nm          44 nm
  After dip-out (nitride loss 1.8 / 1.3     53.6 nm          46.6 nm
    nm per wall)
  After ZAZ (5.5 nm on each wall)           42.6 nm          35.6 nm
  After top-electrode TiN (5 nm each wall)  32.6 nm          25.6 nm
  Free width for the plate fill             ≈ 33 nm          ≈ 26 nm
```

Plate fill through a slot 26 nm wide and 50 nm long is not a trivial CVD problem; a SiGe fill needs about 20 nm of clear width at its narrowest point to close without a void. The specification of at least 40 nm for the middle-support opening comes from this table, not only from the needs of the HF.

### 1.2.4 The Pillars the Plasma Never Sees

The opening lattice is a hexagonal superlattice at twice the pillar pitch, centred on interstitial sites. Each opening overlaps the three pillars that surround its site. Counting pillars against openings (exact for the ideal lattice: three pillars per opening, four pillars per opening cell):

```
Pillars touched by an opening:
  Touched by exactly one opening      75%     → 1.29 × 10¹⁰ pillars per die
  Touched by none                     25%     → 4.3 × 10⁹ pillars per die
  Touched by two or more              0%
```

**One pillar in four never faces the support-open plasma.** The top of such a pillar is covered by the mask throughout the etch. Its neighbours that do face the plasma lose TiN from their tops, take up fluorine, and may open a seam; the covered pillar does none of that. The array therefore contains two classes of cell on a strict 3:1 pattern. Chapter 11 follows that difference through capacitance, leakage, and retention, where it appears as a periodic signature in the fail bitmap, and Chapter 13 shows how it drives differential charging between neighbours.

---

## 1.3 Where the Etch Sits in the Flow

### 1.3.1 The Capacitor Flow

```
Capacitor module (reference), with the books that treat each step:

  Mold deposition (SiN / PE-TEOS / SiN / BPSG / SiN)          Book #29
  Hole etch (hard mask, 57:1)                                 Books #29, #31
  TiN fill; top isolation by CMP                              Book #32 (module 1)
  Support-open mask: ACL, SiON, ArF-i lithography
  ► SUPPORT LAYER ETCH (S0, S1, or S2) ◄                      this book
  ACL strip, polymer removal
  HF dip-out; rinse; dry                                      Book #30
  ZAZ ALD (5.5 nm)                                            Book #33
  Top-electrode TiN, SiGe fill, W strap, oxide cap
  Plate etch                                                  Book #32
  Dielectric clear                                            Book #33
  ILD; periphery contacts
```

The support layer etch has two neighbours that set its terms. Upstream is the planarized pillar array, with its top-isolation CMP scatter in the top-support thickness (±4 nm, 3σ), its pillar dishing, and the incoming TiN surface (Chapter 2). Downstream is the HF dip-out, which dissolves oxide from the sides of the openings, thins the nitride on every wall, and cannot wet a surface covered in fluorocarbon (Chapter 9).

### 1.3.2 Book #30's Support Open and This Book

| | Book #30 | Book #34 |
|---|---|---|
| Treats the support open as | first half of the mold module | a module of its own |
| Support layer seen as | skeleton | film to be etched, and a permanent part of the device |
| Plasma steps | SN1, OX, SN2, LAND as one recipe | the two nitride steps in depth; oxide step as context |
| Statistics | cell-level failures from leaning | opening failures, clusters, and stranded oxide |
| Selectivity to TiN | pillar-top loss of 5 nm accepted | origin of the loss; routes that cut it to 3 nm and to 1 nm |
| Second route | one page (Section 14.2) | a reference process (S2) with its own costs |
| Dip-out, drying, leaning | detailed | taken as given |

Where Book #30 states a result, this book derives it from the etch side, and the two must agree. Where the two differ in a number, the difference is noted in the text.

---

## 1.4 The Routes

### 1.4.1 One Pass or Two

```
Route  How                                               Where treated
─────────────────────────────────────────────────────────────────────────────────────
S0     One-pass plasma: SN1, OX, SN2, LAND in one         Book #30; baseline here
       chamber (Book #30's recipe)
S1     One-pass, nitride steps rebuilt: polymer flash,    Ch. 3, 5, 6, 10–12
       tailored-waveform bias, pulsed OX step (reference)
S2     Sequential and self-aligned: SN1; partial HF       Ch. 7, 13, 14
       dip; dry; SN2 through the top-support openings;
       second dip
S3     S2 extended to three supports                      Ch. 14
P      Pre-opened middle support, patterned before the    Ch. 14
       upper oxide is deposited
```

S0 and S1 cut the whole column, nitride, oxide, nitride, and landing, in one plasma pass before any HF. The pass is deep (about 920 nm of film, with the mask 1220 nm), and its mask budget leaves 47 nm of a 300 nm carbon mask. S2 cuts only the top support, lets HF remove the upper oxide, and then cuts the middle support through the top-support openings from above, in a cavity from which all the upper oxide is gone. It removes the oxide step from the plasma, and with it about half of the TiN top loss and most of the mask budget problem. It exposes the free upper half of every pillar to the plasma, and it costs a second dry. Chapter 14 weighs the trade quantitatively.

### 1.4.2 What Each Route Gives and Costs

```
Route comparison (reference array, illustrative; derived in Ch. 3, 6, 13, 14, 16):
                      S0        S1        S2
Plasma time           195 s     226 s     ≈ 75 s
Mask (ACL)            300 nm    300 nm    160 nm
ACL margin            47 nm     47 nm     57 nm
TiN top loss          5.0 nm    3.2 nm    1.0 nm
TiN sidewall dose     crescents crescents upper pillar surface
Support loss in HF    1.8 nm    1.8 nm    3 nm (fast upper oxide)
Dips and dries        1         1         2
Module cost           ref       +$0.5     +$7 (two dips and dries)
```

---

## 1.5 Why a Nitride Etch Is Hard Here

The etch of a 120 nm silicon nitride film is not hard in itself. Contact and via etches cut nitride everywhere. Four conditions make this etch different:

```
1. Metal in the wall     Three TiN crescents form a third of every opening's wall
                         at the top. The nitride must be cut next to them, with
                         the crescent surface facing the plasma for the whole etch.
2. A thin landing        The middle support is 50 nm, buried 650 nm down a column
                         with a landing oxide of its own below it. Cut too short, and
                         a nitride sliver blocks the door. Cut too long, and the
                         etch gouges the BPSG toward the bottom stop.
3. A permanent film      The sheet stays in the device. Its edges, composition, and
                         surface chemistry after the etch are part of the capacitor
                         (Chapters 2, 9, 10).
4. A very large count     4.25 × 10⁹ openings per layer per die. The question is
                         not whether the etch works on average but whether a cluster
                         of failures ever strands oxide (Chapters 4, 12).
```

The first condition is Chapters 3, 6, and 11. The second is Chapters 8 and 12. The third is Chapters 2, 9, and 10. The fourth is Chapter 4 and, with its metrology, Chapter 15.

---

## 1.6 The Specification Sheet

```
Support layer etch specification (reference, illustrative):

Parameter                                  Target                 Protects against
─────────────────────────────────────────────────────────────────────────────────────────
Opening CD, top support, after strip       50 ± 3 nm (3σ)        HF access, lattice strength
Opening CD, middle support                 ≥ 40 nm               plate-fill door (§1.2.3),
                                                                  HF access to the lower oxide
Overlap depth into nearest pillar          ≤ 20 nm               TiN exposure, weakened collar
Top-support remaining after etch           ≥ 116 nm              tie stiffness (loss ≤ 4 nm)
Middle-support remaining                   ≥ 46 nm               tie stiffness
TiN pillar-top loss                        ≤ 5 nm (S1 ≤ 3.5)     capacitance, seam opening
TiN crescent wall loss (lateral)           ≤ 2 nm                capacitance, dielectric leakage
Residual nitride at the middle-support     none ≥ 3 nm wide      blocked HF access
  opening
Landing depth into BPSG                    50–150 nm              mask, bottom-stop distance
Random not-open openings (independent)     ≤ 1 × 10⁻⁴            killer clusters (§4.4)
Killer clusters (≥ 3 adjacent not-open)    < 0.01 per die         stranded oxide, low C_s
Fluorine on TiN after clean (XPS)          ≤ 3 at%               ZAZ nucleation, leakage
Polymer on walls after clean               water contact angle   HF wetting, trapped gas
                                           ≤ 30° on witness
ACL mask margin at end of etch             ≥ 40 nm               top-support loss
Particle adders (≥ 30 nm)                  ≤ 10 per wafer        bridges, residual oxide
Throughput (4-chamber CCP platform)        ≥ 35 wafers/h         cost
```

---

## 1.7 The Reference Process

The reference array, mold, mask, and supports are those of Book #30. What this book adds is the nitride etch in detail and two routes beyond Book #30's recipe.

```
Reference array (Book #30):
  1b-class 6F², F = 17 nm, cell 1734 nm², pitch 45 nm hexagonal
  TiN pillars 32 / 28 / 24 nm, E = 400 GPa, C_s = 8.6 fF (EOT 0.50 nm)
  Mold: SiN 120 | PE-TEOS 650 | SiN 50 | BPSG 760 | SiN 20 (1.60 µm)
  Openings: 50 nm circles on a 90 nm hexagonal lattice at interstitial
            sites; overlap 15 nm into each of three pillars; 28% open

Support-open mask:
  ACL 300 nm / SiON 25 nm / BARC / ArF-i resist, single exposure
  CD 50 ± 2.5 nm (3σ); overlay ± 5 nm (mean + 3σ)

S0 (Book #30's recipe, CCP 60 MHz / 2 MHz, ≈ 400–600 eV):
  SN1 40 s | OX 110 s | SN2 20 s | LAND 25 s = 195 s
  TiN top loss 5.0 nm; ACL used 253 nm of 300

S1 (this book's one-pass reference):
  4 s polymer flash before SN1 and SN2; tailored-waveform bias on the SN steps;
  OX and LAND pulsed (10 kHz, 80%)
  SN1 44 s | OX 129 s | SN2 24 s | LAND 29 s = 226 s
  TiN top loss 3.2 nm

S2 (sequential reference):
  ACL 160 nm retained through dip 1 and SN2
  SN1 44 s | dip 1 (fast upper oxide) | dry | SN2 ≈ 31 s | ACL strip | dip 2 | dry
  TiN top loss ≈ 1.0 nm
```

---

## Summary and Key Takeaways

1. **The support layer is a perforated nitride sheet.** 120 nm on top, 50 nm in the middle, 39–46% solid after the opening, holding 17 billion pillars through every wet step.

2. **The opening is the only door.** About 4.25 × 10⁹ per layer per die; every plasma, wet, and deposition step reaches the pillars through them. After ZAZ and top electrode the door is 33 nm at the top support and 26 nm at the middle.

3. **One pillar in four is never exposed to the plasma.** The lattice touches 75% of pillars, once each. The array is a strict 3:1 pattern of two kinds of cell.

4. **The etch is hard for reasons other than nitride.** TiN in the wall, a thin buried landing, a permanent film, and a count of billions.

5. **Three routes frame the book.** S0 is Book #30's recipe, S1 rebuilds its nitride steps, and S2 splits the plasma around a partial dip.

---

## Study Questions

1. Recompute the solid fraction of the top support for 56 nm openings on the same 90 nm lattice (Book #30 asks the same question). Then find the lattice pitch at which 56 nm openings give the reference open fraction of 28%, and how many openings per layer per die that pitch leaves.

2. A 1c-class array has F = 15 nm, cells of 1350 nm², a 16 Gb die, and an opening lattice at twice the pillar pitch. How many openings per layer per die, and how many per cm² of array?

3. Using the table in Section 1.2.3, compute the free width for the plate fill if ZAZ thickens to 6.2 nm and the top electrode to 6 nm. Is a middle-support opening of 40 nm still adequate if HF loss is 1.3 nm per wall?

4. Show that an opening lattice at exactly twice the pillar pitch touches 75% of the pillars (hint: count pillars in one 2 × 2 supercell that lie within 41 nm of the centroid of one of its two triangles). What fraction would be touched if the openings were centred on pillars instead of interstitial sites?

5. State two reasons the nitride sheet must stay in the capacitor, rather than being removed after the dip-out, and one cost each reason imposes on the etch.

6. S2 removes the oxide step from the plasma. List three things that this change gains and three that it costs. (Chapter 14 returns to each.)

---

**Next Chapter:** [Chapter 2: The Support Film — Nitride Families, Stack, Incoming Surface & Etch Behaviour](./02-support-film-families.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
