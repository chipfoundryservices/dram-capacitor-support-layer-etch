# Chapter 13: Charging, Electrostatics & Free-Standing Pillars in the Plasma

## Overview

A TiN pillar is a conductor connected to the world through one junction. When the plasma delivers ions to it, it charges, and it keeps charging until the junction can carry the current away. Three questions follow. How fast does a pillar charge, compared with everything the process does to the plasma on a microsecond timescale? What do the three-quarters of the pillars that face the plasma do to the quarter that do not? And what happens when the pillars are free-standing, as they are during the second nitride step of S2, and the potential difference between neighbours puts a pressure on them?

The answers correct two statements made earlier in this book. **Pulsing the bias at 10 kHz does not relieve pillar charging**, because a pillar charges over seconds, not microseconds. **The shape of the bias waveform does not change it either**, because the charge on a pillar is set by the ion current, not the sheath voltage. The chapter then shows that the charging is harmless to embedded pillars (S0 and S1) except as a junction stress that falls on the touched class, and **dangerous to free-standing pillars (S2)**: with a potential difference of 10 V between neighbours the pillars are past their pull-in voltage. The remedies are a lower ion flux in SN2 or a lattice in which every pillar is touched.

**Learning Objectives:**
- Compute the ion current into a crescent, and the time to charge a pillar to a clamped potential
- Explain why the touched and untouched classes charge differently
- Compare the time constants of the pillar, the oxide column floor, the sheath, and the pulse period
- Compute the electrostatic pressure between pillars and the deflection and pull-in voltage of a free-standing span
- Choose between a lower flux and an all-touched lattice for the S2 nitride step
- Estimate the local stress relaxation around an opening

---

## 13.1 The Pillar as a Floating Electrode

Each pillar is tied through its landing pad and storage-node contact to a cell junction in the substrate. With the access transistor off and the junction reverse-biased, the pillar is an isolated conductor with a capacitance of about 1 fF to its surroundings (Book #30, Chapter 3) and a small leakage to the substrate.

```
Charging of a pillar (reference, illustrative):
  Ion flux at the wafer                 Γ_i = 5 × 10¹⁵ cm⁻² s⁻¹  →  J_i = e Γ_i = 8.0 A/m²  (0.8 mA/cm²)
  Plasma-facing TiN of a touched pillar  the crescent top, 317 nm² (3.17 × 10⁻¹⁶ m²)
  Plasma-facing TiN of an untouched one  none (covered by the ACL)
  Ion current into a touched pillar     I = J_i × A_c = 2.5 fA
  Capacitance                           C ≈ 1 fF
  Charging rate                         dV/dt = I/C = 2.5 V/s
```

The electrons reaching the crescent are few: the crescent sits at the bottom of the 300 nm ACL aperture, 50 nm wide, and electrons arrive at all angles, while the ions are directed. The electron current is shadowed, and the pillar charges **positive**, as the floor of any shaded feature does.

### 13.1.1 The Clamp

A pillar cannot rise indefinitely. Its junction leaks, and above a few volts it breaks down in reverse:

```
Junction model (illustrative):
  Leakage conductance   G ≈ 0.1 fA/V (at the wafer temperature of 40 °C)
  Avalanche clamp       V_bd ≈ 10 V
  Equilibrium           V_eq = min(I/G, V_bd) = min(25 V, 10 V) = 10 V
  Time to reach 10 V    C V / I = 1 fF × 10 V / 2.5 fA = 3.9 s
```

A touched pillar reaches the clamp in about 4 s and sits there for the rest of the step. An untouched pillar has no ion current and stays near 0 V. **Neighbours of different classes are 10 V apart across a gap of 17 nm.**

---

## 13.2 What Pulsing and the Waveform Can and Cannot Do

### 13.2.1 The Time Constants

```
Timescales (illustrative):
  Sheath crossing by an ion                          0.28 µs
  RF period at 2 MHz                                 0.5 µs
  Bias pulse, 10 kHz, 80% duty: period / off-time    100 µs / 20 µs
  Plasma density decay in the afterglow              ≈ 60 µs
  Oxide column floor (≈ 1 aF) charging to 10 V        ≈ 1 ms
  Pillar (1 fF) charging to 10 V                     3.9 s
```

A pillar charges 4 × 10⁴ times more slowly than the pulse period. A 20 µs off-time lets the pillar's charge change by 2.5 fA × 20 µs = 5 × 10⁻²⁰ C, 0.05 mV. **Pulsing at 10 kHz does not discharge the pillar; it cannot, in 20 µs.** Statements in Chapters 5 and 6 that the afterglow lets "the floating pillar tops discharge" referred to the wrong object. What the afterglow does relieve is the charging of the oxide column floor and walls, with a capacitance a thousand times smaller, which Book #30 (Chapter 3, Section 3.6) identifies as the cause of column offset toward the pillars.

### 13.2.2 The Waveform

The charge on a pillar is the time integral of the ion current to its crescent, balanced by junction leakage. It depends on the ion flux and the area, not on the bias waveform. Wafer and pillars see the same RF bias: the pillar is part of the wafer. The potential difference between a touched and an untouched pillar is a DC difference set by their different currents. **A tailored waveform with a narrower distribution does not change it**, and the benefit assigned to it in Chapters 3, 5, and 6 was overstated. In this book the tailored waveform has no demonstrated benefit. S1 uses the sinusoidal 2 MHz bias for its nitride steps, and the waveform generator is an optional upgrade.

---

## 13.3 In S0 and S1: Embedded Pillars

### 13.3.1 No Deflection

The pillars stand in oxide. A potential difference of 10 V across 17 nm of PE-TEOS is a field of 5.9 MV/cm, below the 10 MV/cm breakdown of the oxide. There is no motion, and the oxide supports the field.

### 13.3.2 Junction Stress on the Touched Class

The touched pillars sit at the junction clamp for most of the 226 s of plasma. The current is that of the crescent:

```
Charge through the junction of a touched pillar, S1:    I × t = 2.5 fA × 226 s = 5.7 × 10⁻¹³ C
  Junction area (≈ 20 nm × 20 nm = 4 × 10⁻¹² cm²)       dose 0.14 C/cm²
  Current density at the clamp                           6 × 10⁻⁴ A/cm²  (avalanche, reverse bias)
```

This is a hot-carrier and avalanche stress on the storage-node junction of every touched cell, for the whole duration of the plasma exposure. Its effect is a degradation of the junction retention, with a possible tail, and it falls on the same sublattice as the TiN-top defects of Chapter 11. It is a second mechanism for the class signature and gives a second reason to shorten the time the pillars are exposed:

```
Junction stress dose (touched pillars), per route:
  S0   195 s × 2.5 fA = 4.9 × 10⁻¹³ C        (ref)
  S1   226 s × 2.5 fA = 5.7 × 10⁻¹³ C        1.16 × S0
  S2   (SN1 44 s + SN2 30 s) = 74 s            0.33 × S1    (layout D, normal flux)
```

---

## 13.4 In S2: Free-Standing Pillars

### 13.4.1 The Pressure

In S2 the upper oxide is gone before SN2. The pillars between the top and the middle support are free over 650 nm. A potential difference ΔV across the gap g of 17 nm gives an electrostatic pressure on the facing surfaces:

```
p = ε₀ E² / 2 = ε₀ (ΔV/g)² / 2
  ΔV = 10 V:   E = 5.9 × 10⁸ V/m,   p = 8.85 × 10⁻¹² × (5.9 × 10⁸)² / 2 = 1.5 MPa
```

For comparison, the capillary pressure of water across the same gap is 2γ/g = 8.5 MPa; this is not much smaller, and unlike the capillary force it is present throughout the plasma step.

### 13.4.2 The Beam

A pillar of 28 nm diameter, E = 400 GPa, has a second moment of area I = πd⁴/64 = 3.02 × 10⁻³² m⁴ and a flexural rigidity EI = 1.21 × 10⁻²⁰ N·m². Loaded along the 650 nm span by the pressure acting on its width d:

```
w = p · d = 1.5 × 10⁶ × 28 × 10⁻⁹ = 0.042 N/m
Deflection  δ = c · w L⁴/(EI),    c = 1/384 (fixed–fixed), 5/384 (pinned–pinned), 3/384 (intermediate)
  Fixed–fixed:  δ = 0.042 × (650 nm)⁴ / (384 × 1.21 × 10⁻²⁰) = 1.6 nm   (linear, before the gap closes)
```

The pillar passes through a nitride sheet 120 nm thick that is perforated and thin and holds it neither fully clamped nor freely pivoting, so the real condition lies between the two limits. The pressure rises as the gap closes, and at a critical voltage the beam is pulled in. For the beam with a gap-dependent load:

```
Pull-in at δ = g/3:    V_pull² = (g/3)(4g²/9) / (c ε₀ d L⁴ / 2EI)

  Boundary condition       c          V_pull (L = 650 nm)    V_pull (L = 400 nm)
  Fixed–fixed              1/384      12.3 V                 32.6 V
  Intermediate             3/384      7.1 V                  18.8 V
  Pinned–pinned            5/384      5.5 V                  14.6 V
```

### 13.4.3 Deflection versus Potential Difference

Solving the nonlinear balance between the electrostatic load and the beam:

```
Deflection of a free span (650 nm) at ΔV across the 17 nm gap (nm):
  ΔV (V)    Fixed–fixed    Intermediate    Pinned–pinned
  2         0.07           0.20            0.34
  4         0.27           0.88            1.61
  5         0.43           1.49            3.08
  7.5       1.06           pull-in         pull-in
  10        2.17           pull-in         pull-in
  12        4.19           pull-in         pull-in
```

The threshold of Book #30 (Chapter 10), that two neighbours deflecting by more than an eighth of the gap, 2.1 nm, do not stop but touch, is a conservative marker. By it, a ΔV of 10 V is **at the limit even for a fixed–fixed beam and beyond pull-in for any realistic boundary**. A touched pillar clamped at 10 V next to an untouched one collapses onto it.

### 13.4.4 Why S2 Is Different

In S1 the 10 V exists too. The difference is that the pillars are embedded. In S2 the 650 nm span is free during SN2, with the clamp at 10 V and a pull-in limit of 5.5–12.3 V. **The S2 nitride step cannot run at the ion flux of S1 on a lattice in which one pillar in four is untouched.**

---

## 13.5 Ways Out

### 13.5.1 Lower the Ion Flux

The charging potential is V_eq = min(I/G, V_bd). It falls below the clamp only when I/G < 10 V, which requires I < 1.0 fA, a flux of 40% or less. Reducing the ion flux while keeping the neutral flux slows the SN2 etch by less than the flux ratio, because a quarter of the nitride etch is neutral-driven (Chapter 6, β = 0.25):

```
SN2 in S2 at flux fraction φ (rate factor = 0.25 + 0.75 φ):
  φ        I (fA)   V_eq (V)    Deflection (intermediate)   SN2 time (s, incl. 4 s flash)
  1.0      2.54     10          pull-in                     30.4
  0.5      1.27     10          pull-in                     46.2
  0.3      0.76     7.6         pull-in                     59.6
  0.16     0.41     4.1         0.9 nm (margin to 2.1 nm: 2.3×)   75.4
  0.12     0.30     3.0         0.5 nm                      —
```

A flux of 16% brings V_eq to 4 V, keeps the intermediate boundary 2.3 times inside the eighth-gap limit, and costs 45 s in SN2 relative to the full-flux step. This is route **S2A** (layout A, reduced flux): SN1 44 s + SN2 75 s = 119 s of plasma. The TiN loss in SN2 falls with the flux (0.16 nm against 0.36 nm), and the junction stress dose of the touched class falls with it.

### 13.5.2 Touch Every Pillar

If every pillar faces an opening, every pillar carries the same ion current and sits at the same potential. The potential difference is the mismatch among nominally equal crescents (overlay and CD vary the exposed area by ± 15% at 3σ, and so the current):

```
Layout D (50 nm on the 78 nm rotated lattice; every pillar touched once):
  Current mismatch ± 15% (3σ)  →  V_eq difference ≈ ± 1.5 V at the clamp (junction slope)
  Deflection at 1.5 V (intermediate boundary):  0.1 nm
```

This is route **S2D**. Its cost is the lattice: the rotated, finer lattice needs EUV or a double pattern (Chapter 4), the solid fraction falls to 34%, and the lattice has no two-class pattern, with every pillar carrying the TiN loss. The normal flux and the 4 s flash give SN2 30.4 s, and the plasma 74 s in total.

```
S2 variants:                     S2A (layout A, 16% flux)     S2D (layout D, full flux)
  Lithography                    ArF-i single exposure        EUV or double pattern
  Plasma time                    119 s                        74 s
  ΔV between neighbours          4.1 V                        ≈ ± 1.5 V
  Deflection (intermediate)      0.9 nm                       0.1 nm
  Margin to the 2.1 nm limit     2.3×                         21×
  Pillars touched                75%                          100%
  Solid fraction (top support)   39%                          34%
```

S2D is the more robust and the more expensive route; S2A is the route available to a fab with single-exposure ArF immersion.

### 13.5.3 What Does Not Work

```
Bias pulsing (10 kHz, any duty)        pillar time constant 3.9 s: no effect
Tailored waveform                      charge set by ion current: no effect
Higher ion energy (600 eV in SN2)      same current: no effect on charging; does raise the TiN rate
Shorter SN2                            the pillar charges to the clamp in 3.9 s; a 30 s step does not escape it
```

---

## 13.6 Stress Release at the Opening

Chapter 2 asserted that perforating a stressed film moves pillars by far less than a nanometre. The estimate: a circular opening of radius a = 25 nm in a film under equibiaxial tension σ = 250 MPa, modulus E = 220 GPa, Poisson ratio 0.25, relaxes elastically at its edge by

```
u = (1 + ν) σ a / E = 1.25 × 250 × 10⁶ × 25 × 10⁻⁹ / (220 × 10⁹) = 3.6 × 10⁻¹¹ m = 0.036 nm
```

The displacement of the hole edge is 0.04 nm and decays as the square of the distance from the hole, so the displacement of a pillar 26 nm from the centre is smaller still. **The local stress release of the opening does not move the pillars.** The global relaxation of the whole sheet when the oxide is removed and the sheet is free is a different effect (Book #30, Chapter 11).

---

## Summary and Key Takeaways

1. **A touched pillar charges at 2.5 V/s.** 2.5 fA of ion current into 1 fF; it reaches the 10 V clamp in 3.9 s, and an untouched neighbour stays at 0 V.

2. **Pulsing does not relieve it.** A 20 µs off-time moves 0.05 mV; the pillar needs seconds. Pulsing helps the oxide column floor, a thousand times smaller in capacitance.

3. **The waveform does not matter.** The charge is set by the ion current, not by the sheath voltage, and the tailored waveform has no demonstrated benefit in this book.

4. **In S0 and S1 the cost is junction stress.** 0.14 C/cm² through the junction of every touched cell, on the same sublattice as the TiN defects.

5. **In S2 the pillars pull in.** 10 V across 17 nm is 1.5 MPa; the pull-in voltage of a 650 nm free span is 5.5–12.3 V.

6. **Two remedies.** A flux of 16% (S2A, 119 s of plasma, ΔV = 4 V) or a lattice that touches every pillar (S2D, 74 s, ΔV ≈ ± 1.5 V).

7. **Opening stress release is 0.04 nm.** It does not move pillars.

---

## Study Questions

1. Compute the ion current into a crescent for a flux of 3 × 10¹⁵ cm⁻² s⁻¹. How long does a pillar of 1.2 fF take to reach the clamp of 10 V?

2. A pillar with G = 0.4 fA/V and I = 2.5 fA: what is its equilibrium potential? Does the clamp matter?

3. Compute the electrostatic pressure for ΔV = 6 V across a 15 nm gap, and the linear fixed–fixed deflection of a 28 nm pillar of span 650 nm.

4. Find the pull-in voltage (intermediate boundary) for a span of 500 nm and for a pillar of 24 nm diameter. Use V_pull ∝ √(EI/(d L⁴)) from Section 13.4.2 and the values in the table.

5. For S2A the flux is reduced to 20%. Compute V_eq, the SN2 time (with a 4 s flash), and the plasma time. Does the intermediate deflection stay inside 2.1 nm?

6. A fab wants to use the S2A route at full flux for 10 s only (the TiN transient). The pillar charges to 10 V in 3.9 s. Explain why a short step does not avoid pull-in, and what duration would keep V below 4 V.

---

**Next Chapter:** [Chapter 14: Advanced Schemes — Sequential Opens, Three-Support Molds, HF-Resistant Supports, Pre-Opened Lattices, 4F² & 3D DRAM](./14-advanced-multi-support-schemes.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
