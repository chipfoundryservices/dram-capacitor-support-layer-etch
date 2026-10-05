# Appendix E: Lattice, Etch & Electrostatics Calculations

Closed-form models used in this book, with the reference worked example for each. All models are deliberately simple; each lists its main assumptions.

---

## E.1 Opening Count and Areas (Ch. 1, 4)

```
cells per die = bits;   cells per opening = A_cell(lattice) / A_cell;   openings = cells / cells per opening

Reference: 16 Gb = 16 × 2³⁰ = 1.718 × 10¹⁰ cells;  A_cell = 1734 nm²
  Opening lattice: hexagonal, pitch P = 90 nm → A = (√3/2) P² = 7015 nm² = 4.045 cells
  Openings per layer = 1.718 × 10¹⁰ / 4.045 = 4.25 × 10⁹;   per cm² of array 10¹⁴ / 7015 = 1.43 × 10¹⁰
  Open fraction = π D²/4 / A = 1963 / 7015 = 28.0%
  Array area per die = 1.718 × 10¹⁰ × 1734 nm² = 0.298 cm²
```

---

## E.2 Crescent and Clover Geometry (Ch. 1, 10, 11)

```
Lens area of two circles (radii r₁, r₂, centre distance d):
  A_lens = r₁² acos[(d² + r₁² − r₂²)/(2 d r₁)] + r₂² acos[(d² + r₂² − r₁²)/(2 d r₂)]
           − ½ √[(−d + r₁ + r₂)(d + r₁ − r₂)(d − r₁ + r₂)(d + r₁ + r₂)]

Top support (opening R = 25 nm, pillar r = 16 nm, d = 45/√3 = 26.0 nm):
  A_lens = 317 nm²;  overlap depth R + r − d = 15.0 nm
  Clover free area = π R² − 3 A_lens = 1963 − 951 = 1012 nm²  (1013 with unrounded d)
Middle support (R = 22 nm, r = 15 nm): A_lens = 194 nm² (3 → 582);  free area 1521 − 582 = 938 nm²
Inscribed free circle between three pillars:  2 (d − r) = 20 nm (top), 22 nm (middle)

Arc of the pillar surface inside the opening:
  cos φ = (d² + r² − R²)/(2 d r) = 0.369 → φ = 68.3°;  arc = 2 φ r = 38.2 nm (38% of the circumference)
```

---

## E.3 Pillars Touched (Ch. 1, 4)

```
A superlattice at twice the pillar pitch has 4 pillars per opening cell and each opening touches 3:
  fraction touched = 3/4 = 75%;  untouched 25%.   (With 4.045 cells per opening: 74.2%.)
Superlattice at √3 × pitch (rotated 30°): 3 pillars per cell, each touched once: 100%.
Superlattice at 3 × pitch: 9 pillars per cell, 3 touched: 33%.
```

---

## E.3a Solid Fraction (Ch. 4)

```
Solid = A − [n_pil π r² + π R² − 3 A_lens],   n_pil = A/A_cell
Reference top support: 7015 − [4.045 × 804 + 1963 − 951] = 7015 − 4264 = 2751 nm²  → 39.2%
```

---

## E.4 Overlap Depth with Overlay and CD Error (Ch. 4, 10)

```
overlap(3σ) = overlap₀ + √(δ² + (ΔCD/2)²) + tilt offset
  Top:    15 + √(5² + 1.25²) = 20.2 nm
  Middle: 11 + 5.2 + 770 nm × tan(0.3°) = 11 + 5.2 + 4.0 = 20.2 nm
Overlap depth distribution: N(15, 1.72) nm →  P(> 16 nm) = 28%;  P(> 18) = 4.0%;  P(> 20) = 0.18%
```

---

## E.5 HF Reach and Killer Clusters (Ch. 4)

```
Lateral reach (S0/S1):  R_crit(t) = R_open + (v t) / τ,   v = 70 nm/min,  τ = 1.74 (tortuosity)
  t = 105 s:  R_crit = 25 + 122.5/1.74 = 95.4 nm
Largest empty circle R_e for a cluster of k failed adjacent openings (enumerated):
  k = 1, 2, line of 3: 90.0;  triangle 103.9;  rhombus 119.1;  k = 5: 121.2;  k = 6: 137.5;  k = 7: 155.9
Killer clusters per die:  λ = N_sites × n_shapes × pᵏ   (n_shapes: triangle 2, rhombus 3, k = 6: 8, k = 7: 1)
  p_max = (λ / (N n))^(1/k):   105 s: 1.06 × 10⁻⁴;  120 s: 9.4 × 10⁻⁴;  150 s: 8.2 × 10⁻³;  180 s: 2.2 × 10⁻²   (λ = 0.01)
Dip time for a single failed opening:   (90 − 25) × 1.74 / 70 × 60 = 97 s
S2 (vertical path):  path = √(ρ² + h²),  h = 635 nm,  ρ = R_e − 25:   +0.5% (single), +2.1% (hexagon)
Killer-particle footprint (triangle):  2 × (P/√3 + R) = 154 nm;  yield: Y = exp(−D_k A_array)
Inspection area for 95% detection of one killer cluster:  A = −ln 0.05 / D_k = 150 cm² at 0.02/cm²
```

---

## E.6 Ligament Stress (Ch. 4, 14)

```
σ_net = σ P/(P − D_final);   σ_peak = σ_net × K_hole × K_rough;   K_rough = 1 + 2√(a/ρ)
Reference:  D_final = 50 + 3.6 = 53.6;  σ_net = 250 × 90/36.4 = 618 MPa;  K = 2 × 2.4;  σ_peak = 2.97 GPa
  Margin to 3.5 GPa = 1.18;  fracture margin 1.0 at D_final = 59.1 nm (etched 55.5 nm)
S2 (PSG upper oxide): SiN loses 4.71 nm per wall (both dips) → D_final 59.4 → margin 0.99
                      SiCN loses 1.18 nm per wall → D_final 52.4 → margin 1.22
```

---

## E.7 Polymer Model, Rates, and Selectivity (Ch. 3)

```
ER_m = R⁰_m(E) exp(−(1 − c_m) d₀/λ);   R⁰_m(E) = R⁰_m(400) (√E − √E_th)/(√400 − √E_th)
Flat distribution [E₁, E₂]: mean(√E − √E_th) = [(2/3)(E₂^1.5 − E₁^1.5) − √E_th (E₂ − E₁)]/(E₂ − E₁)

Reference (d₀ = 3.4 nm, E ∈ [200, 600] eV):
  SiN:  1730 × exp(−0.6 × 3.4) = 1730 × 0.130 = 222 nm/min
  SiO₂: 493 × exp(−0.35 × 3.4) = 493 × 0.300 = 148 nm/min
  TiN:  23 × exp(−3.4) = 23 × 0.0334 = 0.755 nm/min        SiN:TiN = 294;  SiN:SiO₂ = 1.50
Dependence on d₀:  SiN:TiN ∝ exp(0.40 d₀);  SiN rate ∝ exp(−0.60 d₀)
Temperature:  d₀(T) = 3.4 exp[(0.08 eV/k)(1/T − 1/313.15 K)];   20 K warmer: SiN +40%, TiN +74%
```

---

## E.8 TiN Transient and the Flash (Ch. 3, 6)

```
Film built in the flash:  d_f = v_d t_f   (v_d = 0.4 nm/s)
t ≤ τ:   L(t) = (R⁰ λ/v_d)[e^(−d_f/λ) − e^(−(d_f + v_d t)/λ)];   τ = (d₀ − d_f)/v_d
t > τ:   L(t) = L_trans + R_ss (t − τ);   L_trans = (R⁰ λ/v_d)[e^(−d_f/λ) − e^(−d₀/λ)];   R⁰λ/v_d = 0.96 nm
No flash:    L_trans = 0.91 nm,  τ = 8.5 s;   SN1 (40 s) 1.31;  SN2 (20 s) 1.06;  sum 2.36
4 s flash:   d_f = 1.6 nm,  L_trans = 0.16,  τ = 4.5 s;   SN1 0.61;  SN2 0.36;  sum 0.97
Integral selectivity = nitride cleared / TiN lost = 220 nm / 2.36 = 93 (S0);  220 / 0.97 = 226 (S1)
Gain: dL_trans/d(d_f) = −0.96 e^(−d_f) = −0.19 nm per nm of film at 1.6 nm
```

---

## E.9 Step Times, ARDE, and Mask Budget (Ch. 3, 5, 12)

```
ER/ER₀ = 1/(1 + kA), k = 0.02;  A = depth/width:  SN1 (2.4) 0.95;  SN2 S0/S1 (17) 0.75;  SN2 S2 (13) 0.79
SN2 time (S2): 50 × (1 + 0.40) / 159 × 60 = 26.4 s;   (S0/S1: 20 s, overetch supplied by LAND:
  25 s × 290/6 = 20 nm = 40% of 50 nm)
Mask (S0/S1):  120 × 1.25/3 + 650/5 + 50 × 1.4/3 + 100/5 + 30 = 50 + 130 + 23 + 20 + 30 = 253 nm
Mask (S2, SiCN, 220 nm):  120 × 1.25/(3 × 0.55) + 50 × 1.4/(3 × 0.55) + 30 = 91 + 42 + 30 = 163 nm
Throughput: wafers/h = 4 × 3600/(plasma + overhead);  S0 3600 × 4/369 = 39.0;  S1 4 × 3600/400 = 36.0
```

---

## E.10 Radical Attenuation and Ion Acceptance (Ch. 7, 9)

```
λ = 1.155 r/√s;   dose(z)/dose(0) = exp(−z/λ):    s = 0.005: λ = 368 nm, dose(770) = 12%
Ion half-angle θ₁/e = atan(√(T_i/E)); acceptance θ_a = atan(r/L)
Fraction transmitted = 1 − exp(−(θ_a/θ₁/e)²):
  column r = 22.5 nm, L = 770 nm: θ_a = 1.67°;  35 eV: 1 − exp(−0.151) = 14%;  400 eV: 82%
  S2 cavity r = 25 nm, L = 650 nm: θ_a = 2.2°;   35 eV: 23%
ALE at the middle support: B step = 3 s/0.139 = 21.6 s;  cycle 1.5 + 0.5 + 21.6 + 0.5 = 24 s;  1.2 nm/min
```

---

## E.11 Wetting and Strip Coverage (Ch. 9)

```
Cassie:   cos θ = φ cos θ_p + (1 − φ) cos θ_s   (θ_p = 110°, θ_s = 10°)
  φ for θ = 60°:  (cos 10° − 0.5)/(cos 10° − cos 110°) = 0.365;   φ for θ = 90°: 0.742
Strip:    φ(t) = exp(−[t_ion f_ion/τ_ion + t_rad f_rad/τ_rad]),  τ_ion = 3 s, τ_rad = 12 s
  radical only 50 s, f_rad = 12%:   φ = exp(−0.51) = 0.60
  10 s ion flush (f_ion = 35%) + 40 s radical (12%):   φ = exp(−1.17 − 0.41) = 0.21
Failure probability (σ_φ = 0.08, fail if φ > 0.61):  P = ½ erfc[(0.61 − μ)/(0.08 √2)]
  μ = 0.21: 2.9 × 10⁻⁷;  0.30: 5.3 × 10⁻⁵;  0.35: 5.8 × 10⁻⁴;  0.50: 8.5 × 10⁻²
Killer clusters from wetting:  2 N p³ = 2 × 4.25 × 10⁹ × (2.9 × 10⁻⁷)³ = 2 × 10⁻¹⁰;   (5.8 × 10⁻⁴)³ → 1.7
```

---

## E.12 Sliver Model (Ch. 12)

```
Rate relative to bulk near TiN:   f(x) = 1 − (1 − f₀) exp(−x/ℓ);   f₀ = 0.5, ℓ = 4 nm
Sliver width:   x_s = ℓ ln[(1 − f₀)/(1 − 1/(1 + OE))];     fin height:  h(0) = T [1 − (1 + OE) f₀]
  OE 40%: x_s = 4 ln(0.5/0.286) = 2.24 nm;  h(0) = 50 × (1 − 0.7) = 15 nm
  OE 25%: x_s = 3.67 nm;  h(0) = 19 nm  (T = 50);  45 nm (T = 120, top support)
Corner: cos α = (R² + r² − d²)/(2 R r) = 0.050, α = 87.1°;  nitride wedge 92.9°
Wedge area A ≈ w²/(2 tan 46.5°) = 0.48 w²
Gaussian tail:  z = (1.4 − 1)/0.0193 = 20.7  (not the source of not-open events)
```

---

## E.13 Charging and Electrostatics (Ch. 13)

```
Ion current:  I = e Γ_i A_c = 1.602 × 10⁻¹⁹ × 5 × 10¹⁹ m⁻² s⁻¹ × 3.17 × 10⁻¹⁶ m² = 2.54 fA
Charging:     dV/dt = I/C = 2.5 V/s;   V_eq = min(I/G, V_bd) = min(25 V, 10 V);  t = C V/I = 3.9 s
Pressure:     p = ε₀ (ΔV/g)²/2 = 1.5 MPa at 10 V, g = 17 nm
Deflection:   δ = c ε₀ d V² L⁴ / (2 EI (g − δ)²)  (solve iteratively; pull-in at δ = g/3)
Pull-in:      V_pull = 12.3 / 7.1 / 5.5 V (fixed / intermediate / pinned), L = 650 nm, d = 28 nm
S2A flux:     SN2 rate factor 0.25 + 0.75 φ_flux;  φ = 0.16: factor 0.37;  time 26.4/0.37 + 4 = 75 s (SiN, 400 eV)
Hole-edge relaxation:  u = (1 + ν) σ a/E = 1.25 × 250 × 10⁶ × 25 × 10⁻⁹ / (220 × 10⁹) = 0.036 nm
```

---

## E.14 The Opening in S2 (Ch. 10)

```
Lateral blur at height H:   σ_x = H tan(θ₁/e)/√2;   H = 650 nm
Dose across an aperture of width w:  D(x) = ½[erf((x + w/2)/(√2 σ_x)) − erf((x − w/2)/(√2 σ_x))]
Cleared width (dose ≥ 1/(1 + OE) = 0.714):   w_c = w − 2 δ,   δ = 0.4 √2 σ_x
  400 eV: σ_x = 10.3 nm, δ = 5.8 nm, w_c = 38.4 nm;   600 eV: 8.4, 4.7, 40.5;   800 eV: 7.3, 4.1, 41.8
```

---

## E.15 Capacitance Effects (Ch. 11, 14)

```
Top loss:   ΔC/C = (arc × loss) / (π d L) = 38.2 × 3.2 / (π × 28 × 1410) = 0.10%   (S0: 0.15%; S2: 0.03%)
Sidewall skin (S2):   ΔC/C = (f_diss/r) ∫₀ᴸ δ(z) dz / L_pillar;   δ(z) = 1.5 (1 − exp(−Φ₀ e^(−z/139 nm))) nm
  Φ₀ = 3–5, half dissolved:  0.9–1.1%;  all dissolved: 1.8–2.3%
Edge field:   FEF = (t/r)/ln(1 + t/r):  r = 6 nm, t = 5.5 nm: 1.41;  pillar wall r = 14 nm: 1.19
Seam exposure:  P = 10% (open) × 76% (trace in the crescent) = 7.6% of touched pillars
Class test:   z = (f_t − 0.75)/√(0.75 × 0.25/N);   N = 50: z = 3.6 at f_t = 0.97
```

---

## E.16 Equipment and Cost (Ch. 16)

```
Wafers per platform-year = wph × 8760 × 0.85;   platforms = starts per year / wafers per platform-year
  S0 39.0 → 290,600;  S1 36.0 → 268,100;  S2D 33.8 → 251,500;  S2A 29.3 → 218,500
  1.8 × 10⁶ starts per year: 6.2, 6.7, 7.2, 8.2 platforms → 7, 7, 8, 9
Depreciation per wafer = $6.0 M / 5 / wafers per platform-year:  S1 $4.48
Module cost:   S1: 7.3 + 6.0 + 4.2 = $17.5;   S2A: 8.2 + 10.5 + 8.4 + 0.5 = $27.6
Break-even yield gain = Δ cost / ($65 per % die yield):  S2A 0.16%;  S2D 0.60%
```

---

**Appendix E Version:** 1.0  
**Last Updated:** 2026-10-05
