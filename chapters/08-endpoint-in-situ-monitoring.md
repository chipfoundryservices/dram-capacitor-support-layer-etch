# Chapter 8: Endpoint & In-Situ Monitoring of a Thin Nitride in a 50 nm Opening

## Overview

The support layer etch must stop in three places: on the upper oxide after 120 nm of nitride, on the middle nitride after 650 nm of oxide, and in the BPSG after 50 nm of nitride. It must do so for 5.5% of the wafer area, through openings 50 nm wide, under a carbon mask that is itself being etched. Nothing here is a large clean film that goes through a thickness interference fringe. The monitoring options are the emission of the plasma and the signal of the chamber.

This chapter shows what optical emission can tell: it gives a strong signal for the top-support clear, a usable one for the arrival at the middle support, and a weak one for the clear of the middle support itself. It then shows what each signal is worth. Endpoint cannot remove the overetch; the overetch is set by the corner geometry of Chapter 12. Its value is in wafer-to-wafer control and, much more, in fault detection: a chamber whose CN signal drifts is a chamber whose polymer film has drifted.

**Learning Objectives:**
- Estimate the nitrogen flow from a nitride etch and the optical-emission signal that results
- Identify the emission species and the signal direction at each of the four transitions
- Explain why interferometry fails on this stack
- Compute the endpoint spread and decide what an endpoint can and cannot do for the overetch
- Use the flash and the emission signals to monitor the polymer film in situ
- Write the endpoint logic and its fault conditions

---

## 8.1 What Has to Be Detected

```
Transitions in S1 (reference):
  Step    Event                         Nominal time   Spread (3σ)    What it needs
  SN1     top SiN cleared; oxide        40 s           ± 4.5%         stop within 25% OE; protect oxide
  OX      reached the middle SiN        129 s (pulsed) ± 3.4%         start SN2 with minimal oxide OE
  SN2     middle SiN cleared; BPSG      20 s           ± 5.8%         clear every site; no sliver
  LAND    depth 50–150 nm into BPSG     29 s           —              time-based (no signal)
```

The first two are within the first third of the etch, and in a column that is open to the plasma. The third is at the bottom of a column at aspect ratio 17, in 50 nm of film.

---

## 8.2 The Signal: How Much Nitrogen Comes Out

### 8.2.1 An Estimate

Nitride is the only film in the stack that contains nitrogen. Every nitrogen atom that leaves does so as CN, HCN, N₂, or NH, and the CN (B²Σ⁺ → X²Σ⁺, 388.3 nm) is the strongest marker.

```
Nitrogen released in SN1 (reference):
  Wafer area                       706.9 cm²
  Array coverage                   38.5% of the wafer  (272 cm², Book #33)
  Nitride exposed in the array     14.4% of array area (1012 nm² per opening / 7015 nm²)
  Area of nitride etched           706.9 × 0.385 × 0.144 = 39.2 cm²
  SiN rate                         225 nm/min = 3.75 × 10⁻⁷ cm/s
  Volume rate                      1.47 × 10⁻⁵ cm³/s
  N density (PECVD, Si/N = 0.8)    5.0 × 10²² cm⁻³
  N atoms per second               7.3 × 10¹⁷ s⁻¹ = 1.6 sccm
  Gas flow (SN step)               20 + 25 + 18 + 300 = 363 sccm
  Nitrogen fraction of the flow    0.45%
```

1.6 sccm of nitrogen atoms in 363 sccm of gas is a small but measurable fraction. The CN band is the dominant nitrogen emitter and, in a plasma containing carbon, the nitrogen-containing species are present almost entirely as CN and HCN. The emission is proportional to the nitrogen density, and the nitride's contribution to it is the whole of it.

### 8.2.2 Escape from the Column

The products of the middle-support etch leave through the column, not up through the open top of the wafer. At an aspect ratio of 17 the column is a tube of low conductance, but non-sticking gases leave it by diffusion in a time of

```
τ = L² / D_K,   D_K = (2r/3) v̄
  HCN:  v̄ = 509 m/s,  r = 22.5 nm → D_K = 7.6 × 10⁻⁶ m²/s
  τ = (770 nm)² / 7.6 × 10⁻⁶ m²/s = 78 ns
```

78 nanoseconds is negligible against a 100 ms sample. The column delays the signal not at all, and attenuates nothing, because the products do not stick. This differs from the situation of the reactants, which stick and are lost (Chapter 7).

### 8.2.3 Lines Used

```
Species      Wavelength    Origin                      Direction at the transition
─────────────────────────────────────────────────────────────────────────────────────
CN           388.3 nm      nitride etch                falls as nitride clears
CO           483.5 nm      oxide + O₂ + carbon         rises when oxide is exposed
F            703.7 nm      fluorine radical            rises as nitride clears (less consumed)
H_α          656.3 nm      CH₂F₂, CH₃F, polymer        drifts with polymer state
CF₂          250–330 nm   polymer precursor           monitor of polymer supply (flash)
Ar           750.4 nm      actinometer                 normalizes the others
```

All lines are taken as ratios to Ar 750.4 nm. The ratio removes the part of the intensity that follows electron density and temperature, and leaves the part that follows the species.

---

## 8.3 Why Not Interferometry

Interferometry measures the film thickness through the phase of the reflected light and works for films a few hundred nanometres thick and open over most of the monitored area. Here neither condition holds:

1. The **ACL** is a carbon film 300 nm thick that absorbs strongly at visible wavelengths. It covers 72% of the array (the openings are 28% of the area), so the light that reaches the nitride does so through 50 nm openings, smaller than the wavelength by a factor of ten. The reflected signal is that of the mask.
2. The **etched film is 50 nm thick** at the middle support. A film of 50 nm changes the optical path by a fraction of a fringe.
3. The ACL is itself eroding at 50–75 nm/min, so its own fringes would swamp the film's.

Interferometry of the ACL is useful in one place: monitoring how much of it remains (the margin of 47 nm of Chapter 1) by its thickness fringes at near-infrared wavelengths, in a separate measurement (Chapter 15). It does not give endpoint.

---

## 8.4 Signals Through the Recipe

```
Emission signals in S1 (illustrative):
  Step     Marker       Direction        ΔI/I (of the marker)    Noise (rms, normalized)   S/N per sample
  SN1      CN/Ar        falls at clear   −85%                    0.3%                      ≈ 280
           CO/Ar        rises            +25%                    0.3%                      ≈ 80
  OX       CN/Ar        rises at arrival at the middle support    +30%      0.3%            ≈ 100
           CO/Ar        flat to slight   —
  SN2      CN/Ar        falls at clear   −25%                    0.3%                      ≈ 80
           F/Ar         rises            +6%                     0.2%                      ≈ 30
  LAND     none         time only
```

The SN1 signal is excellent: 85% of the CN comes from the nitride being etched, so the signal falls to the baseline when it clears. The OX arrival signal is a rise of the CN as the plasma sees nitrogen again; it is useful and its edge is blurred by the spread of the oxide clear times across the wafer (± 3.4% of the 124 s clear time is ± 4.2 s). The SN2 clear is the hardest. Of the CN during SN2, only about a quarter comes from the middle-support floor; the remainder is from the radical-driven etch of the top-support wall, the SN1 polymer, and the reactor's nitrogen background. The signal is a fall of 25%, with a width set by the clearing spread across the wafer.

---

## 8.5 What an Endpoint Is Worth

### 8.5.1 The Overetch Cannot Be Removed

The overetch of each nitride step, 25% in SN1 and 40% in SN2, is not there to cover a measurement error. It clears the corner of the crescents (Chapter 12), where the nitride sits in an acute angle against the TiN and etches more slowly than the nitride on the flat. An endpoint tells the process when the *average* nitride has cleared and has no information on the corners. An endpoint-based overetch would therefore be 25% of the measured clearing time, and not less.

### 8.5.2 Wafer-to-Wafer Spread

What the endpoint removes is the wafer-to-wafer part of the spread: incoming thickness and chamber rate. With fixed times, the effective overetch of a wafer with 3.3% thicker top support and a 3% slower chamber is 25% − 6.3% = 18.7%. With an endpoint, it is 25%:

```
Overetch spread, SN1 (3σ), nominal clear 32 s, fixed step 40 s:
  Clearing time spread        √(3.3² + 3²) = 4.5%  →  30.6 to 33.4 s
  Fixed time:                 overetch 40/33.4 − 1 = 20%  to  40/30.6 − 1 = 31%
                              OE time 6.6 to 9.4 s; oxide lost (148 nm/min) 16 to 23 nm
  Endpoint + 25% OE:          25% ± 0.5% (noise); OE time 8 ± 0.4 s; oxide lost 20 ± 1 nm
```

The spread in the oxide loss is a few nanometres in either case. An endpoint on SN1 is a modest improvement in control. It is better understood as a **monitor**.

### 8.5.3 OX Arrival

Detecting the arrival at the middle support lets SN2 start at once:

```
OX clear time (pulsed): 105 s / 0.85 = 123.5 s, ± 3.4% (3σ) = ± 4.2 s; fixed step 129 s
Fixed time:             overetch on the middle support 5.5 ± 4.2 s (1.3 to 9.7 s);
                        a thick, slow wafer is within 1.3 s of arriving late
Endpoint + 1 s margin:  SN2 starts within ± 1 s of the arrival
Saving                  ≈ 4.5 s of pulsed OX on average; 0.06 nm of TiN (1.8 nm per 129 s);
                        4.5 nm of ACL (≈ 1 nm/s)
```

The saving is small and consistent. The larger value is protection against a wafer whose oxide is slow, which a fixed time would leave unfinished.

### 8.5.4 SN2

The SN2 marker is weak in S/N terms but strong in value: the clearing time of the middle support is the single best predictor of the sliver rate (Chapter 12). Its width across the wafer is the wafer's clearing spread, and a width that grows is a chamber whose uniformity has changed.

---

## 8.6 The Flash as a Sensor

The flash of Chapter 3 is a 4 s CH₃F/Ar plasma with no bias. Its emission carries information on the polymer supply:

```
Flash monitoring (illustrative):
  CF₂ intensity (ratio to Ar), integrated over the 4 s:      I_CF2
  Polymer built on TiN                                        d_f = 1.6 nm × (I_CF2 / I_ref)
  ± 10% in I_CF2  →  ± 0.16 nm in the film  →  ∓ 0.03 nm in the transient loss (0.96 nm × e^(−1.6) × 0.16)
```

A 10% drift in the flash emission is a 0.16 nm change in the starting film, and it has little effect on the TiN loss. The drift is a good indicator of the wall state and of consumable wear (Chapter 5), and the control system uses it to adjust the flash time (a 10% change in I_CF2 changes the flash time by 0.4 s).

---

## 8.7 Endpoint Logic

```
Endpoint algorithm (per step):

  1. Window       Ignore the first t_mask seconds (SN1: 4 s after bias on; SN2: 4 s).
  2. Signal       x(t) = [CN/Ar](t), smoothed over 1.0 s (10 samples).
  3. Reference    x_ref = mean of x over the 3 s after the window.
  4. Detection    EP when x(t) falls below x_ref × (1 − 0.5·ΔI/I_expected) and the first
                  derivative is negative for 5 consecutive samples.
  5. Overetch     t_OE = k · t_EP, with k = 0.25 (SN1) or 0.40 (SN2); min and max
                  limits ±25% of the nominal OE.
  6. Fault        If no EP by t = 1.5 × t_nominal: stop; flag the wafer (underclear risk).
                  If EP before 0.6 × t_nominal: stop; flag the wafer (thin film or arcing).
```

The fault conditions matter more than the nominal ones. An endpoint that occurs early on a wafer may indicate a film that is thinner than specified (a lot problem), a mask problem (the nitride is exposed early, and ACL is gone), or a chamber state that has changed (the CN signal from a drifting polymer film has crossed the threshold). Each calls for a different action, and the logic records the signals for the engineer.

---

## 8.8 In S2

In S2 the SN2 etch is done in a free cavity. The CN signal is the same, the CO signal from oxide walls is absent (the oxide is gone), and the signal to monitor for the arrival at BPSG is the F/Ar and SiF emission from the BPSG. The cavity has no memory of OX polymer (Chapter 5), so the flash is repeatable and the SN2 start is clean. The overetch of 40% is carried by SN2 itself (26 s). The tools and the logic are the same.

---

## Summary and Key Takeaways

1. **Nitrogen is the marker.** 1.6 sccm of N atoms in 363 sccm of gas; CN at 388.3 nm normalized to Ar at 750.4 nm.

2. **SN1 is easy; SN2 is hard.** The SN1 signal falls 85% at clear (S/N ≈ 280); the SN2 signal falls about 25% (S/N ≈ 80) because three-quarters of the CN is not from the middle support.

3. **The column does not delay products.** 78 ns of diffusion time at AR 17; products do not stick.

4. **Interferometry fails.** The ACL is absorbing and covers 72% of the array; the film is 50 nm thick.

5. **An endpoint cannot shorten the overetch.** The OE clears the crescent corners; endpoint removes only the wafer-to-wafer spread (4.5% → 0.5%).

6. **The best use of the signals is fault detection.** The flash emission and the SN2 width track the polymer film and the clearing spread.

---

## Study Questions

1. Repeat the nitrogen estimate for SN2 (50 nm film, 150 nm/min, nitride 13.5% of the array area, 363 sccm). What fraction of the flow is nitrogen? (Expect about 1 sccm.)

2. For HCN at 330 K, compute v̄ and the column escape time for a column of 770 nm and radius 22.5 nm. Compare with the sample time of 100 ms. At what column depth would the escape time equal the sample time?

3. The openings are 28% of the array area. Of that, 14.4 points are nitride and 951/7015 = 13.6 points are the TiN crescents. Check that they add to 28%, and say what share of the exposed area at the start of SN1 is nitride.

4. A new lot has a top-support film 3% thinner than the reference. With a fixed-time recipe and with an endpoint recipe, what are the overetch and the oxide loss at SN1?

5. A chamber's flash CF₂ intensity rises 15% over 400 RF-hours. By how much does the starting film change, and what happens to the SN1 TiN loss? What would you adjust?

6. The endpoint logic flags a wafer with EP at 0.55 × t_nominal. List three causes and the check that distinguishes each.

---

**Next Chapter:** [Chapter 9: Walls, Polymer, Particles & Post-Etch Clean](./09-walls-polymer-post-etch-clean.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
