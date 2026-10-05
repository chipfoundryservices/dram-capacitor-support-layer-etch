# Preface: Cutting the Film That Holds the Capacitor Up

## Why This Book Exists

Most etches remove material that was put down in order to be patterned. The support layer is different. It is put down in order to stay. A 120 nm sheet of silicon nitride in the mold of a DRAM capacitor holds seventeen billion titanium nitride pillars upright through the most violent step of the process, when the oxide around them is dissolved and the liquid that replaces it is dried away. Then the sheet stays in the finished capacitor, tied to every pillar, for the life of the device. It must be perforated so that the acid can get in, and it must not be harmed by being perforated.

The previous books of this series treated the perforation as a part of other modules. *DRAM Capacitor Mold Etch* gave it half a module, the first half of a story that ends with the HF dip-out and the physics of pillars leaning under capillary load. That treatment was written from the mold's side, and it was right to be: the supports matter to the mold because they hold the pillars. This book is written from the support's side. The questions change. How is the nitride made, and what does its hydrogen do to the etch? How can a plasma cut nitride a few nanometres from titanium nitride and spare the titanium nitride? What happens to the thousands of openings in a million cells that do not cut cleanly? How would anyone know?

Six facts make the support layer etch a subject of its own:

1. **There are four billion openings per layer per die.** About 4.25 × 10⁹, on a lattice nobody can repair. The specification is a statistical statement about clusters, not a statement about dimensions.

2. **Every opening has metal in its wall.** Three TiN crescents form a third of the opening at the top. The nitride must be cut next to a metal that fluorine passivates and chlorine would consume, and the passivation is a film that takes eight seconds to grow.

3. **The film is hydrogen-bearing PECVD nitride after a 580 °C anneal.** Its etch rate and its HF rate each depend on a few atomic percent of hydrogen, differently, and not in the direction a process engineer would choose.

4. **The bottom of the column cannot be reached.** At aspect ratio 17, 12% of the radicals and 14% of the low-energy ions reach the middle support. A clean that works at the top of the column leaves the bottom coated, and a coated column does not fill with acid.

5. **One pillar in four never sees the plasma.** The lattice is a superlattice of the pillar array, and it touches three pillars in every four. The array is divided into two classes of cell on a strict 3:1 pattern, and the failures follow the pattern.

6. **The film that survives HF best is the film that resists the plasma.** Carbon and boron make a nitride that is four to seven times less soluble in HF, and twice as slow to etch. That trade decides which routes can be run at all.

This book treats the support layer etch as **the perforation of a permanent film, with a statistical specification, next to a passivating metal, at the bottom of a column that cannot be cleaned or measured from the top**, and not as the first half of a dip-out.

---

## Unique Aspects of DRAM Capacitor Support Layer Etch

### 1. The Specification Is a Count

The target is not a CD but a probability: fewer than 0.01 clusters of three adjacent failures per die, among 4.25 × 10⁹ openings. A single failure is invisible and harmless. A cluster is fatal. The process is designed against the footprint of a particle, 154 nm across, and a resist defect, and it is confirmed only by a bitmap months later.

### 2. The Loss Is Paid at the Start

The pillar loses most of its TiN in the first eight seconds of each nitride step, while the protective polymer film is still growing. The steady-state selectivity of the chemistry is 294, and the effective selectivity of a 40 s step is 93. A four-second polymer flash before the step makes it 226. Almost everything else an engineer might adjust, the ion energy, the temperature, the pulse duty, the oxygen, changes the rate and not the loss.

### 3. A Door That Closes

Every liquid, vapor, and precursor that reaches the pillars afterwards passes through the opening. After the dielectric the free area is a quarter of what the etch left, and after the top electrode it is closed. The opening's shape is a three-lobed clover, not a circle, and the quantity that matters is its area.

### 4. Two Classes of Cell

The pillar that touches an opening loses TiN, takes up fluorine, may open its seam, and charges at 2.5 V/s in the plasma. The pillar that does not, does none of that. In a route where the pillars are free-standing the 10 V difference between neighbours is enough to pull them together. The asymmetry is a hazard in one route and a diagnostic in all: the failing cells show which module did it.

### 5. What Cannot Be Seen Must Be Inferred

The middle support is 770 nm down. The polymer at the bottom of the column, the nitride fin in its corner, and the junction stress on the pillar are all out of sight. The metrology of this book is a ladder: what can be seen from the top, what a test structure in the scribe stands in for, and what must be inferred from the signals of a chamber that cuts 3.8 × 10¹² openings in every wafer.

---

## How to Read This Book

### For Process Engineers
Read Chapters 1–4 for the film, the chemistry, and the lattice statistics, then Chapters 9–12 for the strip, the profile, the pillar tops, and the residue. Use Appendix D for windows and Appendix G for excursions.

### For Equipment Engineers
Read Chapter 1, then Chapters 5–9 for chambers, levers, trim and finishing tools, endpoint, and wall and polymer management. Chapter 15 covers the metrology that judges your tools, and Chapter 16 the equipment counts.

### For Integration Engineers
Read Chapters 1–2 for the film and the routes, Chapters 4 and 10 for the lattice and the CD budget, Chapter 14 for sequential routes and three-support molds, and Chapter 16 for the cost model and the new-product checklist.

### For Device Engineers
Read Chapter 1, Chapter 11 for the two classes and the weak-cell budget, Chapter 13 for charging and junction stress, and Chapter 16 for yield signatures.

### For Researchers
Read Chapters 3, 4, 7, and 13. The polymer-film model of Chapter 3, the cluster statistics of Chapter 4, the radical and ion transport estimates of Chapter 7, and the electrostatic pull-in of Chapter 13 are deliberately simple and invite refinement.

---

## A Note on the Reference Process

A single reference process runs through every chapter so that numbers connect. It inherits the array and mold of Book #30: a 1b-class 6F² cell on a 45 nm hexagonal pitch, a 1.60 µm mold with a 120 nm top support and a 50 nm middle support, solid TiN pillars, and 50 nm openings on a 90 nm hexagonal lattice. Three etch processes follow. **S0**, Book #30's recipe, cuts the whole column in one pass in 195 s and loses 5.0 nm of TiN. **S1**, with a polymer flash before each nitride step and a pulsed oxide step, takes 226 s and loses 3.2 nm. **S2** opens the top support, lets HF remove the upper oxide, dries the wafer, and opens the middle support from above through a SiCN lattice, in 118 s with 1.8 nm of loss, at the price of a second dip, a finer lattice, and a free pillar exposed to the plasma. Three supports at the 1d-class array of Book #31, a pre-opened lattice, and the supports of 4F² and 3D DRAM appear as extensions. All values are illustrative; the arithmetic is shown so that readers can replace them with their own.

---

## Acknowledgments

This book draws on decades of published work on silicon nitride and hydrofluorocarbon plasma etching, polymer-film models of selectivity, the transport of radicals and ions in narrow features, plasma charging of floating structures, the mechanics of slender pillars, and the shared experience of the engineers who have kept DRAM capacitor lattices open, wet, and standing through every node.

---

**Preface Version:** 1.0  
**Last Updated:** 2026-10-05
