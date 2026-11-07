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

## Quality and metrology

| Repo | What it does | The finding |
|---|---|---|
| **[cmm-spc-dashboard](https://github.com/Pratsss24/cmm-spc-dashboard)** | Cp/Cpk/Pp/Ppk and X̄/R control charts from a CMM export | A bore with Cp 1.66 and Cpk 0.68 — a capable machine set wrong. The fix is a boring-bar offset, not a new machine. Capability and stability are different questions. |
| **[tolerance-stackup](https://github.com/Pratsss24/tolerance-stackup)** | Worst case vs RSS vs Monte Carlo on a 1D stack, plus allocation to a target Cpk | Worst case calls a working gearbox stack impossible; Monte Carlo puts the real scrap at 19,860 ppm. The gap between the three methods *is* the deliverable. |
| **[scan-cad-deviation](https://github.com/Pratsss24/scan-cad-deviation)** | 3D scan-to-CAD inspection: ICP written from scratch, datum A\|B\|C alignment, signed deviation | The same 41,414 points pass the top face at 98.6% under a best fit and 61.3% under the datum scheme. **The alignment decides which feature gets blamed.** |
| **[pitstop-spc](https://github.com/Pratsss24/pitstop-spc)** | SPC on 1,475 real pit stops, charted the way a manufacturing process is charted | A textbook 3-sigma individuals chart raises **14.7× as many alarms as it should** when nothing is wrong; the eight Nelson rules raise 82×. The same test on normal data returns 1.0×, which is how you know the machinery is right and the assumption is not. |

## Production systems and simulation

| Repo | What it does | The finding |
|---|---|---|
| **[opcua-machine-monitor](https://github.com/Pratsss24/opcua-machine-monitor)** | Simulated CNC published over OPC UA → subscribed client → SQLite historian → OEE | A full shift end to end: 71.4% OEE from 1,541 samples over a real OPC UA socket. The traps are which timestamp you trust and what a counter reset does to your part count. |
| **[production-line-sim](https://github.com/Pratsss24/production-line-sim)** | SimPy discrete-event line: finite buffers, failures, buffer sweep, paired comparison | Every station has spare capacity and the line still runs 5.5 parts/h under its own bottleneck. That is variability meeting finite buffers, and no amount of fixing machines removes it. |
| **[laptime-sim](https://github.com/Pratsss24/laptime-sim)** | Quasi-steady-state lap time solver, ~60 lines, validated against a real season | No optimiser, no driver model, no library — written rather than called so every assumption stays visible, and honest about where it disagrees with reality. |
| **[race-strategy-mc](https://github.com/Pratsss24/race-strategy-mc)** | Monte Carlo pit strategy with every input measured from the same season it is tested against | The optimiser is **wrong in one direction at nine of fourteen circuits**, and most of the project is finding out why. The answer is a cost lap-time data cannot measure — for a reason that is itself measurable. |

## Reliability and remaining life

| Repo | What it does | The finding |
|---|---|---|
| **[reliability-weibull](https://github.com/Pratsss24/reliability-weibull)** | Survival analysis as a reliability problem: right-censored MLE, competing risks | **90.4% of the observations are censored, and getting them wrong reverses the conclusion.** Counting survivors as failures returns β = 3.53, a confident wear-out signature; the right likelihood returns β = 0.918 (CI 0.824–1.023), indistinguishable from constant hazard. |
| **[remaining-useful-life](https://github.com/Pratsss24/remaining-useful-life)** | RUL on NASA C-MAPSS turbofans: two independent estimators, censoring against a planted truth | **A single error number for a fleet is close to meaningless.** The sensor-driven estimator is 4.4× more accurate than the age-only one near failure — where the age-only one's nominal 50% interval covers **11%** of those engines against 48% pooled. Coverage is reported as measured, not as claimed. |

## Measuring a cause from observational data

Seven projects on the same problem: the quantity you want is tangled with the one
you can see, and the obvious regression measures the wrong thing.

| Repo | The question | The finding |
|---|---|---|
| **[driver-or-car](https://github.com/Pratsss24/driver-or-car)** | How much of a lap is the car, how much the driver? | Car 0.732 s a lap, driver 0.192 — but *what happened on the day* is 0.461 s, **2.4× the driver**. The largest thing a season ranking measures, after the car, is luck. |
| **[grid-slot-value](https://github.com/Pratsss24/grid-slot-value)** | What is one grid slot worth? | Measured only from the 596 entries moved by a penalty — the one thing that moves a car without changing it. A slot is worth 0.17 places; the naive regression says 0.30. **44% of apparent track position is the car reasserting itself.** |
| **[stint-degradation](https://github.com/Pratsss24/stint-degradation)** | How fast do tyres degrade? | **The obvious estimate has the wrong sign.** Within a stint the data says 0.025 s/lap *faster*; put the race lap in the model and it says 0.032 s/lap slower. The difference is the fuel load, algebraically inseparable unless you put it there on purpose. |
| **[price-of-a-second](https://github.com/Pratsss24/price-of-a-second)** | What does a botched pit stop cost? | 1.34 places at the flag (CI 0.70–1.98, p = 0.0001), measured from two cars of the same team in the same race, one of which had the gun misfire. |
| **[safety-car-lottery](https://github.com/Pratsss24/safety-car-lottery)** | How much earned advantage does luck delete? | A stop costs 23.2 s green, 5.2 s under a safety car — an 18.0 s prize nobody chooses to receive. 160 of 280 cars took it; the other 120 watched. |
| **[undercut-effect](https://github.com/Pratsss24/undercut-effect)** | What is pitting first worth? | +2.1 to +3.8 s, best at a three-lap head start — and **fully repaid by lap 12. It is a loan, not a gain.** Exists because the project before it proved stint order cannot change race time and said so. |
| **[pace-to-pass](https://github.com/Pratsss24/pace-to-pass)** | How much quicker must a car be to get past? | +0.40 s a lap for an even chance; being held up costs +0.25 s a lap. Circuit differences come out at p 0.47 — **one season cannot resolve them**, which is reported rather than hidden. |

---

## How they are built

The same discipline runs through all seventeen, because it is the part that transfers:

- **Ground truth, not plausible output.** The synthetic data carries *injected* errors,
  so the pipeline is asked to recover known values. scan-cad-deviation recovers a
  0.080 mm boss oversize as 0.0802 mm; remaining-useful-life recovers a planted
  detectability horizon exactly and predicts to within three cycles. That is a check,
  not a demo.
- **Closed-form test anchors.** 592 tests across the seventeen repos, 13 to 80 each,
  asserting values derived by hand — never a golden output file that only proves
  nothing changed.
- **Every README number recomputed** before it is written down, and corrected when it
  turns out to be wrong.
- **An explicit Scope section** in each README saying what is not implemented. A tool
  that hides its limits is worse than one that has them.
- **A printable PDF report** per repo, composed in matplotlib from the same run that
  produces the figures, so no number can drift between code and write-up.
- **A *Fachbegriffe* table** in sixteen of the seventeen, because the terminology is
  half the job in a German plant.

The write-ups spend as much space on what went wrong as on what works — a trimmed-ICP
objective that invented a false minimum 9.7 mm off, an RNG seed collision that silently
deleted half a cylinder, a datum selection rule that tilted the datum by 0.06 mm, a
censoring result that came out backwards and had to be explained by simulation rather
than reported raw. Those are the parts worth reading.

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
