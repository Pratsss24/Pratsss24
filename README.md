# Prathamesh Bedre

**M.Sc. Intelligent Manufacturing, TU Clausthal.** Production and manufacturing
engineering, with metrology and digital manufacturing as the edge.

*Produktionstechnik, Messtechnik und digitale Fertigung. Auf der Suche nach einer
Werkstudenten- oder Praktikumsstelle sowie einer Masterarbeit in Deutschland.*

I build the small, sharp tools that turn measurement and production data into a
decision someone on the shop floor can act on — which machine to adjust, how much
buffer to buy, whether the part actually conforms. Each repo below answers one
question and states plainly what it does **not** cover.

---

## Projects

| Repo | What it does | The finding |
|---|---|---|
| **[cmm-spc-dashboard](https://github.com/Pratsss24/cmm-spc-dashboard)** | Cp/Cpk/Pp/Ppk and X̄/R control charts from a CMM export | A bore with Cp 1.66 and Cpk 0.68 — a capable machine set wrong. The fix is a boring-bar offset, not a new machine. Capability and stability are different questions. |
| **[tolerance-stackup](https://github.com/Pratsss24/tolerance-stackup)** | Worst case vs RSS vs Monte Carlo on a 1D stack, plus allocation to a target Cpk | Worst case calls a working gearbox stack impossible; Monte Carlo puts the real scrap at 19,860 ppm. The gap between the three methods *is* the deliverable. |
| **[opcua-machine-monitor](https://github.com/Pratsss24/opcua-machine-monitor)** | Simulated CNC published over OPC UA → subscribed client → SQLite historian → OEE | A full shift end to end: 71.4% OEE from 1,541 samples over a real OPC UA socket. The traps are which timestamp you trust and what a counter reset does to your part count. |
| **[production-line-sim](https://github.com/Pratsss24/production-line-sim)** | SimPy discrete-event line: finite buffers, failures, buffer sweep, paired comparison | Every station has spare capacity and the line still runs 5.5 parts/h under its own bottleneck. That is variability meeting finite buffers, and no amount of fixing machines removes it. |
| **[scan-cad-deviation](https://github.com/Pratsss24/scan-cad-deviation)** | 3D scan-to-CAD inspection: ICP written from scratch, datum A\|B\|C alignment, signed deviation | The same 41,414 points pass the top face at 98.6% under a best fit and 61.3% under the datum scheme. **The alignment decides which feature gets blamed.** |

## How they are built

The same discipline runs through all five, because it is the part that transfers:

- **Ground truth, not plausible output.** The synthetic data carries *injected* errors,
  so the pipeline is asked to recover known values. scan-cad-deviation recovers a
  0.080 mm boss oversize as 0.0802 mm — that is a check, not a demo.
- **Closed-form test anchors.** 13 to 27 tests per repo, asserting values derived by
  hand, never a golden output file that only proves nothing changed.
- **Every README number recomputed** before it is written down, and corrected when it
  turns out to be wrong.
- **An explicit Scope section** in each README saying what is not implemented. A tool
  that hides its limits is worse than one that has them.
- **A *Fachbegriffe* table**, because the terminology is half the job in a German plant.

The write-ups spend as much space on what went wrong as on what works — a trimmed-ICP
objective that invented a false minimum 9.7 mm off, an RNG seed collision that silently
deleted half a cylinder, a datum selection rule that tilted the datum by 0.06 mm. Those
are the parts worth reading.

## Background

- **B.Eng. Mechanical Engineering** (SPPU, India, 2023)
- Hands-on **CMM and quality-metrology** experience in automotive production
- ~1 year in **hydraulic systems design**
- **Flywheel project:** hand calculation → ANSYS FEA → built prototype → validation.
  The full loop, including the places the three disagreed.

## Tools

`Python` · `NumPy / SciPy` · `SimPy` · `trimesh` · `matplotlib` · `SQLite` · `OPC UA`
· `ANSYS Workbench & Fluent` · `SolidWorks` · `AutoCAD` · `MATLAB` · `Git`

## Looking for

Werkstudent, internship or Masterarbeit in **Germany** — production engineering,
quality and metrology, or manufacturing simulation and digitalisation.

Languages: English (fluent) · German (B1, working toward B2) · Hindi (native)
