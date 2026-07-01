# CM-DC-01 — CMOS Inverter DC Transfer Curve

**Category:** Logic | **Complexity:** Basic | **Analysis:** DC | **VDD:** 1.8V

## Overview

This is the most fundamental CMOS circuit — a single inverter with NMOS and PMOS pair. The input is swept from 0 to 1.8V and the output voltage is recorded at each point, giving the Voltage Transfer Characteristic (VTC). From the VTC, the switching threshold VM, noise margins NML and NMH, and the small-signal gain at VM are all extracted. Getting these right is the starting point for any serious CMOS design work.

## Sizing

|Device|W (µm)|L (µm)|
|-|-:|-:|
|NMOS|0.42|0.15|
|PMOS|0.84|0.15|

PMOS is sized at 2× the NMOS width. Since hole mobility is roughly half that of electrons, doubling the PMOS width brings the drive strengths into balance and centers VM near VDD/2.

## Test Setup

* Vin swept DC from 0 → 1.8V in 10mV steps
* Vout recorded at each Vin step
* VM, NML, NMH, and gain at VM extracted from the resulting curve
* Simulated on sky130A PDK, Typical corner, T = 27°C

## Results

|Metric|Target|Result|
|-|-|-|
|VM|0.9 ± 0.1V|✅ Pass|
|NML|> 0.35V|✅ Pass|
|NMH|> 0.35V|✅ Pass|
|Gain at VM|> −10 V/V|✅ Pass|

## Key Insight

The curve shows a sharp transition centered near 0.9V, confirming that the 2× PMOS sizing achieves the intended balance. Symmetric noise margins mean the inverter handles both logic levels equally well — this is the baseline behavior all downstream logic timing is built on.

## Files

|File|Description|
|-|-|
|`schematic.png`|Circuit schematic|
|`schematic\_raw.json`|CircuitPro schematic export|
|`results/voltage\_transfer\_curve.png`|VTC simulation result|



