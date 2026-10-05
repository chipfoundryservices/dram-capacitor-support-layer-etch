# Chapter 7: Radical, Atomic-Layer & Wet Nitride Removal — Trim, Finish & Stencil Routes

## Overview

The ion-driven HFC step of Chapters 3 to 6 cuts the support layer. It leaves a surface that is not quite what the specification asks: a hydrogen-depleted and fluorinated skin 1–2 nm thick on every nitride wall, an opening that may be 2–3 nm too narrow at the middle support, and, at the worst corners of the worst crescents, a nitride sliver. Three families of tools do not rely on ion bombardment and could in principle repair these: remote-plasma radical etching, atomic-layer etching, and a hot wet etch.

This chapter asks what each can do and how far it can reach. The answer is the central result: **radicals and low-energy ions do not reach the middle support**. A 50 nm column at aspect ratio 17 attenuates radicals to a few percent and low-energy ions to 14% of their flux at the top. The three tools are therefore tools for the top support, for trimming, and for rework, and not for the soft landing at the middle support. That one result decides what S2's second nitride etch must be (an ion-driven step, as in S1) and how much of the opening a finishing step may touch.

**Learning Objectives:**
- Compute the radical dose reaching depth z in a column from the wall recombination probability
- Compute the fraction of low-energy ions that can reach the bottom of a column from their angular spread
- Describe remote-plasma NF₃ etching of SiN and its fluorination of TiN
- Describe plasma ALE of SiN and its selectivity to TiN
- Evaluate a hot-phosphoric-acid finish with its trim, TiN, and wetting costs
- Match each tool to the job (trim, skin, sliver, free area) and the layer it can reach

---

## 7.1 The Jobs

```
Job                             Where              Size of the task
──────────────────────────────────────────────────────────────────────────────────
Trim the opening wider          top support wall   +1.5 nm per side (CD 50 → 53)
Remove the damaged wall skin    top and mid walls  1–2 nm of H-depleted, F, C-bearing nitride
Remove a nitride sliver         mid-support floor  up to 3 nm wide, in the crescent corners
Widen the middle-support opening mid support wall   +1–2 nm per side to reach 40 nm
Remove polymer                  every surface      Ch. 9 (not a nitride etch)
```

The first three are repair jobs and the fourth is a dimensional job. All are *small*: nanometres, not tens of nanometres. The bounds come from the lattice: the opening may grow by at most 3 nm in diameter (Chapter 4, Section 4.6.2) before the ligament margin falls to 1.1, so the **trim budget is 1.5 nm per side** on the top support. The skin and the sliver are of the same order.

---

## 7.2 Remote-Plasma Radical Etching

### 7.2.1 Chemistry

A plasma generated 20–40 cm from the wafer, behind an ion filter, delivers neutral fluorine atoms and no ions. In NF₃/O₂ or NF₃/H₂ chemistry:

```
Remote NF₃ etch of SiN (illustrative):
  Gases                   NF₃ 200, O₂ 100, Ar 500 sccm   (or NF₃ with H₂ for selectivity to oxide)
  Pressure                1.5 Torr;  remote source 3 kW (ICP or microwave)
  Wafer temperature       40 °C
  SiN rate                10 nm/min   (isotropic)
  SiO₂ rate               0.8 nm/min  → SiN:SiO₂ ≈ 12
  TiN                     fluorinated, not etched: self-limiting TiFₓ skin, 1.5 nm
  Activation energy (SiN) 0.12 eV:  7.4 nm/min at 20 °C, 10 at 40, 13 at 60, 16.5 at 80
```

The thermochemistry of Chapter 3 explains the selectivity: F atoms etch SiN spontaneously because forming N₂ pays for the broken Si–N bond (−1680 kJ per Si, against −1020 kJ for SiO₂). The TiN reacts equally strongly and produces TiF₄, which stays on the surface. With no ions to sputter it, the TiN **gains a fluorinated skin of about 1.5 nm and loses nothing**.

### 7.2.2 Trim and Sliver Removal

```
Trim of the top-support wall by 1.5 nm:    1.5 nm / (10 nm/min) = 9 s on a wall that sees the full flux
Removal of a 3 nm sliver, two exposed faces: 1.5 nm / (10 nm/min) = 9 s
Oxide loss in 9 s at 0.8 nm/min:           0.12 nm
TiN fluorination:                          1.5 nm skin in the first seconds, then self-limiting
```

On the surface the numbers look excellent. The difficulty is not the rate but the distribution of the dose.

### 7.2.3 The Reach of Radicals

F atoms travel down a column by diffusion and are lost on the walls. With a wall loss probability s per collision, the dose falls exponentially with depth over a length

```
λ = r · (4/(3s))^½ = 1.155 r / √s        (diffusion-reaction in a tube of radius r)
```

For the column radius of 22.5 nm:

```
Wall loss    λ          Dose at the base of the      Dose at the middle support
probability  (nm)       top support (120 nm)         (770 nm), relative to the top
0.002        581        81%                          27%
0.005        368        72%                          12%
0.02         184        52%                          1.5%
0.05         116        36%                          0.13%
```

On a clean oxide wall the F recombination probability is 0.002–0.01. Where polymer coats the wall it is higher. Taking s = 0.005, the dose at the bottom of the top support (z = 120 nm) is 72% of that at its top; at the middle support it is 12% of the dose at the top. A trim that removes 1.5 nm from the top of the top-support wall removes 1.1 nm from its bottom and **0.2 nm at the middle support**. Removing a 3 nm sliver at the middle support (1.5 nm from each of its two faces) would need 1.5/0.12 = 12 nm removed from each side at the top: an opening 24 nm too wide, and a broken lattice.

The result is a clear rule:

```
Radical etching is a tool for the top 150–350 nm of the column. It cannot finish the middle support.
```

### 7.2.4 The Fluorinated Skin

The TiN skin is the cost. The pillar tops and crescent walls gain 1.5 nm of TiFₓ and TiOₓFᵧ. TiF₃ and TiF₄ dissolve in water and in HF, so part of the skin is dissolved in the dip-out and takes its titanium with it. The loss is bounded by the skin thickness:

```
TiN removed with the skin in the dip-out (upper bound):  ≤ 1.5 nm per exposed surface
Exposed surfaces: the pillar top (crescent) and the crescent wall at the top support
```

The plasma etch of Chapter 3 leaves a similar fluorinated skin, so an additional radical step is an additional dose on the same surfaces. What the radical step costs is therefore not TiN sputtered but a deeper fluorination layer on the crescents; Chapter 11 treats the fraction that the dip-out removes.

---

## 7.3 Plasma Atomic-Layer Etching of Nitride

### 7.3.1 The Cycle

```
Plasma ALE of SiN (illustrative):
  Step A (modify)   CH₃F/Ar, 1.5 s, no bias:   forms a modified layer ≈ 0.5 nm deep
                    (the same chemistry as the flash of Chapter 3)
  Purge             0.5 s
  Step B (remove)   Ar⁺ at 35 eV, 3 s:         removes the modified layer, stops on the unmodified nitride
  Purge             0.5 s
  Cycle time        5.5 s      EPC ≈ 0.5 nm/cycle        rate ≈ 5.5 nm/min (at the top)
  Ion energy window 25–45 eV (below the sputter threshold of unmodified SiN, above that of the modified layer)
```

Because 35 eV lies below the TiN sputter threshold of 45 eV, the removal step does not sputter TiN at all. The TiN takes up polymer in step A and sheds it in B or in the strip; its loss is below the resolution of metrology, and the SiN:TiN selectivity is larger than 1000.

### 7.3.2 Ion Starvation in a Column

Low-energy ions have a large angular spread. For an ion temperature of 0.2 eV the 1/e half-angle of the angular distribution is atan(√(T_i/E)):

```
Ion energy    1/e half-angle    Acceptance of the        Fraction reaching the bottom
                                column (770 nm deep,     of the column
                                22.5 nm half-width: 1.67°)
35 eV         4.32°             1.67°                    14%
100 eV        2.56°                                      35%
400 eV        1.28°                                      82%
```

At 35 eV only 14% of the ions that enter the column reach the middle support. The B step, 3 s at the top, needs 3 s / 0.139 = 21.6 s at the bottom to deliver the same dose. A cycle at the middle support takes 1.5 + 0.5 + 21.6 + 0.5 = 24 s, and the removal rate is about 1.2 nm/min:

```
ALE at the middle support:  EPC 0.5 nm / 24 s = 1.2 nm/min
ALE at the top support (shallow): EPC 0.5 nm / 5.5 s = 5.5 nm/min
A 3 nm sliver at the middle support: 6 cycles × 24 s = 2.4 min
```

ALE is the right tool for the top support, and a rework tool at the middle support, where the 2.4 minutes per wafer are affordable only for lots that have already shown slivers.

### 7.3.3 In S2

In S2 the middle support is opened from above through the top-support stencil, in a free cavity of 650 nm. The acceptance angle is atan(25/650) = 2.2°, and the fraction at 35 eV is 23% instead of 14%. That is better, and still too slow for the opening itself (a 50 nm film in 100 cycles of 15.6 s is 26 minutes). The opening in S2 is made by the ion-driven HFC step at 400 eV, with 95% transmission, and ALE appears as a possible finish.

---

## 7.4 Hot Phosphoric Acid

### 7.4.1 What It Does

Hot phosphoric acid at 160 °C is the standard wet etch for nitride, with oxide selectivity of about 100:

```
Hot H₃PO₄, 160 °C (illustrative):
  SiN      5 nm/min
  SiO₂     0.05 nm/min       (BPSG: 0.05–0.1 nm/min)
  TiN      0.8 nm/min        (attacked; more with dissolved oxygen)
```

A 1.5 nm trim of every exposed nitride face takes 18 s and costs 0.24 nm of TiN and 0.015 nm of oxide:

```
H₃PO₄ for 18 s:   SiN 1.5 nm,  TiN 0.24 nm,  BPSG 0.015 nm
```

Unlike radicals, a liquid reaches everything it wets, so the dose at the middle support equals the dose at the top.

### 7.4.2 What It Costs

1. **It is isotropic and non-selective between faces.** It takes 1.5 nm from every nitride face: the top-support wall (opening +3 nm), the middle-support wall, and the ledge. It cannot remove a sliver without widening the opening by as much.
2. **It needs wetting.** A column coated with fluorocarbon residue does not fill (Book #30, Section 4.5; Chapter 9 of this book). The post-etch clean of Chapter 9 must come first, and a H₃PO₄ step that cleans the nitride and not the polymer is a poor cleaner.
3. **Silica.** Dissolved nitride becomes silicic acid and precipitates as silica when its concentration exceeds the solubility. In an 18 s step removing 1.5 nm from a 14% nitride-covered array the local concentration is low, but the bath is a recirculating one and its silicon content must be controlled below 100 ppm.
4. **Drying.** The step is in liquid; in S0 and S1 the pillars are embedded in oxide and are dried at no risk. In S2, with free pillars, it would add a dry (Chapter 14).

---

## 7.5 Which Tool for Which Job

```
Tool                  Reach              Trim top   Skin     Sliver at     Widen mid   TiN effect
                                         support    (walls)  mid support   mid support
────────────────────────────────────────────────────────────────────────────────────────────────────
Remote NF₃ radicals   top 150–350 nm     ✔  9 s     ✔        ✘ (12% dose)  ✘           1.5 nm F skin
Plasma ALE            top support;       ✔  17 s    ✔        rework only   rework      none (< 1 nm
  (35 eV)             mid: 14% of ions                        (2.4 min)                  resolution)
Hot H₃PO₄ (wet)       full depth         ✔  18 s    ✔        ✔ but trims   ✔ but trims 0.24 nm lateral
                                                                everything               everything
Ion-driven HFC        full depth         ✘          —        ✔ (SN2, LAND) ✔           flash-limited,
(Chapters 3–6)                                                                            0.4–1 nm
```

The mid-support sliver, the hard job, falls to the ion-driven step. In S0 and S1 that is the first seconds of LAND (Chapter 3, Section 3.6.2), and in S2 the SN2 overetch. The trim of the top support is where radicals or ALE earn their place. The decision between them rests on two points. Radicals are fast (9 s) and leave a fluorinated skin on the TiN; ALE is slower (17 s) and leaves none.

---

## 7.6 Hardware

```
Remote-plasma reactor (radical trim):
  Source             3 kW, ICP or microwave, 20–40 cm upstream of the wafer
  Ion filter         grounded grid or showerhead with high aspect ratio holes
  Wafer              ESC at 40 °C ± 1 K; no bias
  Process chamber    1.5 Torr; Al₂O₃ or Y₂O₃ lined; no Si parts (they would scavenge F)
  Throughput         9–18 s etch + 60 s overhead → 40–50 wafers/h per chamber

ALE chamber:         the CCP of Chapter 5 with 1 s gas switching and a bias generator
                     that can hold 35 eV ± 5 eV. A 6-cycle top-support trim is 33 s.

Wet processor:       single-wafer H₃PO₄ at 160 °C (≥ 45 s overhead for heat-up/purge);
                     ≥ 100 wafers/h on a 12-chamber platform. Silicon-in-bath control.
```

---

## Summary and Key Takeaways

1. **The finishing jobs are nanometres.** A 1.5 nm trim per side is the whole budget; the ligament limit sets it.

2. **Radicals do not reach the middle support.** With a wall loss probability of 0.005 the dose at 770 nm is 12% of the top, and a 3 nm sliver there would need 12 nm of trim per side at the top.

3. **Low-energy ions are starved.** At 35 eV, 14% of ions reach the middle support; an ALE cycle at the bottom takes 24–32 s.

4. **Fluorine passivates TiN; radicals fluorinate it.** The radical step costs no TiN, but leaves a 1.5 nm TiFₓ skin that the HF dip takes with it.

5. **Hot phosphoric acid reaches everywhere and trims everything.** 18 s removes 1.5 nm of every nitride face and 0.24 nm of TiN; wetting and silica are its problems.

6. **The soft landing is an ion-driven problem.** The tools of this chapter trim the top support. The middle-support sliver falls to the HFC step.

---

## Study Questions

1. Compute λ and the dose at 770 nm for a wall loss probability of 0.01 and 0.001. What wall condition would make a radical finish at the middle support viable (dose ≥ 50% at 770 nm)?

2. A top-support trim of 1.5 nm per side is required in a column with s = 0.02. What time is needed at the top, and what is removed from the bottom of the top support (120 nm)? Does the wall remain within the 3 nm total CD budget?

3. Using the Arrhenius form with E_a = 0.12 eV, find the temperature at which the remote NF₃ etch gives 20 nm/min. What does the TiN skin do at that temperature?

4. Compute the fraction of 50 eV ions that reach the bottom of the column and of the S2 cavity (take T_i = 0.2 eV). How long does a 3 s (at the top) B-step have to be at each bottom?

5. A hot-H₃PO₄ rework removes 3 nm from every nitride face. By how much does the opening grow, and where in the ligament margin table of Chapter 4 does that leave the lattice? What does it cost in TiN?

6. Choose a finishing tool for each of: a lot with a 2 nm skin on the top-support wall; a lot with slivers in 1 in 10⁶ middle-support openings; a lot whose middle-support opening is 38 nm instead of 40 nm. Justify with the table of Section 7.5.

---

**Next Chapter:** [Chapter 8: Endpoint & In-Situ Monitoring of a Thin Nitride in a 50 nm Opening](./08-endpoint-in-situ-monitoring.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
