# Chapter 5: CCP Chambers for the Nitride Lattice Open

## Overview

Book #30 chose a medium-power dual-frequency CCP for the support open and described it in terms of what the whole column needs: frequencies, power, a four-step gas sequence, throughput. This chapter looks at the same chamber from the nitride's side. The nitride steps of the recipe are the ones that expose TiN to the plasma at its weakest, and the questions are specific to them. What does the chamber remember when the gas changes from the oxide step to the nitride step? How fast must it switch? What does a polymer flash demand of the RF system? How does a worn ring, an eroded electrode, or a thin coating shift the polymer film on which the whole selectivity model of Chapter 3 depends?

The chapter ends with the chamber's contribution to wafer-level uniformity, which for this etch means the tilt of the column at the wafer edge, and with fleet matching, throughput, and the safety of a process that makes hydrogen cyanide.

**Learning Objectives:**
- State the requirements the nitride steps place on a CCP chamber beyond those of the oxide step
- Compute the sheath and ion transit time and the consequences for ion energy distribution at 400 kHz, 2 MHz, and 60 MHz
- Explain the chamber memory between steps and why a polymer flash resets it
- Write the full S1 recipe, step by step, with the gas switching it requires
- Relate consumable wear to polymer thickness, and polymer thickness to rate and TiN loss
- Compute the edge-ring tilt budget and chamber throughput for S0 and S1

---

## 5.1 Requirements the Nitride Steps Add

```
Support layer etch, chamber requirements (reference; S1):

                           OX step               SN1, SN2 (nitride)        FLASH
  Ion energy               600 eV, broad OK      400 eV, ± 50% (sinusoidal) none (bias off)
  Polymer on TiN           ≥ 3 nm self-limiting  set by gas to 3.4 nm      build 1.6 nm in 4 s
  Switching in/out         ≥ 3 s gas settle      ≤ 2 s gas settle          ≤ 1 s, bias fully off
  Wafer temperature        ± 2 K                 ± 1 K                     ± 1 K
  Selectivity driver       C₄F₆ polymer, ACL     polymer film on TiN       polymer on TiN
  Uniformity driver        landing depth         clearing time ± 4.5%      film uniformity
```

Four requirements go beyond the oxide step:

1. **The polymer film is the process variable.** In the nitride steps, rate and selectivity follow exp(−d/λ) (Chapter 3). A 10% change in film thickness at 3.4 nm moves the SiN rate by 20% and the TiN rate by 30%. The chamber must hold the film to within 0.1 nm, which means holding the polymer arrival rate and the wall state.
2. **A stable mean ion energy.** The nitride steps run at 400 eV with a sinusoidal 2 MHz bias; the mean must hold to ± 5%, because the rate follows it (Chapter 6).
3. **Fast, clean switching.** The flash is a 4 s step. A 2 s gas settle on a 4 s step would be half the step.
4. **Temperature within 1 K.** Chapter 3's table: 20 K shifts the TiN rate by 74%, or 3.7% per kelvin.

---

## 5.2 Sheath, Ion Transit, and the Choice of Frequency

### 5.2.1 Why Two Frequencies

```
Plasma and sheath (illustrative, argon-dominated, 25 mTorr):
  Electron temperature             T_e = 3 eV
  Ion density                      n_i = 1 × 10¹¹ cm⁻³
  Debye length                     λ_D = 7430 √(T_e/n) m = 41 µm
  Sheath thickness at 1000 V       s ≈ 1.2 λ_D (2V/T_e)^¾ = 6.4 mm
  Ion transit time (Ar⁺)           τ_i = 3 s √(m/(2eV)) = 280 ns
                                   (CF₂⁺, m = 50 amu: 310 ns)
```

The ratio of the ion transit time to the RF period decides how the ions respond:

```
Frequency    Period    τ_i/τ_RF    Ion response               IEDF
60 MHz       16.7 ns   18.6        ions see the mean field    narrow, ≈ source
2 MHz        500 ns    0.6         partly follow the field    bimodal, ± 50% wide
400 kHz      2.5 µs    0.12        follow the field           very broad, saddle-shaped
```

High frequency dissociates gas and makes density, with little ion energy; low frequency delivers energy and a broad distribution. That is why a CCP has a 60 MHz source on the upper electrode and a 2 MHz bias on the lower. The S0 nitride step uses the 2 MHz bias at about 1.4 kW. The ± 50% distribution of Chapter 3 is its IEDF.

### 5.2.2 The Tailored Waveform (Optional)

A bias with an arbitrary waveform can narrow the distribution. The mechanism is that the ion energy is set by the sheath voltage at the moment of crossing; if the sheath voltage is held constant during the crossing, the ions arrive with one energy. A ramp that compensates the sheath capacitor's charging between pulses does that:

```
Tailored-waveform bias (optional; not used in the S1 reference):
  Repetition rate           400 kHz
  Waveform                  pulsed negative with a positive-going compensating ramp
  Mean ion energy           ≈ 400 eV
  IEDF width                ± 15%   (against ± 50% for sinusoidal 2 MHz)
  Power                     ≈ 1.2 kW  (below the 1.4 kW of the sinusoid for the same mean energy)
```

Chapter 3 showed that the narrow distribution does not change the SiN:TiN selectivity in this model, Chapter 6 shows that it changes neither the mask erosion nor the column profile at these energies, and Chapter 13 shows that it does not change the charging of the pillars. **No benefit has been found for it in this book.** S1 runs its nitride steps with the sinusoidal bias, and the generator is an optional upgrade that this chapter describes for completeness.

### 5.2.3 Pulsing

The OX and LAND steps of S1 pulse the bias at 10 kHz, 80% duty. During the off-time the plasma density decays by a factor of about 0.7 and the charge on the oxide column floor relaxes. (The pillars, with a charging time of seconds, are not relieved by it; Chapter 13.) The price is time: the OX rate falls by 15% (110 to 129 s), and LAND (25 to 29 s). Chapter 6 gives the trade quantitatively.

---

## 5.3 Chamber Memory Between Steps

### 5.3.1 What the Walls Hold

The chamber walls, upper electrode, focus ring, and liner carry polymer from the previous step. In a one-pass sequence of four steps, three chemistries share one volume:

```
Step sequence (S0/S1) and what each leaves on the walls:
  SN1    CH₂F₂/CF₄/O₂/Ar     thin, nitrogen-containing polymer (≈ 0.5 nm/wafer)
  OX     C₄F₆/O₂/Ar          thick carbon-rich polymer (≈ 3 nm/wafer)
  SN2    CH₂F₂/CF₄/O₂/Ar     picks up the OX film from the walls at the start
  LAND   C₄F₆/O₂/Ar          the same family as OX
```

At the beginning of SN2, the walls release part of the C₄F₆ polymer into the gas, with a decay time of the order of the gas residence time plus the wall release time:

```
Wall release at the start of SN2 (illustrative):
  Fraction of the polymer precursor flux supplied by the walls at t = 0    ≈ 30%
  Decay time constant                                                      ≈ 6 s
  Effective polymer film on TiN during SN2, early                          d₀ × (1 + 0.3 e^(−t/6 s))
                                                                           = 4.4 nm at t = 0, 3.4 nm after ≈ 15 s
```

The consequence is not a thicker film on the pillar, which would help. It is a **thinner nitride rate** for the first 10–15 s of SN2 and a different SiN:SiO₂, because the film on nitride also thickens. At SN2 the nitride has 20 s to clear. A 15 s period at a 20% lower rate adds 3 s to the clearing time. The time is not lost on average; it varies with the chamber's history, which is the damaging part.

### 5.3.2 A Starting Film That Varies

The TiN pillar top enters SN2 with a polymer film left by the OX step. Its thickness depends on the OX recipe, the wall state, and the time of the gas transition, and lies between 0 and 1.6 nm in a well-run chamber:

```
SN2 TiN loss versus starting film (S0 recipe, 20 s):
  Starting film    0 nm     0.8 nm    1.6 nm
  Transient loss   0.91     0.39      0.16     nm
  Total SN2 loss   1.06     0.56      0.35     nm
```

S0's reference of 1.06 nm assumes a bare start. In a real fleet the SN2 loss of an S0 chamber therefore varies between 0.35 and 1.06 nm with the history of the wall, and a part of that is chamber-to-chamber spread. The flash of S1 sets the initial film deliberately, to 1.6 nm plus whatever the previous step left (the film saturates at d₀): it **resets the memory** and makes the SN2 loss repeatable at 0.36 nm.

### 5.3.3 Two Chambers or One

The alternative to managing memory is to remove it by splitting the sequence between two chambers: a nitride chamber for SN1 and SN2, and an oxide chamber for OX and LAND. SN2 would then need the wafer to travel back to the nitride chamber, which breaks the one-pass sequence. The practical split is:

```
Option                  Chambers per wafer   Wafer path                 Cost
─────────────────────────────────────────────────────────────────────────────────────
One chamber, all steps  1                    none                       baseline
Two chambers            2                    SN1 | OX, SN2, LAND        +15% footprint;
                                                                         SN2 still follows OX
```

Because SN2 must follow OX in a one-pass route, no chamber split removes the memory at SN2. The flash is the remedy that works within one chamber. In S2, SN1 and SN2 are separated by a dip and a dry and need no OX step between them: two nitride-only chambers, or one, with no memory problem at all (Chapter 14).

---

## 5.4 The Full S1 Recipe

```
S1 recipe (CCP, 60 MHz source / 2 MHz bias; illustrative):

Step   Gases (sccm)                      P        Source    Bias            Time
─────────────────────────────────────────────────────────────────────────────────────
FL1    CH₃F 40, Ar 300                   20 mTorr 0.6 kW    none            4 s
SN1    CH₂F₂ 20, CF₄ 25, O₂ 18, Ar 300   25       1.8 kW    2 MHz 400 eV    40 s
  (switch, 2 s, no plasma bias)
OX     C₄F₆ 15, O₂ 30, Ar 400            20       2.2 kW    2 MHz pulsed    129 s
                                                            600 eV, 80%, 10 kHz
  (switch, 2 s)
FL2    CH₃F 40, Ar 300                   20       0.6 kW    none            4 s
SN2    CH₂F₂ 20, CF₄ 25, O₂ 18, Ar 300   25       1.8 kW    2 MHz 400 eV    20 s
  (switch, 2 s)
LAND   C₄F₆ 12, O₂ 28, Ar 400            20       1.8 kW    2 MHz pulsed    29 s
                                                            500 eV, 80%, 10 kHz

Plasma time              226 s       (S0: 195 s)
Wafer temperature        40 °C, ESC with ± 1 K control; He backside 10 Torr
```

The gas switches between steps are done with the plasma off or at minimum power, in 2 s. The FL steps need fast MFC response: CH₃F is switched in at a 40 sccm setpoint and must reach 90% of it in under 1 s.

---

## 5.5 Consumable Wear and the Polymer Film

### 5.5.1 What Wears

```
Consumables in a support-layer etch chamber:
  Upper electrode (Si or SiC)       RF-hours life 600; erodes ≈ 0.5 mm
  Focus / edge ring (Si, SiC)       life 300 h; erodes 0.5–1.0 mm in height
  Chamber liners and shields        Y₂O₃ or YOF coated; life 1500 h
  Gas distribution plate holes      polymer plugging; life 500 h
```

Silicon parts supply a scavenger for fluorine: the Si surface takes fluorine from the gas as SiF₄. The scavenging rate shifts the F/C ratio of the polymer precursors and so the film thickness d₀. A new electrode scavenges more than a worn one; the drift is slow and monotonic over the consumable's life.

```
Polymer film drift over a consumable life (illustrative):
  d₀ new          3.4 nm
  d₀ end of life  3.0 nm  (−0.4 nm; less scavenging as the electrode thins)
  Effect (Chapter 3 table):  SiN rate  222 → 282 nm/min  (+27%)
                             TiN rate  0.755 → 1.126 nm/min  (+49%)
                             SiN:TiN   294 → 251
```

A drift of 0.4 nm in the film changes the rate of the nitride steps by 27% and the TiN loss by 49%. The control response (Chapter 15) is endpoint-based, with a time cap, and a recipe adjustment (O₂ flow) tied to the electrode hours.

### 5.5.2 Focus Ring and Ion Tilt

At the edge of the wafer the sheath bends over the step between the wafer and the ring. When the ring wears, the step grows, and ions arrive tilted. Over a column of 770 nm the tilt moves the bottom of the opening:

```
Tilt budget at the middle support (column depth 770 nm):
  Tilt θ     Offset of the bottom = 770 nm × tan θ
  0.1°       1.3 nm
  0.3°       4.0 nm     ← specification limit (offset ≤ 4 nm)
  0.5°       6.7 nm
  1.0°       13.4 nm
```

An offset of 4 nm moves the bottom of the column toward one pillar by 4 nm and the crescents with it (Chapter 4's overlap depth budget). The tilt budget is therefore as tight as the overlay budget. Ring height is a consumable with a limit on its erosion, and the edge tilt is monitored from the column offset in the last 5 mm of each wafer (Chapter 15).

---

## 5.6 Temperature Control

The ESC holds the wafer at 40 °C with several zones. The requirement of ± 1 K follows from the 3.7%/K sensitivity of the TiN loss rate and the 2.0%/K sensitivity of the SiN rate (Chapter 3).

```
Wafer temperature budget (illustrative):
  ESC setpoint (centre/middle/edge zones)    35 / 35 / 35 °C
  Plasma heating over a 226 s recipe          +8 K, ≈ 0.036 K/s, rising over the SN1 and OX steps
  Backside He pressure                        10 Torr
  Temperature at the wafer                    40 °C, ± 1 K across the wafer
  Edge-to-centre difference allowed           ± 1 K
```

Plasma heating is the larger disturbance and varies step by step: the OX step deposits 2.2 kW of source power and loads the ESC more than the SN steps. A flash step at 0.6 kW lets the wafer cool by about 1 K. The ESC is set cold, at 35 °C, so that the wafer at the middle of the recipe sits at the reference 40 °C.

---

## 5.7 Throughput, Matching, and Safety

### 5.7.1 Throughput

```
Per-wafer chamber time (reference):
  Plasma                       S0 195 s        S1 226 s
  Overhead                     174 s           174 s
    (transfer, pump-down, stabilization, ACL strip 50 s, waferless clean 60 s)
  Per-chamber time             369 s           400 s
  4-chamber platform           39.0 wafers/h   36.0 wafers/h
```

S1's extra 31 s of plasma (the two flashes and the pulsed oxide step) cost 7.7% of platform throughput. The specification of Chapter 1 asks for at least 35 wafers/h.

### 5.7.2 Matching

```
Chamber matching criteria (S1):
  SiN rate (blanket PECVD)            ± 3%  across chambers
  SiN : TiN, steady state             ≥ 250 on a blanket TiN witness
  Polymer film on TiN (ellipsometry
    after a 4 s flash)                1.6 ± 0.15 nm
  OES ratio CN/Ar at SN1              ± 5% from the fleet mean
  Ion tilt (edge column offset)       ≤ 4 nm at 150 mm radius
  Particle adders ≥ 30 nm             ≤ 10 per wafer
```

### 5.7.3 Hydrogen Cyanide and Flammables

The nitride steps make HCN and cyanogen at tens of ppm in the exhaust. CH₃F and CH₂F₂ are flammable. The chamber's installation needs:

```
  Exhaust abatement          thermal oxidizer (burn-box) with scrubber on every foreline
  HCN monitor                continuous, foreline and facilities exhaust, alarm at 2 ppm
  Gas cabinets               leak-checked, with flammable-gas detection and excess-flow shut-off
  Pump oil / purge           inert purge to keep CN polymer from accumulating in the pump
```

---

## Summary and Key Takeaways

1. **The polymer film is the process variable.** 10% in thickness moves SiN by 20% and TiN by 30%; the chamber must hold it to 0.1 nm.

2. **The frequency decides the IEDF.** τ_i/τ_RF of 0.6 at 2 MHz gives a bimodal ± 50% distribution; a tailored waveform narrows it to ± 15% and buys nothing in this process.

3. **The chamber remembers.** The OX polymer on the walls and on the pillar tops gives SN2 a starting film between 0 and 1.6 nm, and an SN2 TiN loss that varies between 0.35 and 1.06 nm from chamber to chamber.

4. **The flash is a memory reset.** It sets the initial film deliberately, and makes the SN2 loss repeatable at 0.36 nm.

5. **Consumable wear shows up as film thickness.** A 0.4 nm drift in d₀ is +27% in SiN rate and +49% in TiN rate; edge ring height maps to column tilt at 1.3 nm per 0.1°.

6. **S1 costs 7.7% in throughput and makes hydrogen cyanide.** 36.0 wafers/h on a 4-chamber platform; abatement is mandatory.

---

## Study Questions

1. Compute the sheath thickness and the Ar⁺ transit time for a sheath voltage of 400 V at the same plasma parameters. At what RF frequency is τ_i/τ_RF = 1 for that voltage?

2. SN2 begins with a polymer film on TiN of 1.2 nm. Using the formulas of Chapter 3, estimate the transient loss and the total SN2 loss in 20 s.

3. Electrode wear reduces d₀ by 0.1 nm per 150 RF-hours. How many hours before the SiN rate has risen 10%? What O₂ change would restore it (assume d₀ rises 0.05 nm per 1 sccm O₂ decrease)?

4. A ring with 0.8 mm of erosion tilts ions by 0.45° at the edge. What offset does that give at the middle support and at the top support? Does it violate the specification?

5. Compute the platform throughput if the flash is lengthened to 6 s each, and compare with the 35 wafers/h limit.

6. Why does splitting the one-pass sequence between two chambers not remove the SN2 memory problem in S0 or S1? In what route does a two-chamber arrangement remove it?

---

**Next Chapter:** [Chapter 6: Ion Energy, Bias Pulsing & Temperature — The Selectivity Levers](./06-ion-energy-pulsing-temperature.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
