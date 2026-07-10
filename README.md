# sky130-cmos-circuit-library
A structured library of 24 CMOS analog and mixed-signal circuits designed and simulated on the SkyWater sky130A process (VDD = 1.8V). Each circuit includes a transistor-level schematic, CircuitPro JSON export, simulation results, and a detailed README explaining the design intent, sizing rationale, and key takeaways.

This library was built as part of a hands-on VLSI/analog design study — progressing from basic logic gates through OTAs, PLLs, and a full ADC front-end signal chain. The testbenches were generated and validated using a companion automation pipeline: [smart-sim-pipeline](https://github.com/YOUR_USERNAME/smart-sim-pipeline).

---

## PDK and Tools
| Item            | Details                                          |
|:-----------------|:--------------------------------------------------|
| PDK              | SkyWater sky130A                                  |
| Supply           | VDD = 1.8V                                        |
| Simulator        | ngspice (via CircuitPro/EDAcloud)                 |
| Process corner   | Typical NM (default), with corner sweeps where noted |
| Temperature      | 27°C unless stated                                |

---

## Circuit Catalog
| ID          | Circuit                                     | Category | Complexity   | Analysis |
|:------------|:---------------------------------------------|:---------|:-------------|:---------|
| [CM-DC-01](circuits/CM-DC-01-inverter-dc-transfer/)     | CMOS Inverter DC Transfer Curve               | Logic    | Basic        | DC       |
| [CM-Tran-01](circuits/CM-Tran-01-inverter-prop-delay/)   | Inverter Propagation Delay vs CL              | Logic    | Basic        | Tran     |
| [CM-Tran-02](circuits/CM-Tran-02-nand2-gate/)            | CMOS NAND2 Gate                               | Logic    | Basic        | Tran     |
| [CM-Tran-03](circuits/CM-Tran-03-nor2-gate/)             | CMOS NOR2 Gate                                | Logic    | Basic        | Tran     |
| [CM-Tran-04](circuits/CM-Tran-04-transmission-gate/)     | CMOS Transmission Gate                        | Logic    | Intermediate | Tran     |
| [CM-AC-01](circuits/CM-AC-01-inverter-linear-amp/)       | CMOS Inverter as Linear Amplifier             | Amps     | Intermediate | AC       |
| [CM-DC-02](circuits/CM-DC-02-nmos-cs-pmos-load/)         | NMOS CS with PMOS Active Load                 | Amps     | Intermediate | DC+AC    |
| [CM-AC-02](circuits/CM-AC-02-diff-pair-resistive-load/)  | Diff Pair — Resistive Load                    | Amps     | Intermediate | AC       |
| [CM-AC-03](circuits/CM-AC-03-diff-pair-mirror-load/)     | Diff Pair — Mirror Active Load                | Amps     | Intermediate | AC       |
| [CM-AC-04](circuits/CM-AC-04-cascode-diff-pair/)         | Cascode Diff Pair                             | Amps     | Advanced     | AC       |
| [CM-AC-05](circuits/CM-AC-05-folded-cascode-ota/)        | Folded-Cascode OTA                            | OTA      | Advanced     | AC       |
| [CM-AC-06](circuits/CM-AC-06-two-stage-miller-ota/)      | Two-Stage Miller-Compensated OTA              | OTA      | Advanced     | AC       |
| [CM-DC-03](circuits/CM-DC-03-bandgap-vref/)              | Bandgap-Style Voltage Reference               | Bias     | Advanced     | DC       |
| [CM-Tran-05](circuits/CM-Tran-05-cmos-ldo/)              | CMOS LDO Regulator                            | Bias     | Advanced     | Tran     |
| [CM-Tran-06](circuits/CM-Tran-06-ring-oscillator/)       | 5-Stage Ring Oscillator                       | Timing   | Intermediate | Tran     |
| [CM-Tran-07](circuits/CM-Tran-07-schmitt-trigger/)       | Schmitt Trigger Inverter                      | Timing   | Intermediate | Tran     |
| [CM-AC-07](circuits/CM-AC-07-vco-ring-based/)            | CMOS Ring-Based VCO                           | Timing   | Advanced     | Tran     |
| [CM-Tran-08](circuits/CM-Tran-08-class-ab-output-stage/) | Class AB Push-Pull Output Stage               | Power    | Intermediate | Tran     |
| [CM-Tran-09](circuits/CM-Tran-09-charge-pump/)           | CMOS Charge Pump (2×)                         | Power    | Advanced     | Tran     |
| [CM-DC-04](circuits/CM-DC-04-mismatch-corner-analysis/)  | Transistor Mismatch — Corner Analysis         | Matching | Advanced     | DC       |
| [CM-AC-08](circuits/CM-AC-08-instrumentation-amp/)       | Instrumentation Amplifier                     | System   | Advanced     | AC       |
| [CM-Tran-10](circuits/CM-Tran-10-sense-amplifier/)       | Sense Amplifier — Regenerative Latch          | System   | Advanced     | Tran     |
| [CM-AC-09](circuits/CM-AC-09-pll-vco-divider/)           | PLL VCO + Divider Block                       | System   | Advanced     | AC+Tran  |
| [CM-AC-10](circuits/CM-AC-10-ADC Front-End (Filter+SH+Comparator)/)             | ADC Front-End (Filter + S/H + Comparator)     | System   | Advanced     | AC+Tran  |

---

## Repo Structure
```
sky130-cmos-circuit-library/
├── circuits/
│   ├── CM-DC-01-inverter-dc-transfer/
│   │   ├── README.md
│   │   ├── schematic.png
│   │   ├── schematic_raw.json
│   │   └── results/
│   └── ...  (one folder per circuit)
└── docs/
```
Each circuit folder follows the same structure: a README with overview, sizing, test setup, results table, and key insight; schematic images; a CircuitPro JSON export; and a results subfolder with all simulation graphs.

---

## Companion Tooling
The testbenches in this repo were generated and validated using **smart-sim-pipeline** — a Python-based automation system covering circuit recognition, testbench generation, failure analysis, self-healing, parameter optimization, and sensitivity analysis targeting ngspice with sky130 PDK.

→ [smart-sim-pipeline](https://github.com/bmayank0/smart-sim-pipeline)

---

## License
MIT License — see [LICENSE](LICENSE) for details.
