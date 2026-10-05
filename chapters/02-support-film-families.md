# Chapter 2: The Support Film — Nitride Families, Stack, Incoming Surface & Etch Behaviour

## Overview

The etch cuts whatever the deposition made. A support layer is not "silicon nitride" in the sense of a stoichiometric crystal. It is a PECVD film with 8 atomic percent hydrogen, a Si/N ratio of about 0.8, a stress set by RF power, and a thermal history that includes a 580 °C TiN fill. Each of those facts moves its plasma etch rate, its HF rate, and its mechanical behaviour, and they do not move together. The film that survives HF best is, as a rule, the film that is hardest to cut.

This chapter describes the support film as deposited and as inherited, the stack of films the etch passes through and what each layer does to the plasma, the incoming surface (CMP-finished TiN tops and a damaged nitride skin), and the families of supports that might replace PECVD nitride. It ends with the trade between HF resistance and plasma etchability, which runs through the rest of the book.

**Learning Objectives:**
- Describe the reference support films, their hydrogen content, stress, and thermal history
- Predict how hydrogen, density, and composition shift the plasma and HF rates
- Describe the layers the etch crosses and the interfaces that make each landing soft or hard
- State the incoming surface: dishing, residues, TiN oxide, damaged nitride skin
- Compare nitride, carbonitride, boronitride, and oxynitride supports on HF loss, etch time, TiN loss, and mask budget

---

## 2.1 The Support Film as Deposited

### 2.1.1 Deposition

The supports are part of the mold. They are deposited before the capacitor holes are etched, by PECVD at about 400 °C from silane, ammonia, and nitrogen, with high RF power and a nitrogen-rich gas mixture to drive hydrogen down. The bottom stop is LPCVD, deposited at higher temperature on the landing-pad level before anything else.

```
Support films (reference, after the TiN fill thermal history):
                    Top support    Middle support    Bottom stop
  Thickness         120 nm         50 nm             20 nm
  Deposition        PECVD          PECVD             LPCVD
  Si/N ratio        0.80           0.80              0.75
  H content         8 at%          8 at%             3 at%
  Density           2.95 g/cm³     2.95 g/cm³        3.10 g/cm³
  Refractive index  1.95           1.95              2.02
  Stress            +250 MPa       +250 MPa          +1.0 GPa
  Modulus           ≈ 220 GPa      ≈ 220 GPa         ≈ 250 GPa
  Dielectric const. 7.0            7.0               7.5
  HF rate (5%)      1.0 nm/min     1.0 nm/min        0.7 nm/min
```

### 2.1.2 Thermal History

The films do not stay as deposited. The TiN fill at 550–600 °C drives hydrogen out of the nitride and densifies it:

```
Effect of the TiN fill (580 °C, ≈ 1 h), illustrative:
                         As deposited     After fill
  H content              14 at%           8 at%
  Thickness              123 nm           120 nm    (−2.5%)
  Stress                 +50 MPa          +250 MPa  (tensile, from shrinkage)
  HF rate (5%)           1.5 nm/min       1.0 nm/min
  Plasma rate (SN)       1.24 (relative)  1.0
```

Two consequences. First, the reference film is the film **after** the fill; a change in fill temperature or queue time at temperature changes the supports as well as the pillars. Second, the HF rate falls by a third and the plasma rate by about 19% over the same thermal history. Both fall because the films densify and lose hydrogen. A process that was tuned on blanket as-deposited monitors is off by that amount.

### 2.1.3 Why Tensile

A support in mild tension pulls itself flat and keeps its pillars straight. In compression, once the oxide around it is gone, it can buckle. Book #30 (Chapter 11) develops the window of +150 to +400 MPa. The etch adds one concern: perforating a stressed film changes its local state around each opening. Chapter 13 shows that the effect on pillar position is far below a nanometre.

---

## 2.2 Composition and Etch Behaviour

### 2.2.1 Hydrogen

Hydrogen sits as Si–H and N–H bonds that interrupt the nitride network. A hydrogen-rich film is less dense, more open, and etches faster in both plasma and HF.

```
Plasma etch rate vs H content (PECVD films of similar stoichiometry, illustrative):
  H content        4 at%    8 at%    12 at%    16 at%
  Relative rate    0.84     1.00     1.16      1.32          (≈ +4% per at%)

HF etch rate vs H content (5 wt% HF, 25 °C):
  H content        4 at%    8 at%    12 at%
  Rate (nm/min)    0.75     1.0      1.35                    (≈ +7% per at%)
```

The plasma sensitivity is weaker than the HF sensitivity. A 4 at% shift in H moves the HF loss by 30% and the SN1 time by 14%. The consequence for process control is that the **HF loss** is the more sensitive indicator of a drifting support, and it is the one measured by the downstream dip-out (Book #30).

### 2.2.2 Silicon-to-Nitrogen Ratio

```
Effect of Si/N ratio (illustrative, relative to 0.80):
  Si/N           0.75 (stoich.)    0.80     0.90 (Si-rich)
  Plasma rate    0.93              1.00     1.15
  HF rate        1.10              1.00     0.65
  SiN:SiO₂ in SN chemistry   1.4    1.5     1.2
```

Silicon-rich films contain Si–Si bonds that fluorine attacks without having to remove nitrogen; the plasma rate rises and the selectivity to oxide falls. They resist HF better because HF attacks the Si–N bond. The reference value of 0.80 is a slight silicon excess chosen to lower the HF loss at a small cost in selectivity.

### 2.2.3 Thickness and Uniformity

```
Thickness control (reference):
  Top support       120 nm ± 4 nm (3σ, wafer)   from CMP; deposition ± 3%
  Middle support     50 nm ± 1.5 nm (3σ)        PECVD uniformity ± 3%
  Plasma rate uniformity       ± 3% (3σ) on SN steps
  SN1 clearing-time spread     √(3.3² + 3²) ≈ 4.5% (3σ)
  SN2 clearing-time spread     √(3² + 4² + 3²) ≈ 5.8% (3σ)  (adds ARDE spread)
```

The overetches of 25% in SN1 and 40% in SN2 are 5 to 7 times the 3σ spread. Spread in the film is not what sets them. Chapter 12 shows that they are sized by the corner geometry at the crescents and by the landing statistics of Chapter 4.

---

## 2.3 The Stack the Etch Crosses

### 2.3.1 Layer by Layer

```
Cross-section of the support-open column (reference, S0/S1):

   ACL 300 nm            ████████████████    mask, etched by O-radical and ions
   SiON cap 25 nm        ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒    open before SN1
   ─────────────────── z = 0
   Top SiN 120 nm        ░░░░░░░░░░░░░░░░    SN1: polymer-rich nitride chemistry
   ·· interface 2 nm (SiON)
   Upper PE-TEOS 650 nm  ················    OX: C₄F₆/O₂/Ar, high energy
   ·· interface 3 nm (SiON)
   Middle SiN 50 nm      ░░░░░░░░░░░░░░░░    SN2: same chemistry, at AR 17
   ·· interface 3 nm (SiON; B, P from BPSG)
   Lower BPSG 760 nm     ················    LAND: 50–150 nm
   ─────────────────── z = 1580
   Bottom SiN stop 20 nm ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓    never reached
```

Each layer asks something different of the plasma:

```
Layer          Etch demand                         Selectivity set by
─────────────────────────────────────────────────────────────────────────────────
SiON cap       open without widening CD            CF₄/CHF₃, short
Top SiN        stop on oxide within 15 nm          polymer on oxide (SiN:Ox ≈ 1.5
                                                   in lean SN; Ch. 3)
Upper oxide    cut 650 nm, spare TiN and ACL       high-energy fluorocarbon, polymer
                                                   from C₄F₆; Ox:ACL ≈ 5
Middle SiN     cut 50 nm at AR 17, no sliver       SN chemistry again; SiN:Ox ≈ 1.5
                                                   makes the landing soft
Lower BPSG     land 50–150 nm; never the stop      Ox:TiN ≈ 40
```

### 2.3.2 Interfaces

The nitride does not end at a sharp plane. PECVD films grown on oxide begin with an oxynitride transition 2–3 nm thick, and the BPSG below the middle support loads it with boron and phosphorus by diffusion:

```
Middle support, as the etch sees it:
  Upper interface     3 nm   SiON, O/N falls from 100% to 0 over 3 nm
  Bulk nitride       44 nm   SiN, H 8 at%
  Lower interface     3 nm   SiON with B, P (≈ 1–2 at%)
```

Consequences:

1. **SN2 begins in an oxide-like layer.** The first 3 nm clear at the OX rate, which is higher than the nitride rate. The nitride proper begins after a short transient.
2. **SN2 ends in a soft landing.** The last 3 nm clear at the rate of a material whose selectivity to the landing oxide is lower than the nitride's. A "just clear" etch is not the same as a clean landing: the transition layer is what is left when the bulk is gone, and it clears slowly. The OES endpoint at SN2 (Chapter 8) sees the oxide signal grow before the last nitride atoms are gone.
3. **The B and P are a second residue.** If the interface layer is not cleared, boron and phosphorus sit at the base of the opening where the dip-out cannot reach them (Chapter 12).

### 2.3.3 What the Plasma Does to Each Surface

```
Surface exposed       Treatment by the SN / OX plasma
────────────────────────────────────────────────────────────────────────────────
Top SiN (top face)    under ACL: not exposed
Opening wall, SiN     fluorinated, 1–2 nm hydrogen-depleted layer, polymer 2 nm
Opening wall, oxide   polymer 1–2 nm; carbon in the top 1–2 nm of oxide
TiN crescent top      polymer 3.4 nm steady-state; fluorinated 1–2 nm
TiN crescent wall     polymer 2–3 nm; grazing ions only
```

The 1–2 nm hydrogen-depleted layer on nitride walls is a source of the HF loss that is not "etch": a layer that has lost its hydrogen and acquired carbon and fluorine etches in HF differently from the bulk, and the first seconds of the dip are controlled by it.

---

## 2.4 The Incoming Surface

### 2.4.1 After Top Isolation

The pillar array arrives from Book #32's module 1 after CMP (or etch-back) of the TiN fill:

```
Incoming surface (reference):
  Top SiN thickness              120 nm ± 4 nm (3σ)
  Pillar dishing                 0–3 nm below the SiN surface
  TiN surface oxide (TiON)       1–2 nm
  Damaged SiN skin               3–5 nm: hydrated, Si–OH rich, slurry residues
  Residual slurry cations        K, Na, Ce ≤ 5 × 10¹⁰ atoms/cm²
  Surface roughness (SiN)        0.3 nm rms
  Seam at pillar centre          closed in 90% of pillars at the surface; open
                                 (a few nm deep) in 10% (Book #30, Chapter 2)
```

The damaged skin on the nitride matters in two ways. First, it etches at an uncontrolled rate in the first seconds, which is part of why a **breakthrough** step (a few seconds of CF₄/Ar) is placed ahead of SN1. Second, it is hydrophilic and holds water: on a nitride that has queued in air, the first plasma seconds see outgassing water, which scavenges fluorine and thins the polymer.

### 2.4.2 The ACL and What It Leaves

The ACL is deposited at 450 °C or less from a hydrocarbon plasma directly on the pillar tops and the top support. At the TiN it forms a mixed carbon–titanium interface of 1–2 nm that is stripped with the mask. The O₂ ash that strips the ACL oxidizes the exposed TiN (Book #30, Chapter 3). In this book the ash is part of the post-etch treatment of Chapter 9, and the incoming TiON on the pillar tops (1–2 nm) is the starting point of that oxidation.

### 2.4.3 Dishing and the Crescent

Pillar dishing of 0–3 nm leaves the TiN crescent at the bottom of a shallow ledge at the start of SN1. It does not change the ion flux to the TiN, which is set by the aperture of the ACL opening, but it does affect where the polymer film grows first: the 3 nm ledge sees reduced neutral flux at the beginning, which lengthens the transient in which the TiN loses material before its protective film forms (Chapter 3, Section 3.5).

---

## 2.5 Families of Support Films

### 2.5.1 The Candidates

PECVD nitride is not the only choice. Films with carbon, boron, or oxygen added to the network change the HF rate by an order of magnitude in either direction:

```
Support film families (illustrative; after a 580 °C thermal history):
                          k     E (GPa)  H (at%)  Stress   HF rate     Plasma rate
                                                  (MPa)    (nm/min)    (rel. to SiN)
  PECVD low-H SiN (ref)   7.0   220      8        +250     1.0         1.00
  LPCVD-class SiN         7.5   250      3        +1000    0.7         0.80
  PEALD SiN               6.5   200      10       +100     1.5         1.10
  SiCN (C 12 at%)         5.0   180      12       +200     0.25        0.55
  SiBN (B 8 at%)          4.8   150      6        +150     0.15        0.45
  SiON (O 15 at%)         5.8   140      7        −50      2.5         1.80
```

LPCVD nitride is the best HF performer among the pure nitrides and cannot be used for the supports: its deposition temperature and its stress of +1.0 GPa crack the perforated lattice and, in the middle of the mold, exceed the thermal budget of the mold films. It is used for the bottom stop, which is never perforated. PEALD nitride has good step coverage and poor HF resistance. SiON is easy to cut and HF-soluble, which makes it useful as a sacrificial cap rather than a support (Chapter 14).

### 2.5.2 The Trade

Plotting the HF rate against the plasma rate shows a pattern: films that resist HF resist the plasma.

```
                    plasma rate (rel.)
              2.0 ┤                          ● SiON
                  │
              1.5 ┤
                  │               ● PEALD
              1.0 ┤        ● PECVD (ref)
                  │   ● LPCVD
              0.5 ┤ ● SiBN   ● SiCN
                  │
              0.0 ┼────┬────┬────┬────┬────┬─── HF rate (nm/min)
                  0   0.5  1.0  1.5  2.0  2.5
```

The reason is bonding. Carbon and boron additions replace Si–N–Si links with bonds that HF does not break, and the fluorine radicals of the plasma meet the same strengthened network. What the dip-out is spared, the etch pays for.

### 2.5.3 What the Trade Costs in the Etch

For each family the SN steps are scaled by the plasma rate. The TiN pillar-top loss and the ACL budget then follow from the model of Chapter 3.

```
Effect of the support family on route S1 and S2 (illustrative):
                     HF loss (nm/face)  SN1    SN2    TiN loss  ACL used (nm)
                     S0/S1    S2        (s)    (s)    SN steps  S1      S2
  PECVD low-H SiN    1.75     3.0       40     20     0.96 nm   253     103
  LPCVD-class SiN    1.23     2.1       50     25     1.15      272     122
  PEALD SiN          2.62     4.6       36     18     0.89      247     97
  SiCN               0.44     0.8       73     36     1.57      313     163
  SiBN               0.26     0.5       89     44     1.87      343     193
  SiON               4.38     7.6       22     11     0.62      221     71
```

In S1, with a 300 nm ACL, **neither SiCN nor SiBN fits the mask budget**: the nitride steps take 1.8 and 2.2 times as long, and the carbon mask erodes during them. In S2, where the oxide step is gone and the ACL is only 160 nm, SiCN just fits (163 nm used, so an ACL of 200 nm in practice) and SiBN needs about 200 nm. This is the opening move of the S2 argument of Chapter 14: a route that removes the oxide plasma step can afford a support that resists the longer HF dip of the sequential scheme.

### 2.5.4 Mechanics

Moduli of 150–220 GPa across the candidates mean that a support in SiBN is about 30% more compliant than the reference. The lattice's contribution to the pillar's stiffness scales with the product of modulus and thickness cubed over the span, and a 30% loss of modulus is recovered by a 10% increase in thickness (1.1³ = 1.33). Thickness costs more plasma time, so the families interact with the etch again through Section 2.5.3.

---

## Summary and Key Takeaways

1. **The reference film is the film after the TiN fill.** Hydrogen falls from 14 to 8 at%, the HF rate from 1.5 to 1.0 nm/min, the plasma rate by 19%. Monitors must see the same thermal history.

2. **Hydrogen moves HF faster than plasma.** About +7% per at% in HF, +4% per at% in the plasma. HF loss is the more sensitive indicator of a drifting support.

3. **The nitride has soft ends.** The middle support begins and ends in 3 nm of oxynitride; the landing is only fully clean when the transition layer, and the boron and phosphorus in it, are gone.

4. **The incoming surface is not clean.** 3–5 nm of damaged nitride skin, 1–2 nm of TiON on the pillar tops, and a seam that is open in 10% of pillars.

5. **What resists HF resists the plasma.** SiCN and SiBN cut the dip-out loss by a factor of 4 to 7 and lengthen the nitride steps by a factor of 1.8 to 2.2; in a one-pass route they exhaust the mask.

---

## Study Questions

1. A lot of supports was deposited with 12 at% H instead of 8 at%, and the TiN fill was unchanged. Using the sensitivities in Section 2.2.1, estimate the change in SN1 time and in HF loss per face. Which will the process engineers notice first?

2. A TiN fill temperature is raised from 580 to 620 °C, taking the support H content from 8 to 6 at%. Estimate the new SN1 time and HF loss.

3. The middle-support interface layers are 3 nm thick at each side. If their combined clearing rate is 60% of the bulk nitride rate in SN2, how many extra seconds does the 6 nm of interface add to the 50 nm film at an SN2 bulk rate of 150 nm/min?

4. A process engineer proposes replacing the middle support with SiCN to reduce HF loss from 1.3 to 0.3 nm per face. Using the table in Section 2.5.3, what does it do to SN2 time and ACL consumption in S1? Is there a mask budget at 300 nm?

5. Why is a PEALD nitride, with excellent step coverage, an unattractive support despite its low stress?

6. SiBN's modulus is 150 GPa against 220 GPa. What thickness would restore the ligament stiffness of the 120 nm top support, assuming stiffness scales as Et³? What does that do to SN1 time (take the SiBN plasma rate of 0.45)?

---

**Next Chapter:** [Chapter 3: Plasma Chemistry of Nitride Etching Between Metal Pillars](./03-nitride-plasma-chemistry.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
