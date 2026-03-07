---
title: "Constant-Current Driver — V1 (BJT) vs V2 (MOSFET) Comparison"
permalink: /projects/laser-current-driver-comparison-v1-v2.html
---

[← Back to Home](../)

---

# Constant-Current Driver — V1 (BJT) vs V2 (MOSFET) Comparison

This page compares two closed-loop constant-current driver prototypes built and measured on a breadboard:

- **V1:** LM358 + **BJT** linear pass element  
- **V2:** LM358 + **IRLZ44N MOSFET** linear pass element

Both versions regulate current using the same control idea (**V+ ≈ V−**) and were characterised at multiple setpoints.

---

## Summary (what changed between versions)

- **Pass element:** BJT (V1) → MOSFET (V2)
- **Measurement method emphasis:** V1 highlighted a key bench pitfall (**ammeter burden**).  
- **V2 behaviour:** similar regulation law, but MOSFET operation is better described via **VGS** and **VDS** requirements.

---

## Regulation check (loop health)

Both versions showed closed-loop regulation across setpoints:

- **V1 (BJT):** V+ and V− matched within ~1 mV across the characterisation table.
- **V2 (MOSFET):** V+ and V− matched within ~0–10 mV across setpoints.

This confirms the control loop behaviour is consistent in both designs.

---

## Setpoint accuracy (measured current vs nominal)

**V2 (MOSFET) — current from shunt (RSENSE = 4.7 Ω):**
- 50 mA setpoint: Vsource = 0.27 V → **~57 mA** (+14.8%)
- 100 mA setpoint: Vsource = 0.51 V → **~109 mA** (+8.5%)
- 150 mA setpoint: Vsource = 0.74 V → **~157 mA** (+4.7%)
- Full-scale: Vsource = 0.97 V → **~206 mA** (+3%)

**V1 (BJT) — current from load resistor (Rload = 4.7 Ω):**
- 50 mA setpoint: VRload = 0.250 V → **~53 mA** (+6.4%)
- 100 mA setpoint: VRload = 0.484 V → **~103 mA** (+3.0%)
- 150 mA setpoint: VRload = 0.707 V → **~150 mA** (+0.3%)
- Full-scale: VRload = 0.991 V → **~211 mA** (+5.5%)

Notes:
- Both versions achieved the target range and behaved predictably.
- Percentage error increases at low current, where pot resolution and offsets are more significant.

---

## Headroom and dissipation (linear pass element reality)

A key practical difference is how much voltage the pass device must drop in regulation.

### V2 (MOSFET) — measured VDS and estimated dissipation

Using measured values (I ≈ Vsource/4.7 and VDS = Vdrain − Vsource):

- ~206 mA: VDS ≈ 1.44 V → **PMOSFET ≈ 0.30 W**
- 150 mA: VDS ≈ 1.53 V → **PMOSFET ≈ 0.24 W**
- 100 mA: VDS ≈ 2.44 V → **PMOSFET ≈ 0.27 W**
- 50 mA:  VDS ≈ 2.97 V → **PMOSFET ≈ 0.17 W**

Thermal observation: MOSFET became slightly warm but remained comfortable to touch during short tests.

### V1 (BJT) — measured VCE and estimated dissipation

Using PBJT ≈ VCE · Icalc (from the V1 table):

- 50 mA:  **~0.17 W**
- 100 mA: **~0.29 W**
- 150 mA: **~0.37 W**
- ~200 mA: **~0.48 W**

Thermal observation: BJT heated rapidly at high current and benefited from airflow during longer measurements.

---

## Measurement discipline: ammeter burden (V1 lesson that applies to both)

V1 testing showed that inserting an ammeter in series introduced a significant burden voltage (~0.21 V), equivalent to ~1.27 Ω of series resistance at ~165 mA.  
This reduced the measured current and shifted the operating point.

Conclusion: for development measurements, verifying current via **V/R across a known resistor (or shunt)** is more reliable than a high-burden series ammeter.

---

## What this comparison shows

- Both designs regulate correctly and are easy to characterise using the loop condition (**V+ ≈ V−**) plus a resistor-based current estimate.
- The **BJT version** dissipates more power at high current in this setup (approaching ~0.5 W), which explains its stronger heating behaviour.
- The **MOSFET version** achieved similar current levels with lower measured dissipation (~0.3 W at ~206 mA) and minimal heating during short tests.
- Practical bench work matters: component variation (including a faulty/out-of-spec LM358 in early V2 testing) and measurement loading can dominate real results.

---
