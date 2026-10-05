# Chapter 6: Ion Energy, Bias Pulsing & Temperature — The Selectivity Levers

## Overview

Every recipe offers the same set of knobs: how hard to hit the wafer, whether to pulse, how warm to keep it, how much polymer to make, how long to wait. Engineers adjust them in this order of habit. The model of Chapter 3 allows the habit to be checked, and the result is not what habit expects. In the support layer etch, **once a polymer flash has been placed before each nitride step, the TiN loss is almost indifferent to every other lever**. Ion energy, distribution width, wafer temperature, polymer thickness, and duty cycle change the nitride rate, the mask consumption, the clearing time, and the throughput. They hardly change the TiN loss, which is set by the flash.

This chapter works through each lever with the model, states what each one buys, and ends with a sensitivity table at constant nitride cleared that tells an engineer where the process window is wide and where it is narrow. It also corrects an expectation: the tailored waveform, which an engineer reaches for first, has no benefit here.

**Learning Objectives:**
- Compute the effect of mean ion energy on rate, selectivity to TiN and ACL, step time, and mask use
- Explain why the width of the ion energy distribution does not change the selectivity here
- Model bias pulsing with a duty-dependent rate factor and choose the duty for a step
- Describe the wafer temperature through a recipe and the thermal role of the flash
- Read the sensitivity table, and identify the levers that matter for TiN loss and the ones that matter for rate

---

## 6.1 The Levers and What They Move

```
Lever                  Moves strongly                 Moves little
──────────────────────────────────────────────────────────────────────────────────
Polymer flash          TiN transient loss (−1.4 nm)   rate, mask
Mean ion energy        rate, step time, mask          TiN loss (with flash)
IEDF width             nothing                        rate (±1.5%), selectivity,
                                                      mask, charging (Ch. 13)
Pulse duty             rate (OX, SN), time,           TiN loss, pillar charging
                       oxide column charging
Wafer temperature      rate (2%/K), step time         TiN loss (with flash)
O₂ flow (film d₀)      rate (−3% per sccm)            TiN loss (with flash)
Number of steps in     TiN transients (one per step   —
  the route            without a flash)
```

The last row decides between routes (Chapter 14): S0 and S1 each have four plasma steps in contact with the pillar tops; S2 has two nitride steps and no others.

---

## 6.2 Ion Energy

### 6.2.1 What It Does to the Nitride Steps

The nitride steps are modelled with a 4 s flash and a distribution of ± 15% about the mean energy E (the result is the same for the ± 50% distribution of the sinusoidal bias to within 1.5%), with the times scaled to clear the same nitride:

```
Mean ion energy sweep (SN steps, S1 with 4 s flash; illustrative):
  Mean E   SiN rate   TiN rate   SiN:TiN    SiN:ACL   SN1    SN2    ACL used     TiN loss
  (eV)     (nm/min)   (nm/min)   (steady)             (s)    (s)    SN1+SN2      SN1+SN2
  150      119        0.319      374        4.34      75     38     51 nm        0.69 nm
  200      145        0.429      339        3.71      62     31     59           0.78
  250      168        0.525      320        3.41      54     27     65           0.85
  300      188        0.612      308        3.22      48     24     68           0.90
  400      225        0.766      293        3.00      40     20     73           0.97   ← S1
  500      257        0.903      285        2.88      35     17.5   77           1.04
```

The carbon mask is modelled with a threshold of 60 eV and 30% polymer consumption, calibrated to SiN:ACL = 3.0 at 400 eV (Book #30).

Moving from 400 to 200 eV gives a gain of 0.19 nm of TiN (0.97 to 0.78 nm), 14 nm of mask (73 to 59 nm), and a **55% longer** nitride etch (60 s to 93 s). The mask gain is useful: the ACL is the clock of the one-pass route (47 nm margin in S0 and S1), and the nitride steps use 73 of its 253 nm. The TiN gain is small, and the time penalty falls on a chamber that is already the throughput limit. S1 stays at 400 eV for the nitride steps.

### 6.2.2 The OX Step

The OX step runs at 600 eV because it must cut oxide at AR 20. Its selectivity to ACL (Ox:ACL ≈ 5) and to TiN (≈ 40) follow the same logic as the nitride steps and are treated in Book #30. The OX step is not tuned in this book.

---

## 6.3 The Width of the Distribution

### 6.3.1 A Negative Result

Chapters 3 and 5 introduced a tailored waveform that narrows the ion energy distribution from ± 50% to ± 15%. The model shows that it does not change the selectivity:

```
Rates at a mean energy of 400 eV (steady state):
                       Broad ± 50%    Narrow ± 15%    Difference
  SiN (nm/min)         222            225             +1.4%
  TiN (nm/min)         0.755          0.766           +1.5%
  SiN:TiN              294            293             0
```

The reason is the yield function. Rates follow √E − √E_th, which is concave in E, so a mean-preserving spread slightly *lowers* the average rate. The TiN threshold (45 eV) lies below the lower edge of either distribution (200 eV for the broad one), so there is no tail below it that the narrow distribution removes. The same argument applies to the carbon mask: the ACL threshold of 60 eV is far below 200 eV, and the facet erosion rate scales with the mean energy flux, not with the width.

### 6.3.2 What the Waveform Is For

Two effects might have justified it. The first is the **sheath voltage swing**: a sinusoidal bias at 2 MHz swings the sheath through about 1 kV peak to peak, and a tailored waveform holds it almost constant through the ion crossing. If the swing charged the pillars, the narrower waveform would help. It does not: the pillars are part of the wafer and see the same RF bias, and the potential difference between a touched and an untouched pillar is a DC difference set by their ion currents (Chapter 13). The second is the **ion angular spread** at the column bottom for ions at the low end of the distribution. At 200 eV and above it is below 2° and does not matter at aspect ratio 17.

The consequence is blunt. In this process the tailored waveform is neither a selectivity control, nor a mask control, nor a profile control, nor a charging control. A sinusoidal 2 MHz bias with a flash gives a TiN loss within 0.01 nm of the tailored one. **S1 does not use it.** It would be a different answer for a process in which the TiN threshold lies inside the distribution, or at much lower mean energies, and the model of Section 6.3.1 is the way to check.

---

## 6.4 Pulsing

### 6.4.1 A Model

Pulsing the bias at duty D keeps the plasma on and the ion energy off for the fraction 1 − D. During the off-phase the ion-driven part of each etch stops; the neutral-driven part continues:

```
Rate factor at duty D:   f(D) = D + β (1 − D)

  β = fraction of the CW rate that is neutral-driven:
    TiN    0       (only ions sputter the fluorinated skin)
    SiN    0.25    (F atoms etch nitride without ions)
    SiO₂   0.25    (calibrated: f(0.8) = 0.85 gives OX 110 → 129 s)
    ACL    0.40    (O radicals etch carbon)

Duty    SiN     TiN     SiN:TiN gain    OX      ACL
100%    1.000   1.000   1.00            1.000   1.000
 80%    0.850   0.800   1.06            0.850   0.880
 70%    0.775   0.700   1.11            0.775   0.820
 60%    0.700   0.600   1.17            0.700   0.760
 50%    0.625   0.500   1.25            0.625   0.700
 40%    0.550   0.400   1.38            0.550   0.640
```

Pulsing improves the steady selectivity by 6% at 80% duty and 25% at 50%, at the price of a proportional loss of rate: 15% for 80%, 37.5% for 50%. The rate loss lengthens the step, and a longer step adds its own steady TiN loss. In S1 with a flash the transient is gone and the steady term is small (Section 6.6), so the gain in selectivity is a gain on a small number.

### 6.4.2 Frequency

The pulse frequency sets the off-time. With plasma density decaying with a time constant of about 60 µs, an off-time must be short enough that the plasma does not extinguish before the next pulse:

```
10 kHz, 80% duty:    period 100 µs, off-time 20 µs; density at the end of the off-phase  e^(−20/60) = 0.72
 5 kHz, 80% duty:    off-time 40 µs;  e^(−40/60) = 0.51
 1 kHz, 80% duty:    off-time 200 µs; plasma essentially extinguished (0.04); re-ignition each pulse
```

At 10 kHz the plasma persists; it is the bias that is modulated. At 1 kHz each pulse re-ignites the plasma, with a voltage overshoot that is a large and non-reproducible ion-energy excursion. S1 pulses the OX and LAND steps at 10 kHz and 80% duty. The reason is the oxide column: the 20 µs off-time lets the sheath collapse and the charge on the column floor and walls relax, which reduces the column offset that Book #30 attributes to charging. The pillars, with a charging time of seconds, are not relieved by it (Chapter 13).

### 6.4.3 What to Pulse

```
Step    Pulsed?   Reason
─────────────────────────────────────────────────────────────────────────────
FL      no bias at all
SN1     no        embedded pillars; rate matters; TiN loss set by the flash
OX      yes 80%   column offset and crescent attack (Book #30, Ch. 3); costs 19 s
SN2     no        same as SN1
LAND    yes 80%   same as OX; costs 4 s
```

---

## 6.5 Wafer Temperature

### 6.5.1 Through a Recipe

Chapter 3 gave the steady-state temperature dependence (2.0%/K in SiN rate, 3.7%/K in TiN rate). A recipe does not run at one temperature. A wafer enters the chamber at about 23 °C, is clamped to an ESC at 35 °C, and warms up as the plasma loads it:

```
Wafer temperature through S1 (illustrative):
  Entry                       23 °C
  After clamp, 4 s of flash   31.6 °C   (heat transfer time constant τ = ρ c_p t / h ≈ 3.2 s
                                         with He backside at 10 Torr, h ≈ 400 W/m²K)
  SN1 (40 s, 1.8 kW)          32 → 38 °C
  OX (129 s, 2.2 kW)          38 → 43 °C   (highest source power)
  SN2                         41 °C
  LAND                        41 → 43 °C
```

The effect on SN1: the film is thicker at the start, where the wafer is cooler.

```
Cold start (d₀ at the wafer temperature; SN steps, narrow distribution):
  Wafer T   d₀ (nm)   SiN (nm/min)   TiN steady (nm/min)
  23 °C     4.03      154            0.408
  30        3.75      182            0.541
  35        3.57      203            0.648
  40        3.40      225            0.766
```

A cold wafer starts with a thicker film and a lower rate. That is helpful for the TiN and costs a few seconds in SN1. The flash does a second job: it is also a **thermal soak**. At the end of its 4 s the wafer is at 31.6 °C, within 3.4 K of the chuck, and SN1 begins at 154–200 nm/min instead of 225 nm/min.

### 6.5.2 The ESC Setpoint

The ESC is set to 35 °C and the wafer, warmed by the plasma, averages 40 °C over the recipe. Setting the ESC 5 K higher would give a 10% faster nitride etch and a 3% higher TiN loss at constant cleared nitride (Section 6.6), and would take the OX step to 43–48 °C, outside the ± 2 K window of Chapter 5. The gain does not pay for the loss of the window.

---

## 6.6 The Sensitivity Table

With the flash in place, each lever is shifted while the nitride cleared is held constant (the step times scaled by the rate change):

```
S1 nitride steps (SN1 + SN2), shift from baseline:
  Shift                         SiN rate   Time     TiN loss (nm)   Δ TiN loss
  Baseline                      225        1.00     0.97            —
  O₂ −1 sccm (d₀ +0.05 nm)      −3.0%      ×1.03    0.96            −0.01
  O₂ +1 sccm (d₀ −0.05 nm)      +3.0%      ×0.97    0.98            +0.01
  d₀ +0.3 nm                    −16.5%     ×1.20    0.92            −0.05
  d₀ −0.3 nm                    +19.7%     ×0.84    1.04            +0.06
  T +5 K                        +9.7%      ×0.91    1.00            +0.03
  T −5 K                        −9.6%      ×1.11    0.94            −0.03
  Mean E 300 eV                 −16.2%     ×1.19    0.90            −0.08
  Mean E 500 eV                 +14.3%     ×0.88    1.03            +0.06
  Flash 3 s                     0          1.00     1.14            +0.16
  Flash 5 s                     0          1.00     0.87            −0.10
  No flash                      0          1.00     2.40            +1.43
```

Two lessons:

1. **The TiN loss is flat in everything but the flash.** Across ± 0.3 nm of film, ± 5 K, and ± 100 eV the loss moves by at most 0.08 nm. The steady-state loss is already small, and the steady term is proportional to the nitride cleared divided by the steady selectivity; only the transient does not scale that way.
2. **The rate moves a lot.** The same shifts change the SiN rate by 3% to 20% and the clearing time by 0.84 to 1.20. Those variations are the mask-budget and throughput questions of Chapters 5 and 15, and they are tracked with endpoint and time caps, not with TiN metrology.

The flash itself has a smaller but real sensitivity: 1 s of flash is worth 0.1–0.16 nm. A flash of 4 s is where the return falls below 0.1 nm per second.

---

## 6.7 Setting the Levers

```
Order of tuning (DOE strategy):
  1. Flash time (3–6 s): sets the TiN loss; confirm with a TiN witness (Ch. 15).
  2. Gas (O₂ fraction): sets d₀ to 3.4 nm and the nitride rate to the clearing-time target.
  3. Wafer temperature (ESC): trims the rate across the wafer; keep within ± 1 K.
  4. Mean energy: trade mask margin against time; stay at 300–400 eV.
  5. Pulsing: only where charging or column offset demands it (OX, LAND; SN steps in S2).
  6. IEDF width: leave it alone; no benefit has been found for a narrow distribution.
```

---

## Summary and Key Takeaways

1. **With a flash, TiN loss is flat.** ± 0.3 nm of film, ± 5 K, and ± 100 eV move it by at most 0.08 nm. Without a flash it is 2.40 nm and sensitive to everything.

2. **Energy trades mask for time.** 400 to 200 eV saves 14 nm of ACL and 0.19 nm of TiN and lengthens the nitride etch by 55%.

3. **The width of the distribution does not matter.** The yield function is concave and the TiN threshold is below either distribution; the tailored waveform has no benefit for selectivity, mask, profile, or charging, and S1 does not use it.

4. **Pulsing buys selectivity with rate.** 6% for 15% rate at 80% duty. S1 pulses OX and LAND at 10 kHz, 80%.

5. **The wafer starts cold.** 23 °C at entry; the 4 s flash is also a thermal soak that brings the wafer to 31.6 °C.

6. **The rate moves, the TiN does not.** The levers other than the flash are controlled by endpoint and time caps, not by TiN metrology.

---

## Study Questions

1. Using the energy sweep, compute the SN1 + SN2 time and mask use at 300 eV with a 4 s flash. By how much does the throughput of a 4-chamber platform fall relative to 400 eV? (Overhead 174 s, other steps unchanged.)

2. Show with Jensen's inequality that a mean-preserving spread of ion energies lowers the mean of √E − √E_th when E_th is below the lower edge of the distribution. What happens when E_th lies inside the distribution?

3. A TiN with a heavily fluorinated surface has an effective sputter threshold of 250 eV. Recompute the steady TiN rate for the broad (200–600 eV) and the narrow (340–460 eV) distributions at a mean of 400 eV, using the yield form of Chapter 3 (a flat distribution, no yield below threshold), and find the ratio of the two. Does the width now matter? Repeat for a threshold of 150 eV and explain the difference.

4. Duty is lowered from 80% to 60% in the OX step. Find the new OX time, the change in the ACL consumed (use 650 nm / 5 per Book #30 as the baseline at CW), and the change in the OX contribution to TiN loss if the OX TiN loss is 1.8 nm at 80%.

5. The wafer enters the chamber at 20 °C and the ESC is at 35 °C. What temperature does the wafer reach after a 4 s flash, and after a 6 s flash (τ = 3.2 s)?

6. A DOE finds the SN1 rate 8% low and the TiN loss 0.05 nm higher on a chamber. Using the sensitivity table, which levers could explain both, and which could not?

---

**Next Chapter:** [Chapter 7: Radical, Atomic-Layer & Wet Nitride Removal — Trim, Finish & Stencil Routes](./07-radical-ale-wet-nitride-removal.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
