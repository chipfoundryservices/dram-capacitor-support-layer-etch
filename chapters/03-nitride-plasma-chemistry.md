# Chapter 3: Plasma Chemistry of Nitride Etching Between Metal Pillars

## Overview

Silicon nitride is among the easiest films in the fab to etch and one of the hardest to etch *selectively*. Fluorine attacks it faster than it attacks oxide, at room temperature, with no ion help. In a plasma the same fluorine makes the nitride etch indifferent to what is next to it. The support layer etch needs the opposite: it must cut nitride at 225 nm/min while a titanium nitride surface a few nanometres away loses less than a nanometre per minute, and it must stop on oxide below.

This chapter builds a model of that selectivity from three ingredients: the thermochemistry that says which products leave and which stay, the hydrofluorocarbon (HFC) chemistry that puts a protective film on every surface, and the way that film is consumed differently by nitride, oxide, and titanium nitride. The model reproduces the numbers of Book #30's recipe, shows why ion energy is a weak lever, and shows that most of the TiN lost in a nitride step is lost in its first nine seconds. The remedy is a polymer flash before the etch begins. It is the central change that distinguishes S1 from S0.

**Learning Objectives:**
- Compare the thermochemistry of fluorine attack on Si₃N₄, SiO₂, and TiN, and name the product that passivates TiN
- Explain how hydrogen in the HFC gas turns nitrogen into volatile HCN and why oxide behaves differently
- Use the polymer-consumption model to compute rates and selectivities from a film thickness
- Show that ion energy and ion-energy distribution width are weak levers on SiN:TiN selectivity
- Compute the time-resolved TiN loss with and without a polymer flash
- Compute the SN2 rate in a column from its aspect ratio

---

## 3.1 Bonds, Products, and the Volatility Rule

### 3.1.1 Fluorine on Three Films

An etch needs a product that leaves. The thermodynamic drive to form it matters less than whether it is a gas at the wafer temperature and the process pressure.

```
Fluorination, per formula unit (ΔH from standard enthalpies of formation,
illustrative; atomic F as the reactant):

  Si₃N₄ + 12 F → 3 SiF₄(g) + 2 N₂(g)       ΔH ≈ −5050 kJ   (−1680 per Si)
  SiO₂  +  4 F →   SiF₄(g) +  O₂(g)         ΔH ≈ −1020 kJ   (−1020 per Si)
  TiN   +  4 F →   TiF₄(s) + ½N₂(g)         ΔH ≈ −1630 kJ

Products:
  SiF₄    b.p. −86 °C             gas at any wafer temperature
  N₂      gas
  TiF₄    sublimes at 284 °C      involatile at 20–80 °C: remains as a film
```

Two facts follow. First, nitride gives up much more energy per silicon atom than oxide does (1680 against 1020 kJ), because forming the N≡N bond of nitrogen (945 kJ/mol) pays for the cost of breaking Si–N. A fluorine-rich plasma with no polymer therefore etches nitride faster than oxide, and the SiN:SiO₂ selectivity of bare fluorine chemistry is greater than one. Second, TiN reacts just as strongly as the others, but its product is a solid. **Fluorine does not etch TiN. It passivates it.** A TiF₄/TiNₓFᵧ skin forms, 1–2 nm thick, and removal requires ions to sputter it.

### 3.1.2 Why Chlorine Is Out

```
TiN + 4 Cl → TiCl₄(g) + ½N₂     TiCl₄ b.p. 136 °C: volatile at 60–100 °C
```

Chlorine forms a volatile titanium product and etches TiN readily. Any chlorine-containing chemistry, including the BCl₃ and Cl₂ that Book #33 uses for ZrO₂, is excluded from the support layer etch. The same exclusion applies to bromine (TiBr₄ b.p. 233 °C is volatile at modest wafer temperatures). The support-layer chemistry is fluorine, hydrogen, carbon, nitrogen, and oxygen only.

---

## 3.2 Hydrofluorocarbon Chemistry for Nitride

### 3.2.1 What the Gases Do

```
Gas       H/F ratio   Role in the nitride step
─────────────────────────────────────────────────────────────────────────────────
CF₄       0           fluorine source; no hydrogen; polymer-lean
CHF₃      0.33        moderate polymer; the usual oxide etch gas
CH₂F₂     1.0         polymer-forming; hydrogen scavenges F as HF
CH₃F      3.0         heavy polymer; best for nitride:oxide selectivity
C₄F₆      0           heavy polymer without hydrogen (OX step)
O₂        —           removes polymer and carbon; sets the polymer thickness
Ar        —           ion source, dilution
```

Hydrogen does three things in a nitride etch:

1. **It removes nitrogen.** Nitrogen from the film leaves as HCN (b.p. 26 °C) and as CN radicals and cyanogen, in addition to N₂. These products form readily on a surface rich in carbon and hydrogen, which is why nitride etches well in HFC plasmas that deposit polymer.
2. **It scavenges fluorine.** HF formed in the gas lowers the F/C ratio of the polymer precursors, which makes the film heavier. A heavy film protects every surface it covers.
3. **It tilts oxide toward polymer.** On oxide, the film is consumed by oxygen from the substrate and the etch proceeds under a thin layer. That consumption is weaker than the nitrogen-and-hydrogen reaction on nitride (Section 3.3), so nitride etches faster than oxide.

### 3.2.2 Reference Recipes

```
Support layer etch recipes, nitride steps (CCP, 60 MHz source / 2 MHz bias; illustrative):

                         SN1 / SN2 (S0)         SN1 / SN2 (S1)         FLASH (S1)
  Gases (sccm)           CH₂F₂ 20, CF₄ 25,      CH₂F₂ 20, CF₄ 25,      CH₃F 40, Ar 300
                         O₂ 18, Ar 300          O₂ 18, Ar 300
  Pressure               25 mTorr               25 mTorr               20 mTorr
  Source power           1.8 kW                 1.8 kW                 0.6 kW
  Bias                   2 MHz, 1.4 kW          tailored waveform      none
                         (≈ 400 eV, broad)      (≈ 400 eV, ± 15%)
  Wafer temperature      40 °C                  40 °C                  40 °C
  Time                   SN1 40 s, SN2 20 s     SN1 40 s, SN2 20 s     4 s before each
  SiN rate               ≈ 225 nm/min           ≈ 225 nm/min           —
  Polymer on TiN         3.4 nm steady state    3.4 nm steady state    1.6 nm in 4 s
```

SN1 and SN2 are the nitride steps of Book #30's recipe. The tailored waveform and the flash are what S1 adds.

### 3.2.3 Effluent

The products of a nitride etch include HCN and cyanogen in the exhaust, at concentrations of tens of ppm in the foreline. They require point-of-use abatement (Chapter 5), and the chamber's gas panel, pump, and interlocks must be rated for them.

---

## 3.3 The Polymer-Film Model

### 3.3.1 Assumptions

Every surface in an HFC plasma carries a film of fluorocarbon polymer. Its thickness sets how much of the ion energy and radical flux reaches the substrate. Take:

```
Model (all rates in nm/min unless stated):
  1. A surface of material m carries a polymer film of thickness d_m.
  2. The etch rate falls exponentially with the film:
         ER_m = R⁰_m(E) · exp(−d_m / λ)             λ = 1.0 nm
     where R⁰_m(E) is the bare-surface rate at ion energy E.
  3. The film is partly consumed by the substrate chemistry. A fraction c_m of
     the arriving polymer flux is consumed:
         d_m = (1 − c_m) · d₀                        d₀ = film on a non-consuming surface
  4. Bare rate follows an ion-assisted threshold form:
         R⁰_m(E) ∝ √E − √E_th,m
```

Parameters, calibrated to Book #30's SN chemistry (225 nm/min on SiN, SiN:SiO₂ = 1.5, TiN pillar-top loss of about 2.4 nm over the two nitride steps):

```
Material         c_m     E_th (eV)   Bare rate at 400 eV    Film d_m (d₀ = 3.4 nm)
────────────────────────────────────────────────────────────────────────────────────
SiN              0.40    12          1730 nm/min            2.04 nm
SiO₂             0.65    20           493 nm/min            1.19 nm
TiN              0.00    45            23 nm/min            3.40 nm
```

The consumption fractions encode the chemistry of Section 3.2.1. TiN consumes none of the polymer: it has no oxygen to release and no nitrogen to take hydrogen. Nitride consumes 40% by forming HCN; oxide consumes 65% through oxygen release. Film on TiN is therefore the thickest, 3.4 nm, and film on oxide the thinnest, 1.2 nm, which matches the observation of Book #30 (Chapter 3) that a steady film of 2–4 nm protects the pillar tops.

### 3.3.2 Rates and Selectivities

```
Steady-state rates in the SN step (E from 200 to 600 eV, flat distribution):
  SiN   1730 × 0.130 = 222 nm/min
  SiO₂   493 × 0.300 = 148 nm/min
  TiN     23 × 0.033 = 0.75 nm/min

  SiN:SiO₂ = 1.50       SiN:TiN (steady) = 294
```

How the selectivity responds to the polymer thickness, with the same ion energy:

```
d₀ (on TiN)   d_SiN    d_SiO₂   SiN rate   SiO₂ rate   TiN rate   SiN:TiN   SiN:SiO₂
                                (nm/min)   (nm/min)    (nm/min)
  2.0 nm      1.20     0.70     514        241         3.06       168       2.13
  2.5         1.50     0.88     381        203         1.86       205       1.88
  3.0         1.80     1.05     282        170         1.13       251       1.66
  3.4         2.04     1.19     222        148         0.755      294       1.50   ← SN
  4.0         2.40     1.40     155        120         0.414      374       1.29
  4.5         2.70     1.57     115        101         0.251      457       1.14
  5.0         3.00     1.75      85         84         0.152      558       1.01
  6.0         3.60     2.10      47         60         0.056      832       0.78
```

Increasing the polymer improves SiN:TiN, but at the price of the SiN rate and the SiN:SiO₂ selectivity. The relationships are exponential:

```
S(SiN:TiN) = S⁰ · exp(+c_SiN · d₀/λ)         rises as exp(0.40 d₀)
SiN rate   ∝ exp(−(1 − c_SiN) · d₀/λ)         falls as exp(−0.60 d₀)
```

Each 10% of SiN rate given up buys about 7% of SiN:TiN. The trade is poor, and a more polymer-rich recipe is not the way to a better selectivity. It is also what turns the SN step into a source of etch-stop and residue (Chapter 12): at d₀ = 6 nm the oxide etches faster than the nitride.

---

## 3.4 Ion Energy and Its Distribution

### 3.4.1 Selectivity versus Energy

The threshold form makes the TiN rate fall faster than the SiN rate as ion energy is lowered, because TiN has the higher threshold:

```
Steady-state rates and SiN:TiN versus mean ion energy (d₀ = 3.4 nm, continuous bias):
  Mean E    Distribution ±50% (2 MHz)       Distribution ±15% (tailored)
  (eV)      SiN      TiN      S             SiN      TiN      S
  100       87       0.184    476           89       0.190    468
  150       118      0.312    377           119      0.319    374
  200       143      0.420    341           145      0.429    339
  300       186      0.602    309           188      0.612    308
  400       222      0.755    294           225      0.766    293
  500       254      0.890    285           257      0.903    285
  600       283      1.012    279           286      1.026    279
```

Two conclusions:

1. **Energy is a weak lever.** Halving the mean energy from 400 to 200 eV raises the steady SiN:TiN by 16% (294 to 341) and costs 36% of the SiN rate. Going to 100 eV gains 60% in selectivity at a loss of 61% of the rate.
2. **The width of the distribution does not matter for TiN.** The TiN threshold (45 eV) lies below the whole range of ion energies in this process, so tails above the mean do not add disproportionately to TiN loss. A tailored waveform with a narrow distribution gives the same selectivity as a broad one. Its benefit lies elsewhere: a smaller voltage swing on the floating pillars (Chapters 6 and 13).

This is a result of the model's threshold assumptions. A TiN with a higher effective threshold (heavily fluorinated, 80–100 eV) would make the energy lever steeper, and Chapter 6 treats the uncertainty.

### 3.4.2 Temperature

Polymer sticking falls with wafer temperature, which thins the film on every surface:

```
Polymer film d₀ ∝ exp[(E_s/k)(1/T − 1/T_ref)],  E_s = 0.08 eV, T_ref = 40 °C

  Wafer T   d₀ (TiN)   SiN rate   TiN rate   SiN:TiN   SiN:SiO₂
  10 °C     4.65 nm    105        0.215      486       1.1
  20 °C     4.16       141        0.352      399       1.24
  40 °C     3.40       222        0.755      294       1.50   ← reference
  60 °C     2.85       310        1.314      236       1.72
  80 °C     2.43       397        1.991      200       1.91
```

A wafer that runs 20 K warmer etches 40% faster, loses 74% more TiN per minute, and gives a lower SiN:TiN. It also etches nitride more selectively against oxide. Temperature is a stronger lever than energy, which is why the chuck is held to ± 1 K and why wafer temperature during the first seconds of a step (Chapter 6) matters.

---

## 3.5 The Transient: Where the TiN Is Lost

### 3.5.1 A Film That Takes Time to Grow

At the start of a step, the TiN surface carries no polymer. It builds at the polymer arrival rate, v_d = 0.4 nm/s, and takes τ = d₀/v_d = 8.5 s to reach 3.4 nm. During that time the TiN etches at a rate that falls as the film grows:

```
Loss during the build-up (t ≤ τ), polymer pre-deposited for t_f seconds before the bias:
  d_f = v_d · t_f
  L(t) = (R⁰_TiN λ / v_d) · [exp(−d_f/λ) − exp(−(d_f + v_d t)/λ)]
  τ = (d₀ − d_f)/v_d

After the build-up:
  L(t) = L_trans + R_ss · (t − τ)
  L_trans = (R⁰_TiN λ / v_d) · [exp(−d_f/λ) − exp(−d₀/λ)]
  R⁰_TiN λ / v_d = (23/60 nm/s)(1.0 nm)/(0.4 nm/s) = 0.96 nm
```

Without a flash, the transient costs 0.91 nm. The steady rate then adds 0.75 nm/min.

### 3.5.2 Time-Resolved Loss

```
TiN pillar-top loss versus time in the nitride step (nm):
  Time (s)    S0 (no flash)    S1 (4 s flash)
  1           0.31             0.06
  2           0.52             0.11
  4           0.75             0.15
  6           0.86             0.18
  8.5         0.91             0.21
  12          0.96             0.26
  20          1.06             0.36
  40          1.31             0.61
```

In the first 8.5 s, S0 loses 0.91 nm, which is 70% of the loss in a 40 s step and 86% in a 20 s step. Over the two nitride steps of a recipe (SN1 40 s, SN2 20 s), 77% of the TiN loss is paid in the two start-up transients:

```
S0:  SN1 1.31 nm + SN2 1.06 nm = 2.36 nm   (Book #30 states 2.5 nm)
S1:  SN1 0.61 nm + SN2 0.36 nm = 0.97 nm
```

### 3.5.3 The Flash

A short polymer deposition before the bias starts, in CH₃F/Ar with no ion energy (Section 3.2.2), builds film on the TiN without sputtering it:

```
Flash duration   Film built   Transient loss   Loss in a 20 s step
  0 s            0 nm         0.93 nm          1.07 nm
  2 s            0.8 nm       0.40 nm          0.57 nm
  4 s            1.6 nm       0.16 nm          0.36 nm
  6 s            2.4 nm       0.05 nm          0.28 nm
  8 s            3.2 nm       0.01 nm          0.26 nm
```

Four seconds removes 83% of the transient. Longer flashes buy less and cost wafer time at 4 s per step. The flash also deposits polymer on the nitride, which delays the nitride etch by a fraction of a second; the step times in S1 are specified for the flash plus the etch.

### 3.5.4 The Lesson

At steady state, the SiN:TiN selectivity is 294. Averaged over a real step it is lower, because the film must first grow:

```
Integral selectivity = nitride cleared (with overetch) / TiN lost
  SN1 + SN2 nitride cleared: 120 × 1.25 + 50 × 1.4 = 220 nm
  S0:  220 / 2.36 = 93
  S1:  220 / 0.97 = 226
```

The effective selectivity of S0 is therefore about 93. The 90 that follows from Book #30's pillar-top loss of 2.5 nm over about 220 nm of nitride is the same number; the "≈ 15" in the chemistry table of Book #30's Section 3.2.3 is a coupon-level ratio for a thin blanket film and is not the number that sets pillar-top loss. This book uses the integral selectivity, and the steady-state value only when stated.

---

## 3.6 Landing on Oxide; ARDE in the Column

### 3.6.1 SN1: Landing on the Upper Oxide

SN1 stops on PE-TEOS at SiN:SiO₂ = 1.5. The overetch of 25% (8 s) cuts the oxide by

```
Oxide loss in the SN1 overetch = (8 s / 60)(148 nm/min) = 20 nm
```

That is harmless in S0 and S1, where the OX step follows and deepens the column anyway, and in S2, where HF removes the oxide. It sets the first limit on the overetch: the selectivity to oxide at the landing is low (1.5), and a 25% overetch already costs 20 nm of oxide, which at the column wall means a 20 nm deeper start for the OX step and a slightly different profile at the nitride-oxide interface (Chapter 10).

### 3.6.2 SN2: Aspect Ratio and the Rate

SN2 cuts the middle support at the bottom of a column 770 nm deep. The rate falls with the aspect ratio A of the column:

```
ER/ER₀ = 1 / (1 + k·A),    k = 0.02   (Book #29's form, Book #30's value)
A = depth / width:   SN1 (A = 2.4):          0.95
                     SN2 in S0/S1 (A = 17):  0.75  →  200 → 150 nm/min
                     SN2 in S2 (cavity, A = 13):  0.79  →  200 → 159 nm/min
```

At A = 17, SN2 is a quarter slower than the same chemistry at the top of the column. It is also where the soft interface (Chapter 2) and the SiN:SiO₂ of 1.5 combine.

```
Landing and overetch of the middle support:
  S0/S1:  50 nm at 150 nm/min clears in 20 s. The 40% overetch (20 nm of nitride
          equivalent) is supplied by the first seconds of LAND, in which nitride
          etches at one-sixth of the BPSG rate: 25 s × (290/6 ≈ 48 nm/min) = 20 nm.
          The same seconds etch 100–120 nm of BPSG (the landing depth).
  S2:     there is no LAND. SN2 carries its own overetch:
          50 nm × 1.4 / 159 nm/min = 26.4 s, plus the 4 s flash.
```

SN2 is where a nitride sliver can survive: the oxide-free corner at the crescent has no escape path for products, and the nitride has soft ends. Chapter 12 develops the corner geometry and the statistics of what is left.

---

## 3.7 Chemistries Beyond the HFC Step

```
Chemistry                      Strength                     Weakness
─────────────────────────────────────────────────────────────────────────────────────────
HFC + O₂, ion-assisted (S0/S1) Anisotropic; selective to    Polymer: residue, wetting (Ch. 9);
                               TiN with a polymer film      TiN transient (§3.5)
Cl-containing                  none here                    TiCl₄ volatile: TiN etches
NF₃/O₂ or NF₃/H₂ remote        Isotropic, no ions, no       No profile control; trims
                               TiN sputtering; high         and finishes only (Ch. 7)
                               SiN:SiO₂ (≈ 10–20)
Plasma ALE of SiN              Self-limiting; ≤ 0.5 nm      Slow; hard to run in a 50 nm
(CHF₃ adsorption, Ar⁺)         TiN loss                     column (Ch. 7)
Hot H₃PO₄ (wet)               Selective to oxide           Isotropic; widens openings to
                                                            ligament failure; attacks TiN (Ch. 7)
```

---

## Summary and Key Takeaways

1. **Fluorine passivates TiN.** TiF₄ sublimes at 284 °C; at wafer temperatures it stays as a film. Chlorine and bromine are excluded because their titanium products are volatile.

2. **Polymer sets the selectivity.** A film consumed by oxygen (oxide, 65%) or by nitrogen and hydrogen (nitride, 40%) is thinner than the film on TiN (no consumption), so nitride etches and TiN does not.

3. **Steady selectivity is high; effective selectivity is not.** SiN:TiN is 294 at steady state and 93 over a real step in S0, because 77% of the TiN is lost in the first 8.5 s while the film grows.

4. **A 4 s flash removes 83% of the transient.** TiN loss in the two nitride steps drops from 2.36 to 0.97 nm; integral selectivity rises from 93 to 226.

5. **Energy and distribution width are weak levers; temperature is stronger.** Halving the energy gains 16% in selectivity at a cost of 36% in rate; 20 K warmer etches 40% faster and loses 74% more TiN per minute.

6. **SN2 is the hard landing.** At aspect ratio 17 the rate is 75% of the surface rate, the selectivity to oxide is 1.5, and the film has soft ends.

---

## Study Questions

1. Compute ΔH for the fluorination of Si₃N₄ to SiF₄ and N₂ per silicon atom, using ΔH_f(Si₃N₄) = −744, ΔH_f(SiF₄) = −1615, and ΔH_f(F) = +79 kJ/mol. Compare with SiO₂ and say what the difference predicts about bare-fluorine selectivity.

2. With the parameters of Section 3.3.1, compute the steady-state SiN:SiO₂ and SiN:TiN selectivities at d₀ = 4.0 nm, and the SiN rate. By what factor must the SN time grow to clear the same nitride?

3. Section 3.3.2 says a 10% sacrifice in SiN rate buys about 7% in SiN:TiN. Derive the relationship from the two exponentials.

4. A flash of 3 s precedes a step. What film does it build, and what is the transient loss? (Use the formula of Section 3.5.1.)

5. The wafer is 8 K warmer than intended during SN1 because of a chuck calibration drift. Estimate the change in SN1 time and in steady TiN loss rate, using the temperature table.

6. Use the ARDE form to compute the SN2 time for a middle support of 50 nm with a 40% overetch at A = 13 (S2) and at A = 17 (S0/S1), starting from ER₀ = 200 nm/min.

---

**Next Chapter:** [Chapter 4: Lattice Design, Pattern Transfer & Opening Statistics](./04-lattice-design-opening-statistics.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
