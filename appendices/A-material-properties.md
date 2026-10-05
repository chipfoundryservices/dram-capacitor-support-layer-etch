# Appendix A: Material Properties

Properties of the support films, the materials around them, the mask, the polymer, the chamber materials, and the process gases used in this book. Values are representative of the films described in Chapter 2 after the 580 °C thermal history of the TiN fill; bulk values are given where the film value is not well defined. All values are illustrative.

---

## A.1 Support Films

```
Property                  PECVD low-H   LPCVD-class  PEALD     SiCN        SiBN        SiON
                          SiN (ref.)    SiN (stop)   SiN       (C 12 at%)  (B 8 at%)   (O 15 at%)
──────────────────────────────────────────────────────────────────────────────────────────────────
Reference use             top and       bottom stop  —         S2 supports S2 option   sacrificial
                          middle support                                                cap
Thickness (nm)            120 / 50      20           —         120 / 50    120 / 50    —
Si/N ratio                0.80          0.75         0.80      —           —           —
H content (at%)           8             3            10        12          6           7
Density (g/cm³)           2.95          3.10         2.85      2.7         2.6         2.7
Refractive index (633)    1.95          2.02         1.90      1.85        1.80        1.75
Stress (MPa)              +250 T        +1000 T      +100 T    +200 T      +150 T      −50 C
Young's modulus (GPa)     220           250          200       180         150         140
Dielectric constant       7.0           7.5          6.5       5.0         4.8         5.8
HF rate, 5 wt%, 25 °C     1.0           0.7          1.5       0.25        0.15        2.5   nm/min
Plasma rate (SN, rel.)    1.00          0.80         1.10      0.55        0.45        1.80
Fracture strength (GPa)   3–4           5–6          2.5–3.5   2.5–3.5     2–3         1.5–2.5
```

```
Reference supports (Chapter 2):
                    Top support    Middle support    Bottom stop
  Thickness         120 ± 4 nm     50 ± 1.5 nm       20 nm
  Interface layers  2 nm SiON      3 nm SiON top,    —
                    (top face)     3 nm SiON + B, P
                                   at the base
  After the TiN fill:  H 14 → 8 at%, thickness −2.5%, stress +50 → +250 MPa,
                       HF rate 1.5 → 1.0 nm/min, plasma rate × 0.81
```

```
Sensitivities (PECVD films of similar stoichiometry):
  Plasma rate:   +4% per at% H;    Si/N 0.75 → 0.90:  × 1.15 (and SiN:SiO₂ 1.4 → 1.2)
  HF rate:       +7% per at% H;    Si/N 0.75 → 0.90:  × 0.65
```

---

## A.2 TiN Pillar and Related Surfaces

```
Property                           Value
───────────────────────────────────────────────────────────────────────────────
TiN (CVD, pulsed, 550–600 °C)      Resistivity 150–200 µΩ·cm; E ≈ 400 GPa
                                   Density 5.4 g/cm³; Ti–N pair density 5.3 × 10²² cm⁻³
Pillar diameters                   32 nm (top) / 28 nm (average) / 24 nm (bottom)
Seam                               closed at the surface in 90% of pillars; open, a few nm deep, in 10%
Pillar capacitance to ground       ≈ 1 fF (storage-node junction, floating)
TiN native oxide (TiON)            1–2 nm at the pillar top after CMP
TiF₄                               sublimes at 284 °C; soluble in water and HF (hydrolyses)
TiCl₄                              b.p. 136 °C (why Cl-chemistry etches TiN)
TiO₂                               dissolves slowly in dilute HF
Crescent (top support, 32 nm pillar)  top face 317 nm²; arc 38.2 nm; overlap depth 15 nm
```

---

## A.3 Mold Oxides

```
Film                    HF rate, 5%, 25 °C   Plasma (SN, nm/min)   Plasma (OX, nm/min)   Role
─────────────────────────────────────────────────────────────────────────────────────────────────
Thermal SiO₂ (ref.)      23 nm/min            —                     —                     reference
PE-TEOS (upper oxide)    70                   148                   450 (CW)              upper mold
PSG (6 wt% P)            300                  —                     —                     S2 upper oxide
BPSG (3.5 B, 4 P wt%)    600                  —                     400 (CW)              lower mold
Dependence of BPSG HF rate:   +1 wt% B × 1.4;  +1 wt% P × 1.3;  +50 °C anneal × 0.85
```

---

## A.4 The Mask

```
Film             Thickness (nm)   Role / properties
───────────────────────────────────────────────────────────────────────────────────────────────
ACL (carbon)     300 (S1), 220 (S2 SiCN), 160 (S2 SiN)    O/ion etch; absorbing in the visible
SiON cap         25               open by CF₄/CHF₃
BARC + resist    —                ArF immersion, single exposure; CD ≈ 52 nm
Selectivities (nitride steps):    SiN:ACL ≈ 3 at 400 eV; Ox:ACL ≈ 5 (OX step)
ACL CD after open                 50 nm ± 2.5 nm (3σ); striations 2.0 nm (3σ)
Reference budget (S0/S1)          253 nm of 300 nm used; 47 nm remaining at the thinnest point
```

---

## A.5 Polymer and Surface States

```
Property                              Value
──────────────────────────────────────────────────────────────────────────────────────────
Fluorocarbon polymer                  Water contact angle 110° (aged); thickness 1–4 nm
Steady-state film (SN steps, d₀ = 3.4 nm on TiN):   TiN 3.4 nm; SiN 2.04 nm; SiO₂ 1.19 nm; ACL 2.4 nm
Flash (CH₃F/Ar, 4 s, no bias)         1.6 nm on TiN at 0.4 nm/s
Clean oxide or nitride after strip     θ ≈ 10°
Cassie relation                        cos θ = φ cos 110° + (1 − φ) cos 10°
Thresholds                             φ ≤ 0.365 → θ ≤ 60° (reliable fill); φ = 0.74 → θ = 90° (no fill)
TiN oxide after a 50 s O₂/N₂ strip     1.13 nm at 150 °C; 1.58 nm at 250 °C; + ≈ 0.9 nm under the ion flush
Fluorine on TiN (XPS, pillar top)      8–12 at% after the etch; 1.5–3 at% after ion flush + radical strip
```

---

## A.6 Etch Rates Used in the Book

```
Process step (S0/S1)       Chemistry                              Rate (nm/min), at the aspect ratio shown
─────────────────────────────────────────────────────────────────────────────────────────────────────────────
SN1 (top SiN)              CH₂F₂/CF₄/O₂/Ar, 400 eV                SiN 225 (AR 2–4);  SiO₂ 148;  TiN 0.75 steady;  ACL 75
SN2 (middle SiN)           same                                   SiN 150 (AR 17); 159 (AR 13, S2)
OX                         C₄F₆/O₂/Ar, 600 eV, CW                 oxide 370 (average)
LAND                       C₄F₆/O₂/Ar, 500 eV                     BPSG 290; SiN 48
Remote NF₃/O₂ (40 °C)      F atoms, no ions                       SiN 10;  SiO₂ 0.8;  TiN: 1.5 nm F skin
Plasma ALE (35 eV)         CH₃F/Ar + Ar⁺                          SiN 0.5 nm/cycle (5.5 s)
Hot H₃PO₄ (160 °C)         wet                                    SiN 5;  SiO₂ 0.05;  TiN 0.8
HF 5%, 25 °C               wet                                    see A.1 and A.3
Bare rates at 400 eV (model):  SiN 1730;  SiO₂ 493;  TiN 23;  ACL 810   (no polymer)
```

---

## A.7 Chamber Materials

```
Material             Behaviour in HFC/O₂ plasma                        Use
─────────────────────────────────────────────────────────────────────────────────────────────
Silicon              scavenges F (SiF₄); wears 0.5 mm per 600 RF-h     upper electrode, ring
SiC                  scavenges F; more durable                         upper electrode, ring
Y₂O₃                 forms YOF; resistant; sheds fluorinated flakes    liners, shields
                     with age
YOF                  stable in F; some particle shedding                coated surfaces
Al₂O₃                forms AlF₃; erodes; particle source                bare aluminium: avoid
Quartz               attacked by F                                      windows (avoid)
```

---

## A.8 Process Gases

```
Gas      Role                              Hazard and handling
─────────────────────────────────────────────────────────────────────────────────────────────
CH₃F     flash; polymer-rich nitride       flammable; gas cabinet with excess-flow shut-off
CH₂F₂    nitride steps                     flammable
CF₄      fluorine source                   greenhouse (PFC); abatement
C₄F₆     OX and LAND                       toxic, flammable; low vapor pressure
O₂       polymer removal; film control     oxidizer
NF₃      remote-plasma trim                oxidizer; PFC-class; abatement
Ar       ion source; actinometer           inert
Effluent HCN, (CN)₂, SiF₄, COF₂, HF       point-of-use abatement (burn box + scrubber); HCN monitor, alarm at 2 ppm
```

---

## A.9 Geometry Constants

```
Array (reference):          F = 17 nm; cell 1734 nm²; pillar pitch 45 nm hexagonal (1754 nm² by pitch)
Opening lattice:            hexagonal, pitch 90 nm (7015 nm² = 4.045 cells); circles of 50 nm at interstitial sites
Open fraction               28.0%;  solid top support 39.2% (middle ≈ 46%)
Centre-to-pillar axis       45/√3 = 26.0 nm
Openings (16 Gb die)        4.25 × 10⁹ per layer; 1.43 × 10¹⁰ per cm² of array
Pillars touched / untouched 75% / 25% (1.29 × 10¹⁰ / 4.3 × 10⁹ per die)
Clover free area            top 1013 nm² (D = 50); middle 938 nm² (D = 44); 829 nm² at D = 40
Inscribed free diameter     20 nm (top, 32 nm pillars); 22 nm (middle, 30 nm pillars)
Largest empty circle (nm)   1 failed: 90;  triangle: 103.9;  rhombus: 119.1;  hexagon (7): 155.9
1d-class array (Book #31)   37 nm pitch; pillars 23 nm; gap 14 nm; 2.10 µm mold; cells 1176 nm²; 24 Gb
```

---

**Appendix A Version:** 1.0  
**Last Updated:** 2026-10-05
