# Appendix F: Metrology Reference

Methods used for the support layer etch module: what each measures, its precision, its sampling cost, and its main pitfalls. Values are illustrative.

---

## F.1 Dimensional Metrology

```
Method            Measures                          Precision (3σ)   Time/site   Pitfalls
──────────────────────────────────────────────────────────────────────────────────────────────────────
CD-SEM (top-down) top-support opening CD (top      0.3 nm (CD)      ≈ 5 s       charging on nitride and TiN;
                  edge); crescent position;         0.8 nm (overlap)             cannot see the middle support;
                  overlap depth                                                  edge definition on a tapered wall
OCD               profile of the lattice: top CD,   0.3 nm (top CD)  ≈ 3 s       28% fill, 90 nm pitch hex:
(scatterometry)   taper, thickness; middle CD by    1.5 nm (middle                low bottom sensitivity;
                  model                             CD)                          correlated parameters
XTEM / STEM       true profile at every depth:      0.5 nm           hours       destructive; 5 sites per week;
                  middle CD, fin, landing, wall                                  FIB damage on thin walls
                  roughness
Plan-view TEM     middle-support floor: fins,       0.5 nm           hours       sample preparation at a
(at the level)    sliver width and height                                        fixed depth
AFM               top-surface roughness; pillar     0.05 nm rms      ≈ 5 min     small area; tip wear
                  top height (dishing)
CD-SEM tilt       wall angle and striation of the   1 nm             ≈ 10 s      only the top 100–150 nm of a
                  top-support wall                                               45 nm hole
```

---

## F.2 Thickness, Chemistry, and Surface

```
Method              Measures                         Precision (3σ)   Time/site   Pitfalls
──────────────────────────────────────────────────────────────────────────────────────────────────────
Spectroscopic       top SiN thickness (scribe        0.3 nm           ≈ 2 s       damaged skin 3–5 nm biases the fit;
ellipsometry        pads); polymer film on TiN                        (0.1 nm     model must fix n of the polymer
                    (flash monitor)                                   on TiN)
XRF (Ti Kα)         TiN witness loss                 0.1 nm           ≈ 5 s       calibration range 0–20 nm;
                                                                                  pad must see the full ion flux
XRR                 TiN pad thickness, density       0.1 nm           ≈ 5 min     slow; small angle alignment
XPS                 F, C, O on TiN and nitride       0.3 at%          ≈ 10 min    carbon contamination in transfer;
                    (witness); TiO₂ thickness                                      queue-time sensitive
TOF-SIMS / EELS     F and C at depth in sections     ≈ 0.5 at%        hours       destructive; sputter artefacts
                    of deep-hole arrays
Contact angle       polymer coverage on the pad      ± 2°             ≈ 20 s      top surface only; ages with time
(water)
Near-IR             ACL remaining                    2 nm             ≈ 2 s       absorption; stack calibration
interferometry
```

---

## F.3 Defect Inspection

```
Method                Detects                            Capture / sensitivity       Area rate          Use
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Optical darkfield     particles on ACL, resist, wafer    ≥ 100 nm, 90%               minutes per wafer  killer-defect density D_k;
(DUV, full wafer)     (killer footprint ≥ 154 nm)                                                       every lot
Optical brightfield   pattern defects at relaxed pitch   poor at 90 nm pitch hex     minutes            top-level screening
E-beam inspection     missing or blocked openings;       10 nm pixels                ≈ 1 cm²/h-class    confirmation, lattice test block,
(voltage contrast)    residual oxide after dip-out                                                      defect review
SEM review            classification of defects          1–2 nm                      per defect         source analysis
Wafer-edge inspection particles and polymer flakes at    —                           minutes            edge hot-zone mapping
                      the edge
```

Inspection area needed to find one killer cluster with 95% confidence: 150 cm² at D_k = 0.02/cm² (0.55 of the array on a wafer), 300 cm² at 0.01, 599 cm² at 0.005.

---

## F.4 Electrical Monitors

```
Monitor                          Measures                                    Notes
─────────────────────────────────────────────────────────────────────────────────────────────────────
Capacitor array                  C_s (8.6 fF); distribution                  resolves 1% (S2 sidewall), not 0.1%
Array leakage                    < 1 fA per cell at ± 0.55 V, 85 °C          tail by retention test
Retention (bitmap)               weak-cell address, time to fail             class-aware analysis (C.9)
Pillar-to-pillar short chain     leaning or pull-in pairs (S2)               after dip-out and plate
Junction leakage test blocks     touched vs untouched pillar junctions       stress dose from I × t
Plate-edge combs                 Book #33                                     not this module
```

---

## F.5 In-Situ and FDC Signals

```
Signal                    Information                                        Limit / alarm
──────────────────────────────────────────────────────────────────────────────────────────────────────
OES CN/Ar (388.3 nm)      nitride clear (SN1: −85%; SN2: −25%); fall width   EP window 0.6–1.5 × nominal
OES CO/Ar (483.5 nm)      oxide exposure                                      —
OES CF₂/Ar                flash polymer supply; film d_f = 1.6 nm × I/I_ref   ± 10% alarm
OES F/Ar (703.7 nm)       fluorine; arrival at BPSG in S2                     —
RF V_pp, V_dc, reflected  ion energy; coupling; arcing                        ± 5% of recipe
ESC zones, He backside    wafer temperature (± 1 K); clamp                    He leak < 1 sccm
Pressure, throttle        pumping; polymer in the foreline                    ± 3%
HCN monitor               foreline and exhaust                                alarm 2 ppm
Counters                  electrode and ring RF-hours; wafers since the clean 600 h / 300 h; 13,500 wafers
```

---

## F.6 Sampling Plan

```
Per wafer:     FDC and virtual metrology; XRF TiN witness (5 sites); ellipsometry top SiN
Per lot:       CD-SEM 9 sites (top CD, overlap); darkfield full-wafer; ACL remaining
Per lot, one wafer:   contact angle pad; blanket rates; deep-hole wetting check
Per week, per chamber: XTEM (5 sites: middle CD, fin, taper, landing, roughness); edge tilt;
               e-beam on the lattice test block
Per month:     class-aware bitmap review; EWMA σ update; fleet matching
Per quarter:   OCD model re-anchoring with TEM; calibration of XRF TiN and ellipsometry polymer
```

---

**Appendix F Version:** 1.0  
**Last Updated:** 2026-10-05
