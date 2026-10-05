# Appendix B: Chemistry & Thermochemistry Data

Thermodynamic and kinetic data used in Chapters 3, 7, 9, 13, and 14. Enthalpies are standard values at 298 K, rounded; kinetic parameters are model values calibrated to the reference process. All are illustrative.

---

## B.1 Standard Enthalpies of Formation

```
Species          State   ΔH_f (kJ/mol)        Species          State   ΔH_f (kJ/mol)
─────────────────────────────────────────────────────────────────────────────────────────
Si₃N₄            s       −744                 TiN              s       −338
SiO₂             s       −910                 TiF₄             s       −1649
SiF₄             g       −1615                TiCl₄            g       −763
F                g       +79                  N₂               g       0
HF               g       −273                 HCN              g       +135
CF₄              g       −933                 (CN)₂            g       +308
H₂SiF₆ (aq)      aq      −2331                NH₄F             s       −465
```

---

## B.2 Reactions

```
Reaction                                          ΔH (kJ per formula unit)    Per Si or Ti
───────────────────────────────────────────────────────────────────────────────────────────────
Si₃N₄ + 12 F → 3 SiF₄ + 2 N₂                      −5050                       −1680 per Si
SiO₂ + 4 F → SiF₄ + O₂                             −1020                       −1020 per Si
TiN + 4 F → TiF₄(s) + ½ N₂                         −1630                       product involatile
TiN + 4 Cl → TiCl₄(g) + ½ N₂                       (strongly exothermic)       product volatile above ≈ 136 °C
SiO₂ + 6 HF → H₂SiF₆ + 2 H₂O                       (spontaneous in solution)   the dip-out
```

The fluorination of nitride gives up 65% more energy per silicon atom than that of oxide because of the N≡N bond (945 kJ/mol); that is the origin of the SiN:SiO₂ selectivity of bare fluorine chemistry.

---

## B.3 Bond and Product Data

```
Bond (diatomic dissociation energies, kJ/mol):
  Si–N 470;  Si–O 800;  Si–F 565;  N≡N 945;  C–F 485;  H–F 566;  Ti–N 480;  Ti–F 570

Product volatility:
  SiF₄       b.p. −86 °C                gas at any wafer temperature
  HCN        b.p. 26 °C                  forms from N + C + H at the surface; toxic
  (CN)₂      b.p. −21 °C
  TiF₄       sublimes 284 °C             involatile at 20–80 °C (passivation)
  TiCl₄      b.p. 136 °C                 volatile (Cl chemistry excluded)
  NH₄F, (NH₄)₂SiF₆   solids; sublime ≈ 100 °C under vacuum  (residues in NH₃/F chemistries)
```

---

## B.4 Polymer-Film Model Parameters (Chapter 3)

```
Model:   ER_m = R⁰_m(E) · exp(−d_m/λ);   d_m = (1 − c_m) d₀;   R⁰_m(E) ∝ √E − √E_th,m

Parameter                       SiN       SiO₂      TiN       ACL
─────────────────────────────────────────────────────────────────────────
Polymer consumption c_m         0.40      0.65      0.00      0.30
Threshold E_th (eV)             12        20        45        60
Bare rate at 400 eV (nm/min)    1730      493       23        810
Film d_m at d₀ = 3.4 nm (nm)    2.04      1.19      3.40      2.38
Steady rate (nm/min)            222–225   148       0.75–0.77 75

λ = 1.0 nm;   v_d = 0.4 nm/s;   τ = d₀/v_d = 8.5 s
Temperature:  d₀ ∝ exp[(E_s/k)(1/T − 1/T_ref)],  E_s = 0.08 eV,  T_ref = 40 °C
Transient:    L_trans = (R⁰ λ/v_d)[e^(−d_f/λ) − e^(−d₀/λ)];   R⁰_TiN λ/v_d = 0.96 nm
Pulsing:      f(D) = D + β(1 − D);  β = 0 (TiN), 0.25 (SiN, SiO₂), 0.40 (ACL)
```

---

## B.5 Radical and Ion Transport (Chapters 7, 9, 13, 14)

```
Knudsen diffusion in a tube of radius r:    D_K = (2r/3) v̄,    v̄ = (8kT/πm)^½
Attenuation length with wall loss s:        λ = r (4/(3s))^½ = 1.155 r / √s
Slit of width h (pillar gap):               D_K = (2h/3) v̄;  k_w = (s v̄/4)(2/h)

  F atoms:  v̄ = 606 m/s at 330 K;  s = 0.02 on TiN in a 17 nm slit  → λ = 139 nm
  Column (r = 22.5 nm):   s       0.002    0.005    0.02     0.05
                          λ (nm)  581      368      184      116
                          dose at 120 nm / top:  81%  72%  52%  36%
                          dose at 770 nm / top:  27%  12%  1.5% 0.13%

  HCN escape time from a 770 nm column:  L²/D_K = 78 ns  (v̄ = 509 m/s)

Ion angular spread:   θ₁/e = atan(√(T_i/E)),  T_i = 0.2 eV
  35 eV: 4.32°;  100 eV: 2.56°;  400 eV: 1.28°;  600 eV: 1.05°;  800 eV: 0.91°
  Fraction reaching the bottom of a column (acceptance 1.67°):   35 eV 14%;  100 eV 35%;  400 eV 82%
  S2 cavity (aperture 25 nm half-width, 650 nm):  acceptance 2.2°; 35 eV 23%;  100 eV 52%;  400 eV 95%
```

---

## B.6 Plasma and Sheath (Chapter 5)

```
Electron temperature 3 eV; ion density 10¹¹ cm⁻³
  Debye length            λ_D = 7430 √(T_e/n) m = 41 µm
  Sheath at 1000 V        s ≈ 1.2 λ_D (2V/T_e)^¾ = 6.4 mm;  at 400 V: 3.3 mm
  Ion transit time (Ar⁺)  τ_i = 3 s √(m/2eV) = 280 ns (1000 V), 222 ns (400 V)
  τ_i/τ_RF:               60 MHz 18.6;  2 MHz 0.6;  400 kHz 0.12
Ion flux Γ_i = 5 × 10¹⁵ cm⁻² s⁻¹  →  J_i = 8.0 A/m²;  Ion current into a 317 nm² crescent: 2.5 fA
Pillar charging:  C ≈ 1 fF;  dV/dt = 2.5 V/s;  clamp (junction avalanche) ≈ 10 V; t_clamp = 3.9 s
```

---

## B.7 Wet Chemistry (Chapters 7, 14)

```
HF, 5 wt%, 25 °C:    SiO₂ + 2 HF₂⁻ + 2 H₃O⁺ → SiF₄ + 4 H₂O (and onward to H₂SiF₆)
  PE-TEOS 70;  BPSG 600;  PSG 300;  SiN 1.0;  SiCN 0.25;  SiBN 0.15;  TiN ≈ 0.05 nm/min
  HF consumption: 6 mol HF per mol SiO₂;  ≈ 85 volumes of 5% HF per volume of oxide

Hot H₃PO₄, 160 °C:   Si₃N₄ + 4 H₃PO₄ + 12 H₂O → 3 Si(OH)₄ + 4 (NH₄)H₂PO₄ (net)
  SiN 5 nm/min;  SiO₂ 0.05 nm/min;  TiN 0.8 nm/min;  silicon in the bath < 100 ppm

TiN surface:   TiN + F → TiFₓ skin (1.5 nm), dissolves in water and HF
               TiN + O → TiO₂/TiON, δ = 0.5 + 0.35 ln(1 + t/10 s) nm at 150 °C (× 1.4 at 250 °C)
```

---

## B.8 Electrostatics and Mechanics (Chapters 13, 14)

```
Pressure between plates:   p = ε₀ E²/2 = ε₀ (ΔV/g)²/2;   10 V across 17 nm → 1.5 MPa
Beam (pillar, diameter d, length L):   I = πd⁴/64;  EI = 1.21 × 10⁻²⁰ N·m² for 28 nm, E = 400 GPa
Deflection:   δ = c w L⁴/(EI),  c = 1/384 (fixed–fixed), 3/384 (intermediate), 5/384 (pinned–pinned)
Pull-in at δ = g/3:   V_pull² = (g/3)(4g²/9) / (c ε₀ d L⁴/(2EI))
  1b (L = 650 nm, d = 28 nm, g = 17 nm):   12.3 / 7.1 / 5.5 V
  1d (L = 600 nm, d = 23 nm, g = 14 nm):    8.1 / 4.7 / 3.6 V;   L = 700 nm: 5.9 / 3.4 / 2.6 V
Capillary pressure of water across 17 nm:  2γ/g = 8.5 MPa
Opening edge relaxation:   u = (1 + ν) σ a / E = 0.036 nm  (σ = 250 MPa, a = 25 nm, ν = 0.25, E = 220 GPa)
Stress concentration:      K_hole ≈ 2 (equibiaxial);  K_rough = 1 + 2√(a/ρ) = 2.4 (a = 1.5 nm, ρ = 3 nm)
```

---

**Appendix B Version:** 1.0  
**Last Updated:** 2026-10-05
