# Book #34: DRAM Capacitor Support Layer Etch — Cutting the Nitride Lattice Between Metal Pillars, Selective Plasma Chemistry, and Sequential Release of Multi-Support Molds

## Overview

**Book #34** is a technical reference on **DRAM capacitor support layer etch**: the plasma etches that perforate the silicon nitride support layers of the pillar mold. A TiN storage-node pillar 1.6 µm tall and 28 nm wide cannot stand alone through a wet process, so the mold carries a **top support** (120 nm) and a **middle support** (50 nm) of silicon nitride that tie every pillar to its neighbours and cut its free span below 800 nm. A solid sheet would hold the pillars and imprison the mold. The oxide around the pillars is what must be removed, and hydrofluoric acid can reach it only through holes. So each support is perforated: about **4.25 billion openings per layer on a 16 Gb die**, each 50 nm wide, on a 90 nm hexagonal lattice, each placed between pillars so that it overlaps three of them. Cutting them is the support layer etch.

Book #30 (*DRAM Capacitor Mold Etch*) treats the support open as the first half of a module that ends in the HF dip-out, and takes the supports mainly as a mechanical skeleton. This book takes the other view. **The support layer is a film to be etched**: a hydrogen-bearing PECVD nitride with a thermal history, patterned by a mask with a placement error, cut by a plasma that must spare titanium nitride on one side of the opening and oxide below it, and left in the finished capacitor with whatever the etch did to its edges. Where Book #30 asks how many pillars the lattice holds, this book asks **how many openings fail, why, and how anyone would know**.

Four things make the etch hard. **There is metal in the wall**: three TiN crescents form a third of every opening's wall, facing the plasma for the whole etch. **The landing is thin and buried**: the middle support is 50 nm, 770 nm down a column at aspect ratio 17, with oxynitride at both ends. **The film is permanent**: its edges, composition, and surface chemistry are part of the capacitor. **The count is enormous**: the question is not whether the etch works on average but whether a cluster of three adjacent failures ever strands oxide.

Every liquid, vapor, and precursor that touches the pillars afterwards goes through these openings: HF, rinse, drying fluid, the ZAZ precursors, the top electrode. The opening is the only door.

**Cut four billion doors in a nitride sheet, between metal pillars, and leave none closed, none cracked, and none contaminated.** This book covers the chemistry, equipment, process phenomena, and production engineering of doing that.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing hydrofluorocarbon nitride steps with a polymer flash; controlling TiN pillar-top loss, opening CD, nitride fins, polymer at the bottom of the column, and landing in the lower oxide
- **Equipment Engineers**: specifying CCP chambers for nitride etch, fast gas switching, seasoning, endpoint on a 50 nm film, hydrogen cyanide abatement, and remote-plasma and ALE reactors for trimming
- **Integration Engineers**: choosing the lattice (pitch, opening size, orientation), the support film (SiN, SiCN, SiBN), the number of supports, and between the one-pass route and the sequential routes for taller molds
- **Device Engineers**: understanding how top loss, fluorine, junction charging, and stranded oxide become low capacitance, retention tails, and clusters, and why the weak cells fall on a 3:1 pattern
- **Researchers**: studying polymer-film models of selectivity, radical and ion transport in 50 nm columns, electrostatic pull-in of free-standing pillars, and support layers for 4F² and 3D DRAM

The material assumes Books #1–5 (plasma fundamentals), Books #6–10 (dielectric etch), and Books #11–15 (advanced plasma engineering). **Book #30 (*DRAM Capacitor Mold Etch*)** is the direct predecessor: it defines the mold, the supports, the support-open recipe, and the HF dip-out that this book takes as given. Book #29 (*DRAM Capacitor Hole Etch*) and Book #31 (*DRAM High-Aspect-Ratio Capacitor Etch*) cut the holes the supports tie together; Book #32 (*DRAM Capacitor Electrode Etch*) and Book #33 (*DRAM Capacitor Dielectric Etch*) follow. The companion volumes *Silicon Nitride Etch*, *Etch: The Sub-Nanometer Chisel*, and *Carbon Hard Mask Etch* cover related chemistry and the mask in more general settings.

---

## Technical Scope

### Core Concepts Covered

**Function & Films:**
- What the supports do, and why the opening is the only door for every later process
- The support film: PECVD low-H SiN after the TiN fill; hydrogen, stress, interfaces, and the incoming CMP surface
- Families of supports (SiN, LPCVD, PEALD, SiCN, SiBN, SiON) and the trade between HF resistance and plasma etchability
- The lattice as a design object: pitch, size, placement, five layouts, and the lithography each needs

**Etch Chemistry:**
- Fluorine on nitride, oxide, and TiN: thermochemistry and the involatile TiF₄ that passivates the pillar
- Hydrofluorocarbon chemistry: hydrogen, nitrogen removal as HCN, polymer consumption by each surface
- The polymer-film model of selectivity; steady selectivity 294 and effective selectivity 93; the transient and the flash
- Radical, atomic-layer, and wet nitride removal: what each can trim, and how far it reaches into a column

**Equipment Design:**
- CCP chambers: frequency, sheath, ion transit, chamber memory between steps, consumable wear and polymer thickness
- Selectivity levers: energy, distribution width, pulsing, temperature; sensitivity at constant nitride cleared
- Endpoint on 1.6 sccm of nitrogen: CN emission, why interferometry fails, what an endpoint can and cannot do
- Walls, polymer, particles, seasoning, and the post-etch strip that must clean the bottom of a 50 nm column

**Process Phenomena:**
- Opening profile, taper, and CD budget; the free area of the three-lobed clover; the opening in a free cavity as an ion image
- Pillar-top loss, edge rounding, open seams, fluorine, and the two classes of cells (touched, untouched)
- Slivers, micromasks, and not-open events; the stranded-oxide budget
- Charging of floating pillars, junction stress, electrostatic pull-in of free-standing spans
- Opening statistics: reach, empty circles, killer clusters, and the killer-defect footprint

**Production Integration:**
- Sequential routes (S2, S3), HF-resistant supports, pre-opened lattices, 4F² and 3D DRAM
- Metrology: the ladder from CD-SEM to the class-aware bitmap; scribe test structures; killer-defect inspection area
- Feed-forward, EWMA feedback, and virtual metrology of TiN loss
- Yield signatures, equipment sizing for 150,000 wafer starts per month, cost of ownership, break-even yield

### Technology Context

- **Device architectures:** 6F² buried-channel DRAM from the 1x to the 1d generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel and 3D DRAM as emerging forms
- **Support structures:** two nitride supports and a bottom stop (primary focus); three-support lattices for 2.1 µm molds; four supports at 4F²
- **Process sequence:** The support layer etch follows storage-node separation and top isolation (Book #32, module 1) and precedes the HF dip-out (Book #30), the ZAZ ALD (Book #33), the top electrode, and the plate etch (Book #32)
- **Manufacturing scale:** 300 mm wafers; one support layer etch of about 4 min (S1) and one dip-out per wafer

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The Support Layer & Why It Is Etched**
- What the supports do; 4.25 × 10⁹ openings per layer per die
- The opening as the only door; the free area as it closes during ZAZ and top electrode
- Why one pillar in four is never touched; where the etch sits in the flow
- The routes S0, S1, S2, S3, and P; the specification sheet

**Chapter 2: The Support Film — Nitride Families, Stack, Incoming Surface & Etch Behaviour**
- PECVD low-H SiN after the TiN fill; hydrogen and thickness effects on plasma and HF rates
- The stack the etch crosses, and the soft ends of the middle support
- The incoming surface: CMP skin, TiON, dishing, seams
- SiCN, SiBN, SiON, PEALD: what resists HF resists the plasma

**Chapter 3: Plasma Chemistry of Nitride Etching Between Metal Pillars**
- Bonds, products, and the volatility rule; why fluorine passivates TiN
- Hydrofluorocarbon chemistry and the polymer-film model
- Ion energy and its distribution as weak levers
- The transient, and the flash that removes 83% of it

**Chapter 4: Lattice Design, Pattern Transfer & Opening Statistics**
- Five lattice layouts; lithography, overlay, and the overlap depth at 3σ
- Reach, largest empty circles, and the killer cluster; dip time buys cluster tolerance
- Correlated failures: the killer-defect footprint and yield
- Ligaments, roughness, and the upper CD limit

### Part II: Hardware Design (5 Chapters)

**Chapter 5: CCP Chambers for the Nitride Lattice Open**
- Sheath, ion transit, and the choice of frequency
- Chamber memory between steps; the full S1 recipe
- Consumable wear and the polymer film; edge-ring tilt
- Throughput, matching, and hydrogen cyanide abatement

**Chapter 6: Ion Energy, Bias Pulsing & Temperature — The Selectivity Levers**
- Energy sweep; the width of the distribution (a negative result)
- Pulsing: duty, frequency, and what to pulse
- Wafer temperature through the recipe; the flash as a soak
- The sensitivity table at constant nitride cleared

**Chapter 7: Radical, Atomic-Layer & Wet Nitride Removal — Trim, Finish & Stencil Routes**
- Remote NF₃ etching and the TiF skin; the reach of radicals into a column
- Plasma ALE and ion starvation at depth
- Hot phosphoric acid; matching tools to jobs

**Chapter 8: Endpoint & In-Situ Monitoring of a Thin Nitride in a 50 nm Opening**
- Nitrogen as the marker; signals at the four transitions
- Why interferometry fails; what an endpoint is worth
- The flash as a sensor; endpoint logic

**Chapter 9: Walls, Polymer, Particles & Post-Etch Clean**
- Polymer inventory; waferless clean, first-wafer effect, seasoning
- Particles and the killer-defect budget
- Polymer coverage, contact angle, and the strip's reach into the column
- Wetting statistics and TiN oxidation

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Opening Profile, CD & Pattern Fidelity**
- The column from mask to landing; the CD budget at the middle support
- Taper, the interface step, and the free area of the clover
- Roughness, overlay and tilt, landing depth
- The opening in S2 as an ion image

**Chapter 11: The Pillar Tops — TiN Loss, Two Classes of Cells & Fluorine Uptake**
- The crescent; capacitance cost of the loss; edge rounding and field
- The open seam; touched and untouched pillars
- The weak-cell budget; the class signature in the bitmap

**Chapter 12: Slivers, Scum & Not-Open Openings — Residue Statistics**
- The corner and the fin; sliver width versus overetch
- Not-open events are micromasks, not tails
- The stranded-oxide budget

**Chapter 13: Charging, Electrostatics & Free-Standing Pillars in the Plasma**
- Ion current, charging time, and the junction clamp
- What pulsing and the waveform cannot do
- Junction stress in S0/S1; pull-in in S2; flux reduction or an all-touched lattice

**Chapter 14: Advanced Schemes — Sequential Opens, Three-Support Molds, HF-Resistant Supports, Pre-Opened Lattices, 4F² & 3D DRAM**
- The HF selectivity a sequential route needs; loss, final CD, and ligament margin
- Free-pillar fluorination; S2D and S2A
- Three supports at 1d-class; the pre-opened lattice; 4F² and 3D DRAM

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Metrology, Inspection & Advanced Process Control**
- The measurands, the scribe test structures, and the middle support that cannot be seen
- Killer-defect inspection area; virtual metrology; EWMA
- The class-aware bitmap analysis

**Chapter 16: Integration, Yield & Cost of Ownership**
- Customers, queue times, and yield signatures
- Equipment for 150,000 wafer starts per month; cost of ownership
- Break-even yield gain; new-product checklist

---

## Key Technical Themes

1. **The opening is the only door.** 4.25 × 10⁹ per layer per die; after ZAZ the free area is 20–28% of its etched value, and the top electrode closes it. Nothing reaches the pillars except through them.
2. **The lattice forgives randoms and punishes clusters.** A single failed opening, a pair, or a row of three costs nothing; a triangle strands oxide unless the dip is lengthened. Independent failures of 10⁻⁴ are tolerated; the real specification is on killer defects of 154 nm and more.
3. **Fluorine passivates TiN, and the damage is done early.** Steady-state SiN:TiN is 294, effective selectivity is 93, because 77% of the TiN is lost in the first 8.5 s while the polymer film grows. A 4 s flash cuts the loss from 2.36 to 0.97 nm in the nitride steps.
4. **Radicals do not reach the bottom.** In a 50 nm column at aspect ratio 17, 12% of radicals and 14% of 35 eV ions reach the middle support. The trim tools serve the top support, and the strip needs an ion flush to wet the bottom of the column.
5. **One pillar in four is never touched.** The array has two classes of cell on a strict 3:1 pattern. Weak cells fall on the touched sublattice (97% against 75% at random), and a touched pillar charges at 2.5 V/s while its untouched neighbour does not.
6. **What resists HF resists the plasma.** A sequential route needs an HF selectivity of about 300, which only SiCN or SiBN supports, or a fast upper oxide, deliver. For two supports at 1b, the one-pass route S1 costs less; sequential routes are taken when the mask runs out.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheaths, ion energy, radical generation
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): hydrofluorocarbon selectivity of nitride and oxide
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, chucks, endpoint, chamber matching
- **Book #29** (DRAM Capacitor Hole Etch): the holes, the mold, the reference array
- **Book #30** (DRAM Capacitor Mold Etch): the support open as the first half of a mold module, the HF dip-out and drying; the one-pass recipe taken here as S0
- **Book #31** (DRAM High-Aspect-Ratio Capacitor Etch): the 1d-class array used for the three-support route
- **Book #32** (DRAM Capacitor Electrode Etch): storage-node separation before this etch; the plate after it
- **Book #33** (DRAM Capacitor Dielectric Etch): the ZAZ that coats everything the etch leaves
- **Companion volumes:** *Silicon Nitride Etch*, *Etch: The Sub-Nanometer Chisel* (atomic-layer etching), *Carbon Hard Mask Etch* (the support-open mask)

Book #30 cut the openings in one pass and dissolved the mold. This book asks what the cutting did to the film, and what the film now asks of everything that follows.

---

## File Organization

```
dram-capacitor-support-layer-etch/
├── README.md            ← You are here
├── PREFACE.md
├── INDEX.md
├── GLOSSARY.md
│
├── chapters/
│   ├── 01-support-layer-role.md
│   ├── 02-support-film-families.md
│   ├── 03-nitride-plasma-chemistry.md
│   ├── 04-lattice-design-opening-statistics.md
│   ├── 05-ccp-chambers-nitride-lattice.md
│   ├── 06-ion-energy-pulsing-temperature.md
│   ├── 07-radical-ale-wet-nitride-removal.md
│   ├── 08-endpoint-in-situ-monitoring.md
│   ├── 09-walls-polymer-post-etch-clean.md
│   ├── 10-opening-profile-cd-fidelity.md
│   ├── 11-tin-pillar-top-loss-two-classes.md
│   ├── 12-slivers-scum-not-open.md
│   ├── 13-charging-electrostatics-free-pillars.md
│   ├── 14-advanced-multi-support-schemes.md
│   ├── 15-metrology-inspection-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-thermochemistry-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-lattice-etch-electrostatics-calculations.md
    ├── F-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Plasma etching of the top and middle silicon nitride supports of a TiN pillar capacitor mold: one-pass (S0, S1) and sequential (S2, S3) routes  
✅ The support film, the opening lattice, its statistics, and its failure modes  
✅ Hydrofluorocarbon nitride chemistry with a polymer flash; radical, ALE, and wet finishing  
✅ Chamber design, endpoint, wall and polymer management, and the post-etch clean that makes the column wet  
✅ Opening profile, pillar-top loss, residue, charging, and electrostatics of free-standing pillars  
✅ HF-resistant supports, three-support molds, pre-opened lattices, 4F² and 3D DRAM  
✅ Metrology, yield, equipment sizing, and cost of ownership  

### What This Book Does NOT Cover
❌ The capacitor hole etch and the mold deposition (see Books #29 and #31)  
❌ The HF dip-out, drying, pillar leaning, and lattice mechanics beyond what the etch needs (see Book #30)  
❌ Storage-node separation and the plate etch (see Book #32); the dielectric clear (see Book #33)  
❌ The amorphous-carbon mask open and the lithography (see *Carbon Hard Mask Etch*)  
❌ Support film deposition hardware and chemistry in detail  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established thermochemistry and plasma–surface models, published etch-rate and literature trends, simple closed-form models of transport, electrostatics, and statistics, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** is used across chapters so that examples connect. It inherits the array and mold of Book #30: a 1b-class 6F² cell (F = 17 nm, cell area 1734 nm²) on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold (120 nm top SiN support, 650 nm PE-TEOS, 50 nm middle SiN support, 760 nm BPSG, 20 nm bottom SiN stop), solid TiN pillars 32/28/24 nm wide, 50 nm openings on a 90 nm hexagonal lattice at interstitial sites (28% open), and a 300 nm carbon mask. Three etch processes are carried through the book. **S0** is Book #30's one-pass recipe: SN1 40 s, OX 110 s, SN2 20 s, LAND 25 s (195 s), TiN top loss 5.0 nm, mask 253 nm used. **S1** adds a 4 s polymer flash before each nitride step and pulses the OX and LAND steps at 10 kHz, 80%: 226 s, TiN top loss 3.2 nm. **S2** is sequential: the top support is opened, HF removes a fast upper oxide, the wafer is dried, and the middle support is opened through the top-support openings with SiCN supports (S2D: every pillar touched, 118 s, 1.8 nm; S2A: reduced ion flux, 183 s, 1.3 nm). The statistics, polymer-film, transport, electrostatic, and cost numbers come from closed-form models written out in Appendix E. Where this book's number differs from a sibling's, the difference is noted in the text. Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #34 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** Complete  
**Back Matter (Appendices A–G, Glossary):** Complete  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-support-layer-role.md)**: The Support Layer & Why It Is Etched

---

**Book #34 Version:** 1.0  
**Last Updated:** 2026-10-05  
**Series:** ChipFoundryServices Technical Series
