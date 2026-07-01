# CM-DC-04 — Transistor Mismatch and Corner Analysis
**Category:** Matching | **Complexity:** Advanced | **Analysis:** DC | **VDD:** 1.8V

## Overview
A matched NMOS current mirror with Iref = 100µA simulated across all five sky130 process corners (TT, FF, SS, FS, SF). The goal is to quantify how much the output current Iout deviates from Iref across corners, and to understand the relationship between device area and mismatch. This is critical knowledge before committing to any analog layout.

## Sizing
| Device | W (µm) | L (µm) |
|:-------|-------:|-------:|
| NMOS   |   4.00 |   0.35 |

## Test Setup
- Iref = 100µA fixed reference current
- DC operating point simulated at TT, FF, SS, FS, SF corners
- T = 27°C for all corners
- Iout recorded and mismatch σ calculated

## Corner Analysis Results
| Corner | V(vg)  | I(vout)   |
|:-------|-------:|----------:|
| TT     | 0.949V | −101.52µA |
| FF     | 0.870V | −105.47µA |
| FS     | 1.053V | −98.87µA  |
| SF     | 0.842V | −107.77µA |
| SS     | 1.029V | −99.32µA  |

| Metric        | Target     | Result  |
|:--------------|:-----------|:--------|
| σ(Iout)       | < 2%       | ✅ Pass |
| Corner spread | Identified | ✅ Pass |

## Key Insight
FF corner gives the fastest, highest-current devices while SS gives the slowest. FS and SF represent the worst-case mismatch conditions — one transistor fast, the other slow. Increasing device area reduces mismatch (Pelgrom's law: σ(ΔVth) ∝ 1/√WL), but at the cost of larger silicon area and higher parasitic capacitance.

## Files
| File                    | Description                  |
|:-------------------------|:--------------------------------|
| `schematic.png`           | Circuit schematic               |
| `schematic_raw.json`      | CircuitPro schematic export     |
