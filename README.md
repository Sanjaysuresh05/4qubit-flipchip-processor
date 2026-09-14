# 4-Qubit Flip-Chip Transmon Processor

> **VLSID Design Contest 2026 — Finalist**

A 3D-integrated qubit processor designed to cut crosstalk without adding routing
congestion. A Q-chip/C-chip flip-chip architecture built in Keysight ADS
QuantumPro puts the qubits on one die and the control/readout routing on the
other, so isolation is bought with vertical separation rather than with longer,
more congested in-plane routing.

Reported result: crosstalk reduced from ~−37 dB to ~−55 dB after geometry
optimisation, with dispersive shift χ ranging 0.43–1.03 MHz across Q1–Q4 in the
final EM extraction.

This repository collects the EM verification figures for that design.

---

## 1. Design targets

![Design target table](figures/Target.png)

## 2. Circuit and layout

| | |
|---|---|
| ![Schematic](figures/Schematic.png) | ![Layout](figures/Layout.png) |
| Circuit schematic | Keysight ADS QuantumPro layout — four transmons, meandered readout resonators, shared feedline |

## 3. Flip-chip stack

| | |
|---|---|
| ![Substrate](figures/Substrate.png) | ![3D view](figures/3D.png) |
| Substrate and layer definition | Q-chip suspended above the carrier chip |

![3D model](figures/3D_1.png)

## 4. Eigenmode analysis

Six modes were solved. Each qubit mode localises on its own junction, with the
remaining modes belonging to the readout resonators.

| | | |
|---|---|---|
| ![Mode 1](figures/Mode_1.png) | ![Mode 2](figures/Mode_2.png) | ![Mode 3](figures/Mode_3.png) |
| Mode 1 | Mode 2 | Mode 3 |
| ![Mode 4](figures/Mode_4.png) | ![Mode 5](figures/Mode_5.png) | ![Mode 6](figures/Mode_6.png) |
| Mode 4 | Mode 5 | Mode 6 |

## 5. Extracted parameters — full EM analysis

Keysight QuantumPro, Full EM Analysis (RF).

| | Q1 | Q2 | Q3 | Q4 |
|---|---|---|---|---|
| Junction inductance | 10.4 nH | 8.48 nH | 7.05 nH | 5.95 nH |
| Qubit frequency | 4.69 GHz | 5.19 GHz | 5.68 GHz | 6.19 GHz |
| Anharmonicity | 175 MHz | 174 MHz | 174 MHz | 174 MHz |
| Readout resonator | 6.38 GHz | 6.81 GHz | 7.25 GHz | 7.67 GHz |
| Coupling *g* | 49.4 MHz | 53.5 MHz | 61.3 MHz | 70.5 MHz |
| Dispersive shift χ | 0.429 MHz | 0.564 MHz | 0.745 MHz | 1.03 MHz |

All four qubits land inside the 4.5–6.0 GHz target window with anharmonicity held
near 175 MHz, and each qubit couples only to its own resonator — the off-diagonal
entries in the coupling matrix are empty.

| | | |
|---|---|---|
| ![Cross-Kerr](figures/Full_EM.png) | ![Coupling g](figures/Full_EM_g.png) | ![Exchange J](figures/Full_EM_j.png) |
| Anharmonicity and cross-Kerr | Qubit–resonator coupling *g* | Exchange coupling *J* |

## 6. Energy participation ratio

| | |
|---|---|
| ![EPR participation](figures/EPR_E.png) | ![EPR cross-Kerr](figures/EPR_X.png) |
| Participation ratio matrix — each qubit mode sits at ~0.99 on its own junction | Cross-Kerr from EPR |

The EPR solve resolves six resonator modes (6.59–9.9 GHz) alongside the four
qubit modes (4.52–5.89 GHz).

## 7. S-parameters

| | |
|---|---|
| ![S11](figures/S11.png) | ![S21](figures/S21.png) |
| Reflection, S11 | Transmission, S21 |

## 8. Fabrication-ready layout

![GDS export](figures/GDS.png)

---

## Tooling

`Keysight ADS QuantumPro` · `Ansys HFSS` · `Ansys Q3D` · `KLayout` · `GDS export`

Material: aluminium on high-resistivity silicon. Readout: λ/2 CPW resonators.

---

Sanjay S. — ECE · Quantum Hardware Researcher / Engineer
[Portfolio](https://sanjaysuresh05.github.io)
