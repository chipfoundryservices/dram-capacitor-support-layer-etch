# Chapter 15: Metrology, Inspection & Advanced Process Control

## Overview

The quantities that matter most in the support layer etch are the hardest to see. The middle-support opening is 770 nm below the surface in a column 44 nm wide, and its CD has a margin of 1 nm. The pillar-top loss is 3 nm of a 5 nm-wide surface. The polymer coverage that decides whether HF enters a column is on the wall at the bottom. The failure that costs yield is a cluster of three blocked openings among four billion. This chapter sets out how each of these is measured, what each measurement can and cannot resolve, and what is left to inference.

The result is a ladder. At the top are fast, non-destructive measurements of what can be seen from the surface: the top CD, the thickness of the top support, the carbon mask that remains. Below them are test structures in the scribe that stand in for what cannot be seen: a blanket TiN pad for the pillar-top loss, a deep-hole array for the polymer at depth. Below those are destructive and slow measurements: cross-sectional TEM of the middle support. At the bottom is the one that matters and takes weeks: the bitmap of the failing cells, read by class. Around the ladder are the controls that use it: feed-forward of the incoming films, feedback on the chamber, and fault detection on the signals of Chapters 5 and 8.

**Learning Objectives:**
- List the measurands of the support layer etch, the tool for each, and what limits it
- Explain which dimensions can be measured from the top and which must be inferred
- Compute the inspection area needed to detect killer clusters and conclude which tool can do it
- Describe the scribe test structures that replace unmeasurable quantities
- Write a virtual-metrology model for the TiN loss from FDC features
- Design an EWMA control on a TiN witness and compute its limits and sensitivity
- Describe the class-aware bitmap analysis and the sampling it needs

---

## 15.1 The Measurands

```
Measurand                          Where                   Tool                          Resolution, sample
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Top-support opening CD             top, after ACL strip    CD-SEM; OCD                   ± 0.3 nm (3σ); 9 sites per wafer
Overlap depth into pillars         top                     CD-SEM (crescent edge)        ± 0.8 nm; 5 sites
Top-support thickness              scribe pads             spectroscopic ellipsometry    ± 0.3 nm; 9 sites
ACL remaining                      before strip            near-IR interferometry        ± 2 nm; 9 sites
Middle-support opening CD          770 nm below            XTEM; OCD (model)             ± 0.5 nm (TEM); ± 1.5 nm (OCD)
Middle-support thickness           buried                  deposition metrology only     ± 0.5 nm
Nitride fin height and width       corners                 XTEM, plan-view TEM           ± 0.5 nm; destructive
TiN pillar-top loss                crescent top            TiN witness pad (XRF);        ± 0.1 nm (XRF); XTEM ± 0.5 nm
                                                           XTEM                          
Polymer coverage at depth          column wall             deep-hole scribe structure;   TOF-SIMS / TEM-EELS; destructive
                                                           contact-angle witness (top)   θ ± 2° (top only)
F and O on TiN                     pillar top              XPS (witness)                 ± 0.3 at%
Killer defects (≥ 154 nm)          ACL, resist             optical darkfield, full wafer  ≥ 100 nm; 90% capture
Missing or blocked openings        top support             e-beam inspection             10 nm pixels; ~ 1 cm²/h-class
Class-linked weak cells            bitmap                  test (retention, bit fail)    cell by cell; 50 fails per signature
```

---

## 15.2 Dimensional Metrology

### 15.2.1 From the Top

After the ACL is stripped, the top of the wafer shows the top-support openings: a plan view of the clover, with the three crescents of TiN in its edge. The CD-SEM measures the circle's diameter at its top edge and the overlap depth of each crescent (the position of the pillar edge against the circle). The measurements are routine, with a precision of 0.3 nm (3σ) on the CD, and they give the top CD and the overlay of the opening against the pillar lattice. The overlap depth, which enters the TiN budget and the collar (Chapters 4 and 11), is derived from the CD and the overlay: 15 + δ + ΔCD/2.

### 15.2.2 The Middle Support Is Not Visible

The middle support is 770 nm below the top, in a column of aspect ratio 17. A top-down SEM does not see it, and the signals (secondary electrons from the column bottom) do not escape. Three approaches remain:

```
Method                      Information                           Limit
────────────────────────────────────────────────────────────────────────────────────────────
Cross-sectional TEM         true profile and CD at every depth    destructive; 5 sites per week; ± 0.5 nm
Scatterometry (OCD)         profile parameters from a model       28% fill, 90 nm pitch; sensitivity to the
                                                                  bottom CD ± 1.5 nm (3σ), correlated with
                                                                  the top CD and the taper
Inference                   mid CD = top CD − 2 × taper           taper from XTEM and the polymer model
```

With OCD at ± 1.5 nm (3σ), the middle-support CD of 44 ± 3.0 nm cannot be confirmed to the 1.0 nm margin on any single wafer. It is controlled through the top CD (measured to ± 0.3 nm), the taper (a function of the polymer and the temperature, held by the tool, Chapters 5 and 6), and a regular XTEM audit of the fleet. The control is therefore **statistical**: the audit finds the fleet mean and its drift, and the wafer-level measurement of the top CD removes the largest component of the spread.

### 15.2.3 Thickness

The top support is measured by ellipsometry on scribe pads after CMP, and the value is fed forward (Section 15.5). The middle support is a buried film. Its thickness is known from the deposition tool's monitor, wafer by wafer, to ± 0.5 nm (3σ) at deposition and not remeasured.

---

## 15.3 Scribe Test Structures

What cannot be measured on the array is measured on structures in the scribe line that go through the same etch.

```
Scribe structures for the support layer etch:
  1. TiN witness pad      Blanket TiN, 20 nm, 200 µm × 200 µm, under a large window in the ACL.
                          Same ion flux, no aspect ratio. Ti Kα by XRF before and after the etch:
                          the loss is the blanket pillar-top loss; the edge loss is about twice it.
                          Resolution ± 0.1 nm.
  2. Nitride-oxide pads   Blanket SiN/SiO₂ on the same window: rates and selectivity (daily monitor).
  3. Deep-hole array      Holes of 45 nm in oxide, depth 770 nm, with the support nitride at the
                          bottom. Cleaved or TEM-sectioned for the polymer at depth, the
                          nitride sliver, and the landing.
  4. Lattice test block   A 100 µm × 100 µm block of the actual 90 nm lattice with pillars, for
                          CD-SEM and XTEM, and for the e-beam inspection reference.
  5. Wetting pad          Hydrophobic-sensitive pad (TiN and oxide) for water contact angle (top surface).
```

The TiN witness is the one the control system runs on. A TiN loss of 3.2 nm on a 20 nm film is a 16% change in the Ti signal; XRF resolves it to ± 0.1 nm, and the witness can be measured on every wafer in the scribe at a cost of seconds.

---

## 15.4 Inspection for Killer Defects

### 15.4.1 How Much Area Must Be Inspected

A killer cluster is a defect with a footprint of about 154 nm (Chapter 4). With a density D_k, finding at least one on a wafer with 95% confidence needs an inspected area

```
A = −ln(0.05) / D_k
  D_k = 0.02/cm²    A = 150 cm²     (0.55 of the 272 cm² of array on a wafer)
  D_k = 0.01        A = 300 cm²     (1.1 wafers)
  D_k = 0.005       A = 599 cm²     (2.2 wafers)
```

An e-beam inspection tool that scans a fraction of a square centimetre per hour cannot do that. An optical darkfield tool at DUV wavelengths that scans a wafer in minutes captures particles above about 100 nm with 90% efficiency and can. **Killer-defect density is therefore measured by full-wafer optical inspection, before and after the ACL open, and not by e-beam**, and the e-beam is used for review and for confirming a single event.

### 15.4.2 Missing Openings

A missing or unopened hole in a 90 nm-pitch lattice is a defect of 50 nm in a periodic pattern. Brightfield optical inspection at this pitch has poor sensitivity for it, and e-beam inspection with large fields and voltage-contrast capability is the tool, applied to the lattice test block and to a few array locations per lot, to confirm that a defect population seen optically corresponds to missing openings.

### 15.4.3 After the Dip-Out

A residue of oxide that has not been removed (Book #30, Chapter 15) shows in e-beam voltage contrast and in optical haze; the support layer etch's contribution is the cluster, and a cluster shows in the same inspection with its footprint. Defect source analysis by the location of clusters (a hot zone at the wafer edge, for polymer wetting; a random distribution, for particles) separates the sources of Chapter 12.

---

## 15.5 Electrical Monitors and the Class Signature

### 15.5.1 Capacitance and Leakage

The array capacitance (8.6 fF per cell) and leakage (< 1 fA per cell) are monitored on array test structures after the plate (Book #32). They do not resolve the top-loss capacitance effect of 0.1% (Chapter 11) and they do resolve a lot-level change in the polymer or oxide layer on the pillar sidewalls of S2 (1%).

### 15.5.2 The Class Signature

The class-aware bitmap analysis of Chapter 11 is the one measurement that connects the support layer etch to yield:

```
Procedure:
  1. Collect the failing cells (retention, bit-fail) per die with their physical addresses.
  2. Map each cell to its pillar class (touched or untouched) using the lattice position
     (a function of position in the 2 × 2 supercell and the measured overlay).
  3. Compute the fraction f_t on the touched sublattice.
  4. Test against 75% (random): z = (f_t − 0.75) / √(0.75 × 0.25 / N).
  5. If z > 3: a class-linked mechanism; examine the TiN loss witness, the flash CF₂ log,
     the junction stress (OX/SN time), and the seam (Chapter 11) for the lots concerned.
```

At 50 fails the test reaches 3.6σ, and at 100 fails 5.1σ. With 14 class-linked weak cells per die in S1 and 900 dies per wafer, the sample is available within a lot.

---

## 15.6 Fault Detection and Virtual Metrology

### 15.6.1 Signals

Every wafer carries a record from the chamber:

```
FDC signals (per wafer, per step):
  OES                    CN/Ar at SN1 and SN2 (EP time, fall width, baseline), CF₂/Ar in the flash
  RF                     V_pp, V_dc, reflected power, matcher positions
  Gas                    flows, pressure, throttle position
  Thermal                ESC zone temperatures, He backside flow
  Time                   step times, endpoint times, overetch times
  Counters               RF-hours of the electrode and ring; wafers since the last clean
```

### 15.6.2 A Virtual-Metrology Model for the TiN Loss

The TiN loss is a function of the flash, the steady rate, and the time. A model fitted to the chamber's data (here written from the physics of Chapter 3) has the form

```
L̂_TiN = 3.22 + 0.0128 × (t_SN − 60 s) + 0.0141 × (t_OX+LAND − 158 s) − 0.39 × (d_f − 1.6 nm)    [nm]

  3.22 nm      reference S1 loss: 0.97 nm in the nitride steps + 2.25 nm in OX and LAND
  t_SN         total SN1 + SN2 etch time (s)    (steady loss 0.766 nm/min = 0.0128 nm/s)
  t_OX+LAND    total OX + LAND time (s)         (loss rate 2.25 nm / 158 s = 0.0141 nm/s)
  d_f          polymer film built in each flash, from the CF₂ integral: d_f = 1.6 nm × (I_CF2/I_ref)
  −0.39        two flashes, each with dL/d(d_f) = −0.96 e^(−1.6) = −0.19 nm per nm of film
```

Its prediction for a wafer with a 5% weaker flash (d_f = 1.52 nm) and SN steps 4 s longer (t_SN = 64 s) is 3.22 + 0.051 + 0.031 = 3.30 nm. The prediction is checked against the XRF witness on one wafer per lot, and the residual is the model error:

```
Residual standard deviation:   0.12 nm
Specification:                 TiN loss ≤ 3.5 nm (S1 reference 3.2 nm)
Margin to the limit:           (3.5 − 3.2) / 0.12 = 2.5σ
```

The virtual metrology provides a score on every wafer, and the XRF witness remains the truth.

---

## 15.7 Advanced Process Control

### 15.7.1 Feed-Forward

```
Feed-forward (wafer by wafer):
  Top-support thickness (ellipsometry after CMP)         → SN1 time:  t_SN1 = (T/120 nm) × 40 s,   OE fixed at 25%
  Middle-support thickness (deposition monitor)          → SN2 / LAND time scaling
  ACL CD after ACL open (CD-SEM)                         → trim time (radical or ALE, Ch. 7):
                                                            1 nm per side (2 nm of CD) takes 6 s of remote NF₃
                                                            (limit 1.5 nm per side on the top-support wall)
  Overlay (litho, to the pillar lattice)                 → recorded; overlap depth computed per die zone
```

The trim is the only CD control available after the mask and it reaches the top support only (Chapter 7). It corrects the part of the CD error that is systematic across the wafer: a radial CD gradient of ± 1 nm can be flattened by a zone-dependent trim, but a mask CD error cannot reach the middle support.

### 15.7.2 Feedback

```
Feedback (lot by lot, EWMA):
  Input                        Target      σ (wafer)   Action
  TiN witness loss (XRF)       3.2 nm      0.12 nm     flash time ± 0.5 s
  SN1 clearing time (EP)       32.0 s      0.5 s       O₂ flow, ESC temperature
  SN2 fall width (CN/Ar)       2.4 s       0.2 s       uniformity: zone temperatures
  Flash CF₂ integral           1.00        0.03        wall state: season; electrode hours
  Ion tilt (edge column)       ≤ 4 nm      0.6 nm      ring replacement
```

An EWMA chart on the TiN witness uses

```
z_k = λ x_k + (1 − λ) z_{k−1},  λ = 0.3
Control limit:  ± L σ √(λ/(2 − λ)) = 3 × 0.12 nm × 0.42 = ± 0.15 nm
Detection:      a sustained shift of +0.2 nm (1.7σ) is flagged in about 5 wafers (average run length)
```

The limits are tight enough to catch a 0.2 nm drift in the TiN loss, which is a 6% change in a quantity that the specification places at 3.5 nm, well before it approaches the limit.

---

## 15.8 The Measurement Ladder

```
Level  What                                  Frequency            Role
─────────────────────────────────────────────────────────────────────────────────────────
1      FDC and virtual metrology             every wafer          score; alarms
2      CD-SEM top CD; ellipsometry; XRF      9 sites per wafer    feed-forward and feedback
       TiN witness; ACL remaining
3      Darkfield inspection (full wafer)     every lot            killer-defect density D_k
4      Scribe structures: contact angle,     one wafer per lot    wetting, selectivity, rates
       blanket rates
5      XTEM: middle CD, fin, landing,        weekly, per chamber  taper, fleet mean and drift
       polymer at depth
6      E-beam inspection of the lattice      weekly               missing openings, review
7      Class-aware bitmap analysis           per lot, at test     the verdict; weeks of delay
```

---

## Summary and Key Takeaways

1. **The middle support cannot be seen from above.** Its CD is inferred from the top CD (± 0.3 nm) and the taper, with a TEM audit and an OCD model at ± 1.5 nm.

2. **The scribe stands in for the array.** A TiN witness pad gives the pillar-top loss to ± 0.1 nm by XRF; a deep-hole array gives the polymer and the sliver at depth.

3. **Killer clusters are seen optically.** Detecting one at D_k = 0.02 per cm² takes 150 cm², more than half a wafer's array; e-beam cannot, and darkfield can.

4. **A virtual metrology model gives the TiN loss within 0.12 nm (1σ).** It uses the flash CF₂ integral, the step times, and the physics of Chapter 3.

5. **The control is EWMA on the witness.** Limits of ± 0.15 nm catch a 0.2 nm shift in about 5 wafers.

6. **The verdict is the bitmap.** Class-aware analysis separates the support layer etch from the other modules at 50 fails (3.6σ).

---

## Study Questions

1. A TiN witness pad loses 3.4 nm and the edge of a crescent loses twice as much as its centre. What are the centre and edge losses in the array, and the radius of curvature of the edge?

2. The detection of one killer cluster with 99% confidence at D_k = 0.01/cm² requires what area? How many wafers of array is that?

3. Using the virtual-metrology model, predict the loss for t_SN = 56 s, t_OX+LAND = 165 s, and a flash with I_CF2 = 1.1 × I_ref. (Expect about 3.2 nm.)

4. For the EWMA with λ = 0.2 and L = 3 on a quantity with σ = 0.10 nm, find the control limit. Compare with λ = 0.3.

5. A bitmap analysis finds 72 class-linked weak cells, of which 64 are on the touched sublattice. What is the z-value against 75%? What would the z-value be for 36 fails with the same fraction?

6. An OCD measurement of the middle-support CD reads 42.5 ± 1.5 nm (3σ) at one site. The top CD is 49.4 nm and the fleet taper is 6.0 nm. What does the inference give, and which of the two estimates would you act on?

---

**Next Chapter:** [Chapter 16: Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
