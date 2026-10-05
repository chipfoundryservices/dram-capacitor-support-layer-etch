# Appendix C: Standard Procedures

Step-by-step procedures for qualifying and monitoring the support layer etch module (route S1; additions for S2 are marked). Each procedure lists purpose, materials, steps, and acceptance criteria. Values are illustrative.

---

## C.1 S1 Chamber Qualification

**Purpose:** Qualify a support layer etch chamber after installation or wet clean.

**Materials:** 30 seasoning wafers (blanket PECVD SiN 120 nm on oxide, no pattern); monitor wafers: blanket PECVD SiN (120 nm), PE-TEOS (650 nm), BPSG (760 nm), blanket TiN (20 nm); 3 full-structure wafers (planarized pillar array with ACL mask, scribe structures of Chapter 15); 1 particle wafer.

**Steps:**
1. Bake the chamber at wall temperature (80 °C) for 4 h after pump-down. Verify ESC zones at 35 °C setpoint and wafer temperature of 40 ± 1 K under a standard plasma (thermocouple wafer).
2. Run waferless clean, then the season step (CH₃F/Ar, 10 s with a cover wafer), then 6 seasoning wafers through the full recipe, until the SN rate and the flash CF₂ integral on two consecutive wafers are within 2% of the fleet reference.
3. Measure blanket rates at 49 sites in the SN chemistry (30 s): SiN, PE-TEOS, BPSG, TiN (XRF).
4. Run the flash on blanket TiN (4 s, no bias): measure the polymer film by ellipsometry on the TiN.
5. Run the particle wafer (full recipe, no film).
6. Run 3 structure wafers. Record OES (CN/Ar fall time and width; CF₂/Ar in the flash), V_pp, step times, wafer temperature trace.
7. On structure wafers: CD-SEM (9 sites, top CD and overlap depth), ellipsometry (top SiN remaining), XRF TiN witness, XTEM (centre and edge: middle-support CD, fin, landing depth, taper, polymer by EELS), contact angle on the wetting pad.
8. Compare with the fleet reference.

**Acceptance:**
```
SiN rate 225 ± 7 nm/min (SN); uniformity ≤ 1.5% (1σ); SiN:SiO₂ 1.5 ± 0.1
TiN steady rate ≤ 0.85 nm/min; TiN witness loss (SN steps) 0.97 ± 0.15 nm
Flash film 1.6 ± 0.15 nm; flash CF₂ integral within ± 5% of fleet
Top CD 50 ± 1 nm after ACL strip (3σ ≤ 2.7 nm); overlap depth ≤ 20 nm at 3σ
Middle-support CD ≥ 41 nm at every sampled site; taper 6.0 ± 0.8 nm
Fin width (99.9th percentile) ≤ 4 nm; landing depth 100 ± 15 nm
Ion tilt: edge column offset ≤ 4 nm at 150 mm radius
Particles ≤ 10 adders ≥ 30 nm; no cluster of adders ≥ 100 nm
```

---

## C.2 Daily Monitor

**Purpose:** Detect drift in rate, polymer film, and selectivity.

**Steps:**
1. Run one blanket PECVD SiN, one PE-TEOS, and one TiN monitor in the SN chemistry for 30 s (with a 4 s flash).
2. Measure 49 sites by ellipsometry (SiN, PE-TEOS) and XRF (TiN).
3. Log OES CN/Ar and CF₂/Ar.

**Acceptance:**
```
SiN rate within ± 3% of the chamber baseline; uniformity ≤ 2% (1σ)
SiN:SiO₂ 1.5 ± 0.15; TiN loss in 30 s with flash 0.55 ± 0.1 nm
Centre-to-edge SiN rate within ± 2% (ring wear indicator)
CF₂ integral in the flash within ± 5%
```

---

## C.3 Flash Calibration

**Purpose:** Set the flash time and verify the film it builds.

**Steps:**
1. On blanket TiN (20 nm) run flash times of 0, 2, 4, 6, 8 s with no bias; measure the polymer thickness by ellipsometry (± 0.1 nm).
2. Repeat followed by a 20 s SN step; measure the TiN loss by XRF.
3. Fit the film thickness against flash time (target slope 0.4 nm/s) and the TiN loss against flash time (target 1.07, 0.57, 0.36, 0.28, 0.26 nm in 20 s at 0, 2, 4, 6, 8 s).
4. Set the flash time that gives 1.6 nm; record the CF₂ integral as I_ref.

**Acceptance:** film 1.6 ± 0.15 nm at 4 s; TiN loss in 20 s ≤ 0.40 nm; fit residual ≤ 0.05 nm.

---

## C.4 Seasoning After a Clean

**Purpose:** Remove the first-wafer effect (Chapter 9).

**Steps:**
1. After a waferless clean or a wet clean, run the season step: CH₃F/Ar, 10 s, with a cover wafer.
2. Run one production-recipe wafer on blanket SiN and measure the SN rate.
3. If the rate exceeds baseline by more than 2%, repeat the season and re-measure.

**Acceptance:** first-wafer SiN rate within 2% of the fleet; TiN loss within 0.1 nm of the fleet.

---

## C.5 TiN Witness Measurement

**Purpose:** Measure the pillar-top loss every wafer.

**Steps:**
1. Before the etch, measure Ti Kα on the scribe TiN pad (20 nm, 200 × 200 µm) by XRF, 5 sites.
2. After the etch and the strip, measure the same sites.
3. Convert the intensity ratio to nm using the calibration (Ti signal ∝ thickness for 0–20 nm).
4. Log the loss; update the EWMA (λ = 0.3).

**Acceptance:** loss 3.2 ± 0.12 nm (1σ); EWMA within ± 0.15 nm of 3.2 nm; measurement precision ± 0.1 nm.

---

## C.6 Deep-Hole Wetting and Polymer Qualification

**Purpose:** Verify that the strip cleans the bottom of the column.

**Materials:** scribe deep-hole arrays (45 nm holes, 770 nm depth, oxide walls, nitride base); wetting pads.

**Steps:**
1. After the etch and strip, measure the water contact angle on the wetting pad (top surface).
2. Section a deep-hole array by FIB; measure F and C by EELS or TOF-SIMS at depths of 50, 400, and 750 nm. Convert to polymer coverage φ (calibrated against pads of known coverage).
3. Run a short HF pre-wet dip (5 s) on a sister wafer and inspect the array for unfilled holes (optical contrast or SEM after sectioning).

**Acceptance:**
```
Contact angle on the pad ≤ 30°
φ at 750 nm ≤ 0.31 (mean); σ ≤ 0.08;  φ at the wafer edge ≤ 0.31
Unfilled holes in the pre-wet test: 0 of 10⁴ inspected
```

---

## C.7 Sliver and Profile Audit

**Purpose:** Measure the middle-support opening and the fins weekly per chamber.

**Steps:**
1. XTEM (or plan-view TEM at the middle-support level) at 5 sites (centre, mid-radius, edge at four angles).
2. Measure the middle-support CD, taper, fin width and height at the crescent corners (≥ 50 corners), landing depth, and wall roughness.
3. Fit the fin-width distribution; read the 99.9th percentile.
4. Log the fleet mean and drift.

**Acceptance:** middle-support CD ≥ 41 nm; taper 6.0 ± 0.8 nm; fin width 99.9th percentile ≤ 4 nm and no continuous nitride film; wall roughness ≤ 1.5 nm (3σ).

---

## C.8 Ion Tilt (Edge Column Offset)

**Purpose:** Detect edge-ring wear.

**Steps:**
1. Section columns in the scribe at radii of 0, 100, and 148 mm.
2. Measure the offset of the bottom of the column relative to the top, along the radial direction.
3. Convert to tilt: θ = atan(offset/770 nm).

**Acceptance:** offset ≤ 4 nm (0.3°) at 148 mm; replace the ring if the offset exceeds 3 nm.

---

## C.9 Class-Aware Bitmap Analysis

**Purpose:** Test whether a failing-cell population is class-linked.

**Steps:**
1. Collect the failing cells (retention, bit-fail) per die with their physical addresses; N ≥ 50.
2. Assign each cell to the touched or untouched class from its position in the 2 × 2 supercell and the measured overlay offset.
3. Compute f_t = (fails on touched sublattice) / N and z = (f_t − 0.75)/√(0.75 × 0.25/N).
4. If z > 3, flag the lot; review the TiN witness, the flash CF₂ log, OX/SN times (junction stress), and the seam audit.

**Acceptance:** z ≤ 3 for the lot's weak-cell population; class-linked weak cells ≤ 14 per die.

---

## C.10 EWMA Setup and Maintenance

**Purpose:** Run the lot-to-lot feedback of Chapter 15.

**Steps:**
1. For each controlled variable (TiN witness loss, SN1 clearing time, SN2 fall width, flash CF₂ integral, edge tilt) set the target and the wafer σ from 100 baseline wafers.
2. Compute the EWMA with λ = 0.3; limits ± 3σ√(λ/(2 − λ)) = ± 1.26σ.
3. On an out-of-limit point: hold the lot, check the chamber (C.1 items), correct, requalify.
4. Recompute σ quarterly and after any hardware change.

**Acceptance:** false-alarm rate ≤ 1 per 300 wafers; detection of a 1.7σ shift in ≤ 5 wafers.

---

## C.11 Additions for S2

**C.11.1 Cleared-width check.** After SN2 and the dip, XTEM the middle-support opening at five sites; the cleared width at 600 eV must be ≥ 40 nm (model: 40.5 nm). If the width is below 40 nm, raise the ion energy in SN2 by 50 eV steps or request a larger top opening, within the 47–53 nm window.

**C.11.2 Charging check.** On test lattices with every pillar touched and with 75% touched, run SN2 and the dip; inspect by SEM for pillar pairs touching. Zero touching pairs at the S2D lattice and at S2A with the reduced flux.

**C.11.3 Dip-1 loss.** XTEM the top-support wall after dip 1 and after dip 2: loss ≤ 0.9 nm per wall (SiCN, dip 1) and 1.2 nm total; final CD ≤ 53 nm; ligament margin ≥ 1.08.

**C.11.4 Sidewall check.** XPS of the pillar sidewalls at 100 nm and 500 nm from the top (cleaved structures): F ≤ 3 at% at 100 nm; TiO₂ ≤ 1.6 nm.

---

**Appendix C Version:** 1.0  
**Last Updated:** 2026-10-05
