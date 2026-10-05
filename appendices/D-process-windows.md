# Appendix D: Process Windows

Reference windows for the support layer etch module. "Target" is the reference process; "window" is the range within which the specification of Chapter 1 is met with the other parameters at target. All values are illustrative starting points for a design of experiments.

---

## D.1 S1 — Nitride Steps (SN1, SN2)

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────
Wafer temperature         40 °C                39–41 °C            rate 2%/K, TiN rate 3.7%/K;
                                                                   polymer d₀ and taper
Pressure                  25 mTorr             22–28 mTorr         uniformity; polymer supply
Source power (60 MHz)     1.8 kW               1.6–2.0 kW          ion flux; rate
Bias (2 MHz) mean energy  400 eV               300–500 eV          mask margin / time (low);
                                                                   TiN rate, mask rate (high)
Gas CH₂F₂ / CF₄ / O₂ / Ar 20 / 25 / 18 / 300   O₂ ± 2 sccm         d₀ 3.4 ± 0.3 nm; SiN rate −3%/sccm
Polymer on TiN (d₀)       3.4 nm               3.1–3.7 nm          rate ± 17%; stall at d₀ > 5 nm
SN1 time (incl. 25% OE)   40 s                 36–44 s             top-support clear (low);
                                                                   oxide loss 20 nm at 25% OE (high)
SN2 time (S0/S1)          20 s                 18–23 s             clear (low); LAND supplies the 40% OE
Overetch SN1 / SN2        25% / 40%            ≥ 25% / ≥ 30%       fin width ≤ 4 nm (99.9th percentile)
Endpoint                  CN/Ar fall (SN1);    —                   —
                          arrival rise (OX)
```

---

## D.2 S1 — Polymer Flash (FL1, FL2)

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────────
Gases                     CH₃F 40 / Ar 300     CH₃F 35–45          film rate 0.4 nm/s
Pressure                  20 mTorr             18–22 mTorr         uniformity
Source power              0.6 kW               0.5–0.7 kW          polymer supply
Bias                      none                 0 (no stray)        TiN sputtering during the flash
Time                      4 s                  3–6 s               transient loss +0.16 nm at 3 s;
                                                                   throughput −3.4 s per step
Film on TiN               1.6 nm               1.45–1.75 nm        transient 0.16 nm (0.05–0.4 nm)
Gas switching             ≤ 1 s to 90%         —                   fraction of the 4 s lost
CF₂ integral              I_ref ± 5%           ± 10% (alarm)       wall state, consumables
```

---

## D.3 S1 — OX and LAND (Pulsed)

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────────────
OX gases                  C₄F₆ 15 / O₂ 30 / Ar 400   O₂ ± 3 sccm   polymer, Ox:ACL ≈ 5
Pressure                  20 mTorr             18–22 mTorr         profile
Source / bias             2.2 kW / 600 eV      2.0–2.4 kW          rate; TiN loss
Pulsing                   10 kHz, 80%          5–20 kHz; 70–90%    re-ignition (< 5 kHz); rate (low duty)
OX time                   129 s                118–140 s           middle-support arrival + 1–10 s OE
LAND gases / energy       C₄F₆ 12 / O₂ 28 / Ar 400, 500 eV   —     landing depth
LAND time                 29 s                 26–33 s             landing 50–150 nm; mask (high)
Wafer temperature         38 → 43 °C           ± 2 K               rate, selectivity
ACL consumed (all steps)  253 nm               ≤ 260 nm            margin ≥ 40 nm of 300 nm
```

---

## D.4 S1 — Post-Etch Treatment

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────────────
Stage 1 gas / energy      O₂/Ar, 100 eV        80–120 eV           TiN oxidation (high);
                                                                   polymer at the bottom (low)
Stage 1 time              10 s                 8–15 s              φ at 770 nm ≤ 0.31 (low);
                                                                   TiN oxide +0.9 nm at 10 s (high)
Stage 2                   O₂/N₂ downstream, 200 °C, 40 s   35–50 s ACL strip; TiN oxide 1.4 nm
Pre-wet (dip tool)        5–10 s dilute HF or     —                  column fill; Book #30
                          DI with surfactant
Queue before dip          ≤ 4 h                —                    contact angle rises beyond
```

---

## D.5 S2 — Sequential Route (S2D and S2A)

```
Parameter                 S2D target           S2A target          Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────────────
Support / upper oxide     SiCN / PSG           SiCN / PSG          ligament margin ≥ 1.08 after both dips
ACL                       220 nm               220 nm              163 nm used (SiCN), margin ≥ 40 nm
SN1                       4 s flash + 72.7 s   same                top-support clear; 25% OE
Dip 1                     178 s (PSG, 5% HF)   178 s               ≤ 1.2 nm per wall in both dips
SN2 ion energy            600 eV               600 eV              cleared width ≥ 40 nm (40.5 nm)
SN2 ion flux fraction     1.0                  0.16                ΔV ≤ 4 V (S2A); every pillar touched (S2D)
SN2 time                  4 s flash + 37.7 s   4 s + 102 s         40% OE; junction stress dose
Post-SN2 strip            O₂/N₂ downstream, 50 s, 200 °C           TiO₂ ≤ 1.6 nm on the free pillars
Dip 2                     105 s (BPSG)         105 s               bottom stop loss ≤ 0.5 nm
Free-pillar potential     ± 1.5 V              4.1 V               pull-in 7.1 V (intermediate), 5.5 V (pinned)
```

---

## D.6 Radical Trim (Remote NF₃)

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────────────
Gases                     NF₃ 200 / O₂ 100 / Ar 500   —             F atom flux
Pressure / power          1.5 Torr / 3 kW remote       —            uniformity
Wafer temperature         40 °C                30–60 °C            SiN rate 7.4–13 nm/min
SiN rate                  10 nm/min            —                   isotropic
SiN:SiO₂                  12                   ≥ 10                oxide loss ≤ 0.15 nm
Trim per side             1.5 nm (9 s)         ≤ 1.5 nm            ligament margin (CD ≤ 53 nm etched)
Reach                     top 150–350 nm       —                   12% dose at 770 nm (s = 0.005)
TiN                       1.5 nm F skin        —                   removed in dip; ≤ 1.5 nm
```

---

## D.7 Plasma ALE of Nitride

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────────────
Step A                    CH₃F/Ar, 1.5 s, no bias   ≥ 1.0 s        saturation of the modified layer
Step B ion energy         35 eV                25–45 eV            below TiN threshold (45 eV);
                                                                   above SiN threshold of the modified layer
Step B time (top)         3 s                  ≥ 2 s               ion dose
Step B time (middle, 770 nm)   21.6 s          —                   14% of ions reach the bottom
Purges                    0.5 s each           ≥ 0.3 s             cross-talk
EPC                       0.5 nm/cycle         0.4–0.6             —
Cycle time                5.5 s (top)          —                   rate 5.5 nm/min (top); 1.2 nm/min (middle)
```

---

## D.8 Hot Phosphoric Acid (Wet Option)

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────────────
Bath temperature          160 °C               155–165 °C          rate ± 8%
Time (1.5 nm trim)        18 s                 15–21 s             TiN 0.24 nm; opening +3 nm
Silicon in the bath       < 100 ppm            —                   silica precipitation in 17 nm gaps
Pre-condition             polymer-free walls (θ ≤ 30°)               wetting (Ch. 9)
Drying                    embedded pillars only (S0/S1)              S2: adds a dry
```

---

**Appendix D Version:** 1.0  
**Last Updated:** 2026-10-05
