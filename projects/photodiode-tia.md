[← Back to Home](../)

---

# Photodiode Transimpedance Amplifier (TIA) — Simulation and Breadboard Validation

This project validates a basic **photodiode analogue front end** using a **BPW34 photodiode** and an **MCP6002-based transimpedance amplifier (TIA)**.

The goal was to verify that a small light-dependent photodiode current could be converted into a stable, measurable voltage in both **simulation** and **real hardware**, using a practical **5 V single-supply** design.

This work forms part of a broader optical measurement track, where low-level photodiode current must be converted into a usable analogue voltage before any further processing, monitoring, or control.

---

## Project Objective

The objective of this stage was to confirm three key points:

- a photodiode current can be converted into a measurable voltage using a simple TIA stage
- a **single-supply op-amp** can be biased around mid-supply for practical optical sensing
- the simulated gain behaviour can be reproduced in a real breadboard prototype

The intended first-order relationship was:

`Vout ≈ Vref + (IPD × Rf)`

where:

- `Vref` is the mid-supply bias point
- `IPD` is the photodiode current
- `Rf` is the TIA feedback resistor

---

## Circuit Overview

The circuit was built around the **MCP6002** operating from a **5 V supply**, with a **2.5 V reference** applied to the non-inverting input.

The photodiode current was applied at the inverting input, and the output voltage was set by the transimpedance gain defined by the feedback network.

### Main Components

- **Photodiode:** BPW34
- **Op-amp:** MCP6002
- **Supply:** 5 V
- **Reference voltage:** 2.5 V
- **Feedback resistor:** 100 kΩ
- **Feedback capacitor:** 22 pF

---

## Why this project matters

Photodiodes do not produce a convenient voltage output on their own. They produce a **small current**, often in the **nA to µA range**, which must be converted into a stable voltage before it can be measured or used by the rest of the system.

This makes the TIA one of the most important analogue building blocks in optical sensing.

This project was useful because it demonstrated:

- practical current-to-voltage conversion
- mid-supply biasing in a 5 V analogue system
- breadboard-level validation of a real optical front end
- the effect of illumination level on gain and output range

---

## Circuit Schematic

![Photodiode TIA Proteus Simulation](../images/tia-simulation-proteus.png)

*Proteus schematic used for the initial validation of the MCP6002-based photodiode transimpedance amplifier.*

---

## Simulation Validation

The first step was to validate the TIA behaviour in simulation by imposing known input current levels at the photodiode input node.

### Simulated Configuration

- **Op-amp:** MCP6002
- **Supply:** 5 V
- **Reference voltage:** 2.5 V
- **Feedback resistor:** 100 kΩ
- **Feedback capacitor:** 22 pF
- **Photodiode input current range tested:** 1 nA to 5 µA

### Simulation Results

| Photodiode Current | Simulated Output Voltage |
|--------------------|--------------------------|
| 1 nA               | 2.52453 V                |
| 10 nA              | 2.52543 V                |
| 100 nA             | 2.53443 V                |
| 1 µA               | 2.62443 V                |
| 5 µA               | 3.02443 V                |

### Simulation Interpretation

The output voltage increased with photodiode current as expected, confirming the intended **current-to-voltage conversion behaviour** of the TIA stage.

With **Rf = 100 kΩ**, the expected transimpedance gain is approximately:

- **1 µA → 0.1 V**
- **5 µA → 0.5 V**

This matches the observed trend in simulation, where the output rose from approximately **2.52 V** at very low current to **3.02 V** at **5 µA**.

A small DC offset was present at the lowest current levels, but the incremental response remained consistent with the expected gain behaviour.

---

## Breadboard Validation

After simulation, the circuit was built on breadboard using the **MCP6002**, **BPW34**, **100 kΩ feedback resistor**, and **22 pF feedback capacitor**.

This hardware stage was important because it moved the project beyond imposed current injection and into **real optical response**.

![TIA Breadboard](../images/TIA_Breadboard.png)

*Breadboard implementation of the MCP6002 + BPW34 transimpedance amplifier stage.*

---

## Controlled LED Illumination Test

To obtain more repeatable hardware measurements, the photodiode was tested using a **red LED** as a controlled light source.

The LED and photodiode were positioned in a fixed arrangement, and the LED drive level was adjusted using different series resistors. This provided a simple and repeatable way to vary incident light without relying on ambient lighting conditions.

The **off** condition was used as the reference baseline, and the equivalent increase in photodiode current was estimated from the measured output shift using:

`ΔIPD ≈ (Vout - 2.515 V) / 100 kΩ`

### Breadboard Results

| LED Series Resistor | Measured Output Voltage | Estimated Photodiode Current Increase |
|---------------------|-------------------------|---------------------------------------|
| Off                 | 2.515 V                 | 0.00 µA                               |
| 3.3 kΩ              | 2.541 V                 | 0.26 µA                               |
| 1 kΩ                | 2.656 V                 | 1.41 µA                               |
| 360 Ω               | 3.185 V                 | 6.70 µA                               |
| 220 Ω               | 3.345 V                 | 8.30 µA                               |

### Breadboard Interpretation

The measured output increased consistently as LED drive resistance was reduced, confirming that:

- the **BPW34 photodiode** responded correctly to increasing illumination
- the **TIA converted that changing current into a measurable voltage**
- the analogue front end behaved predictably in real hardware

This was not a fully calibrated optical power measurement, but it was a useful and repeatable hardware validation of the light-dependent analogue response.

---

## Simulation vs Breadboard

The simulation and breadboard results were consistent at the **behavioural level**.

In simulation, the TIA showed the expected first-order current-to-voltage relationship, with output voltage increasing approximately in proportion to imposed photodiode current through the **100 kΩ feedback resistor**.

In hardware, the **BPW34 + MCP6002** stage showed the same overall trend: as illumination increased, the output voltage increased accordingly.

Although the breadboard measurements were obtained under practical optical test conditions rather than calibrated photodiode current injection, they confirmed the same fundamental system behaviour observed in simulation.

Taken together, the results show that the photodiode and TIA stage operate as expected as a light-dependent analogue front end. The simulation validated the gain principle, while the breadboard confirmed real optical response in hardware.

---

## Engineering Takeaways

- A **single-supply TIA** can be used to convert small photodiode current into a practical voltage signal
- Biasing the op-amp around **mid-supply** provides a useful operating point for low-current optical sensing in a 5 V system
- The selected **100 kΩ feedback resistor** produced the expected first-order gain behaviour in simulation
- Breadboard testing confirmed real analogue response to controlled illumination changes
- A simple **LED-to-photodiode test arrangement** can provide a practical bridge between simulation and real optical hardware validation

---

## Conclusion

This project confirmed that the proposed **MCP6002-based transimpedance stage** works as intended as a first analogue front end for photodiode-based measurement.

The simulation validated the expected gain behaviour, and the breadboard build showed that the real **BPW34 + MCP6002** system produced a predictable voltage response to controlled changes in illumination.

Overall, this stage established a solid foundation for future work in photodiode measurement, gain optimisation, and broader optical sensing electronics.
