# Appendix G: Troubleshooting Guide

Symptom-driven guide for support layer etch excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 TiN Witness Loss High (Above 3.5 nm in S1)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Flash film thin or missing              CF₂ integral in the flash; FL step  Restore flash; check CH₃F
   (Ch. 3.5, 6.6)                          log; MFC response                   MFC; reseason
2. Gas switching slow: flash short in      MFC settling log (90% time)         Retune the gas delivery;
   effect (Ch. 5.4)                                                            lengthen the flash by 1 s
3. SN or OX time too long                  Endpoint times; step log            Check EP logic, rate drift
   (Ch. 6.6, 15.6)
4. Hot wafer (ESC offset)                  Thermocouple wafer; He backside     Recalibrate ESC; fix He leak
   (Ch. 3.4.2)
5. Film d₀ low after wall change           First-wafer effect; electrode hours Season; adjust O₂ flow
   (Ch. 5.5, 9.2)
```

## G.2 Nitride Rate Drifting

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Electrode or ring wear: d₀ falls        RF-hours; CF₂ integral; rate trend  Replace parts; lower O₂ to
   (Ch. 5.5)                               (+27% for −0.4 nm)                  restore d₀ (−3 sccm)
2. Wafer temperature offset                Thermocouple; ESC zone logs         Recalibrate
   (2%/K, Ch. 3.4.2)
3. First-wafer effect after a clean        Rate of wafer 1 vs wafer 6          Add or lengthen the season
   (Ch. 9.2.2)
4. Incoming film: H or thickness           Deposition logs (H +4 at% → +16%)   Feed forward; recheck monitors
   (Ch. 2.2)
```

## G.3 Middle-Support CD Low (< 41 nm)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Mask CD low                             CD-SEM top CD; ACL CD log           Correct litho; radical trim
   (Ch. 10.1)                                                                  top only; reject lot if < 47 nm
2. Taper steeper: more polymer, cooler     XTEM taper; flash and O₂ settings;  Reduce polymer; raise ESC
   wafer (Ch. 10.2.1)                      ESC temperature                     setpoint within the window
3. Ion energy low                          V_pp, V_dc; mean energy log         Restore energy (+100 eV: +0.3 nm)
4. Residual nitride / fin wide             Fin audit (Ch. 12)                  Lengthen SN2 OE; check f₀
5. S2: cleared width < 40 nm               Cleared-width test (C.11.1)         Raise SN2 energy to 600 eV
   (Ch. 10.6)
```

## G.4 Clusters of Low Capacitance at the Wafer Edge

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Polymer at the column bottom, thicker   Deep-hole φ at 750 nm; edge θ map   Lengthen the ion flush; raise
   at the edge (Ch. 9.5)                                                       edge temperature; check ring
2. Ring wear: ion tilt, edge column        Edge offset (C.8); XTEM edge        Replace ring
   offset (Ch. 5.5.2, 10.5)
3. Edge zone cooler: thicker polymer       ESC zone logs; thermocouple wafer   Retune zone offset
   (Ch. 3.4.2)
4. Edge particles, flakes                  Wafer-edge inspection               Clean; check edge ring coating
```

## G.5 Clusters at Random Positions (10–100 Cells)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Resist or mask defects: missing         Pre-etch darkfield; e-beam review   Hold litho; requalify mask
   openings (Ch. 4.5, 12.6)                of lattice block
2. Killer particles ≥ 154 nm on ACL        Darkfield (before and after ACL     Source analysis; clean
   (Ch. 4.5, 9.3)                          open)
3. Polymer plug or flake in the column     Defect review; polymer in forelines Chamber clean; check wall
   (Ch. 9.3, 12.5)                                                              polymer limit (1 µm)
4. Trapped gas in unfilled columns         Deep-hole pre-wet test              Lengthen pre-wet; surfactant;
   (Ch. 9.4)                                                                    ion flush
```

## G.6 Class-Linked Weak Cells (97% on the Touched Sublattice)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. TiN top loss or open-seam slot          TiN witness; XTEM of crescent;      Fix flash, step times;
   (Ch. 11.3–11.4)                         seam audit                          reduce overlap depth
2. Junction stress from long exposure      OX/SN time log; I × t dose          Shorten steps; route S2 if the
   (Ch. 13.3)                                                                  mask allows
3. F-delayed ZAZ nucleation                XPS F on TiN (> 3 at%)              Longer ion flush; check strip
   (Ch. 11.5.2)
4. Overlay: large overlap depth            CD-SEM overlap depth at 3σ          Correct overlay; trim; recentre
   (Ch. 4.3.2)
```

## G.7 First-Wafer Effect After a Clean

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Walls clean and fluorinated             SiN rate wafer 1 vs 6 (+9.4%)       Add or lengthen the season
   (Ch. 9.2.2)
2. Season step skipped                     Recipe log                          Re-enable season
```

## G.8 Cracks or Ligament Failures After the Dip-Out

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Etched CD too large: ligament margin    CD-SEM top CD (> 53 nm); XTEM       Reduce CD; no trim
   < 1.08 (Ch. 4.6)                        final CD after the dip
2. Edge roughness high (striations)        Wall roughness (> 1.5 nm 3σ)        Resist/ACL open; flash
   (Ch. 10.4)
3. Support film more HF-soluble            HF rate monitor (+7% per at% H);    Feed back deposition; recheck
   (Ch. 2.2)                               thermal history                     TiN fill temperature
4. Dip too long (cluster tolerance chased) Dip time log                        Limit to the budget (loss ≤ 2 nm)
   (Ch. 4.4.3)
```

## G.9 S2: Pillars Touching After SN2 or Dip 2

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Electrostatic pull-in during SN2        Ion flux (source power); ΔV model   Cut flux to ≤ 16% (S2A);
   (Ch. 13.4)                              (> 7 V); all-touched lattice?       use S2D lattice
2. Capillary collapse in the dry           Book #30 collapse margin            Supercritical CO₂; lower surface
                                                                               tension
3. Free-span too long for the pillar       Span (> 650 nm at 1b)              Add a support (S3)
   (Ch. 14.5)
4. Queue condensation between dip 1 and    Queue time; humidity               Purged FOUP; ≤ 4 h
   SN2 (Ch. 16.2)
```

## G.10 Polymer Residue and Poor Wetting

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Ion flush shortened or disabled         Strip recipe; bias log              Restore 10 s at 100 eV
   (Ch. 9.5.3)
2. Radical dose low (high wall loss s)     Deep-hole φ at 750 nm               Raise ion flush time to 15 s
3. Queue time > 4 h                        Queue log; contact angle             Re-strip; longer pre-wet
4. Polymer thicker than d₀ (O₂ low)        Flash and SN d₀; OES H_α            Restore O₂; check temperature
```

## G.11 Particles

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Wall polymer flakes (> 1 µm)            Wafers since the clean (> 13,500); Wet clean; shorten interval
   (Ch. 9.2)                               adders by size
2. Coating spall (Y₂O₃/YOF)                Particle EDS (Y, O, F)              Replace coated parts
3. Foreline or pump back-streaming          Foreline temperature; HCN polymer   Heat the foreline; purge
   (Ch. 9.1.2)
4. Mask fragments (ACL)                    Particle EDS (C); ACL margin        Check mask margin; strip chemistry
```

## G.12 HCN or Exhaust Alarm

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Burn-box or scrubber fault              Abatement status; pressure drop     Stop wafers; service abatement
2. Foreline leak                           Leak check; pressure                Stop; repair
3. Stuck-open gas valve (CH₂F₂ / CH₃F)     Flow log; valve state               Stop gas; isolate; investigate
(Always: treat an HCN alarm as a safety event first and a process event second.)
```

---

**Appendix G Version:** 1.0  
**Last Updated:** 2026-10-05
