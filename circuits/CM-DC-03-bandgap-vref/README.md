# CM-DC-03 — Bandgap-Style Voltage Reference (CMOS + R)
**Category:** Bias | **Complexity:** Advanced | **Analysis:** DC | **VDD:** 1.8V

## Overview
A CMOS bandgap-style voltage reference combining a PTAT (proportional to absolute temperature) component from subthreshold NMOS ratio with a CTAT (complementary to absolute temperature) component. The two components are summed through resistors to produce a reference voltage that is largely temperature-independent over the range −20 to +80°C.

## Sizing
| Device | W (µm) | L (µm) |
|:-------|-------:|-------:|
| NMOS   |   4.00 |   0.35 |
| PMOS   |   4.00 |   0.35 |

## Test Setup
- Temperature swept: −20°C → +80°C in 5°C steps
- Vref measured at each temperature point
- Temperature coefficient (TC) calculated in ppm/°C

## Results
| Metric | Target       | Result  |
|:-------|:-------------|:--------|
| TC     | < 100 ppm/°C | ✅ Pass |
| Vref   | ≈ 0.6V ± 3%  | ✅ Pass |

## Key Insight
In subthreshold operation, MOSFET current follows Id = I0·exp(Vgs/nVT) where VT = kT/q is proportional to temperature. By ratioing two subthreshold devices, a PTAT voltage is generated. Summing it with a CTAT diode voltage cancels the first-order temperature dependence.

## Files
| File                    | Description                  |
|:-------------------------|:--------------------------------|
| `schematic.png`           | Circuit schematic               |
| `schematic_raw.json`      | CircuitPro schematic export     |
