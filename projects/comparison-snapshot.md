[← Back to Home](../)

---
title: "Constant-Current Driver — V1 (BJT) vs V2 (MOSFET) Comparison"
permalink: /projects/laser-current-driver-comparison-v1-v2.html
---

# Constant-Current Driver — V1 (BJT) vs V2 (MOSFET) Comparison

This comparison captures the progression from an initial BJT-based current driver prototype to a MOSFET-based version developed as a more robust follow-on architecture.

Both circuits were built around the same closed-loop control principle using the LM358, and both were characterised on the bench across multiple current setpoints. The aim was not only to confirm regulation behaviour, but also to compare device headroom, dissipation, measurement quality, and practical suitability for continued laser-driver development.

- **V1:** LM358 + BJT linear pass element  
- **V2:** LM358 + IRLZ44N MOSFET linear pass element

---

# Constant-Current Driver — V1 (BJT) vs V2 (MOSFET) Comparison

This comparison captures the progression from an initial BJT-based current driver prototype to a MOSFET-based version developed as a more robust follow-on architecture.

Both circuits were built around the same closed-loop control principle using the LM358, and both were characterised on the bench across multiple current setpoints. The aim was not only to confirm regulation behaviour, but also to compare device headroom, dissipation, measurement quality, and practical suitability for continued laser-driver development.

- **V1:** LM358 + BJT linear pass element  
- **V2:** LM358 + IRLZ44N MOSFET linear pass element

![current-driver-v1-v2-breadboard-comparison](https://github.com/user-attachments/assets/8b143e3f-1572-47b8-96dc-ef450a43e333)

*Breadboard comparison of the two closed-loop current-driver prototypes: V1 (BJT) above and V2 (MOSFET) below. This side-by-side build supported direct bench comparison of regulation behaviour, device heating, and measurement approach.*

---

## Why this comparison matters

This project is useful as more than a simple version-to-version check. It shows the engineering process behind moving from a working prototype to a better-informed design choice.

The comparison highlights:
- closed-loop regulation behaviour in both versions
- current-setpoint tracking across the operating range
- pass-device voltage and power dissipation differences
- practical bench issues that affect measurement quality and interpretation

---

## Architecture change between versions

The main design change was the linear pass element:

- **V1:** BJT  
- **V2:** MOSFET

The underlying control law remained the same in both cases: the op-amp drives the pass device so that **V+ ≈ V−**, forcing the sensed current to follow the setpoint.

Although both versions regulate correctly, the MOSFET-based version is better interpreted in terms of **VGS** and **VDS** requirements, while the BJT version is naturally discussed through **VBE**, **VCE**, and its stronger thermal behaviour at higher current.

---

## Regulation check

Both versions showed healthy closed-loop operation across the tested setpoints.

- **V1 (BJT):** V+ and V− matched within approximately **1 mV**
- **V2 (MOSFET):** V+ and V− matched within approximately **0–10 mV**

This confirms that, in both architectures, the feedback loop behaved as intended and maintained the expected regulation condition.

---

## Setpoint tracking

Both versions reached the intended operating range and showed predictable current control behaviour.

### V2 (MOSFET) — measured VDS and estimated dissipation

Using measured values with:

- **I ≈ Vsource / 4.7**
- **VDS = Vdrain − Vsource**

Estimated dissipation was:

- ~206 mA: VDS ≈ 1.44 V → **MOSFET dissipation ≈ 0.30 W**
- 150 mA: VDS ≈ 1.53 V → **MOSFET dissipation ≈ 0.24 W**
- 100 mA: VDS ≈ 2.44 V → **MOSFET dissipation ≈ 0.27 W**
- 50 mA: VDS ≈ 2.97 V → **MOSFET dissipation ≈ 0.17 W**

### V1 (BJT) — current estimated from load resistor voltage (Rload = 4.7 Ω)

- 50 mA setpoint: VRload = 0.250 V → **~53 mA** (+6.4%)
- 100 mA setpoint: VRload = 0.484 V → **~103 mA** (+3.0%)
- 150 mA setpoint: VRload = 0.707 V → **~150 mA** (+0.3%)
- Full-scale: VRload = 0.991 V → **~211 mA** (+5.5%)

In both versions, error was more noticeable at lower current, where potentiometer resolution, offsets, and small measurement uncertainties have a larger relative effect. At higher current, both circuits tracked the setpoint more closely and remained within a practical range for prototype evaluation.

---

## Headroom and dissipation

A key difference between the two versions was the electrical and thermal behaviour of the linear pass device.

### V2 (MOSFET) — measured VDS and estimated dissipation

Using measured values with:

- **I ≈ Vsource / 4.7**
- **VDS = Vdrain − Vsource**

Estimated dissipation was:

- ~206 mA: VDS ≈ 1.44 V → **PMOSFET ≈ 0.30 W**
- 150 mA: VDS ≈ 1.53 V → **PMOSFET ≈ 0.24 W**
- 100 mA: VDS ≈ 2.44 V → **PMOSFET ≈ 0.27 W**
- 50 mA: VDS ≈ 2.97 V → **PMOSFET ≈ 0.17 W**

Thermally, the MOSFET became only slightly warm during short tests and remained comfortable to touch.

### V1 (BJT) — measured VCE and estimated dissipation

Using the measured V1 values:

- 50 mA: **~0.17 W**
- 100 mA: **~0.29 W**
- 150 mA: **~0.37 W**
- ~200 mA: **~0.48 W**

The BJT version heated more noticeably at higher current and benefited from airflow during longer measurements. In practical terms, this made the MOSFET version the more comfortable device to work with under the tested conditions.

---

## Measurement discipline: ammeter burden

One of the most useful lessons from the V1 bench work was the effect of **ammeter burden voltage**.

Inserting an ammeter in series introduced an additional voltage drop of approximately **0.21 V**, equivalent to around **1.27 Ω** of unintended series resistance at about **165 mA**. This altered the operating point and reduced the measured current.

The practical lesson is important: for current-driver development, estimating current from **V/R across a known resistor or shunt** is often more reliable than inserting a high-burden ammeter directly in series.

This was not just a measurement detail; it affected how the circuit appeared to behave, and therefore influenced design interpretation.

---

## Key outcome

This comparison showed that both designs achieved stable closed-loop current regulation and reached the intended operating range, but they differed meaningfully in practical behaviour.

The **BJT version** worked well as an initial prototype and provided useful validation of the control approach, but dissipated more power at higher current and showed stronger heating.

The **MOSFET version** preserved the same regulation concept while offering lower measured dissipation and more comfortable thermal behaviour during short tests, making it the stronger platform for continued development.

Overall, this project demonstrates iterative analog design, bench-based validation, and the importance of measurement discipline when comparing real hardware.
