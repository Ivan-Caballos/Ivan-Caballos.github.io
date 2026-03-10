[← Back to Home](../)

---

# Photodiode Transimpedance Amplifier (TIA) — Initial Validation

This project explored the basic analogue front-end stage for an optical power measurement system, using a photodiode and a transimpedance amplifier (TIA) to convert very small sensor current into a measurable voltage.

The objective of this initial validation was to confirm that a single-supply op-amp configuration could provide the expected current-to-voltage conversion behaviour, and to establish a practical starting point for later breadboard implementation.

The circuit was built around the **MCP6002** operating from a **5 V supply**, with a **2.5 V reference** applied to the non-inverting input. A simulated photodiode current was then applied at the inverting input, giving the expected first-order transimpedance relationship:

`Vout ≈ Vref + (IPD × Rf)`

---

## Why this project matters

This stage is relevant because optical sensing systems often begin with a low-level current output from a photodiode, which must be converted into a stable, measurable voltage before further processing.

Even at this early stage, the project helped validate three useful ideas:

- a photodiode current can be translated into a readable voltage using a simple TIA stage
- a single-supply analogue front-end can be biased around mid-supply for practical low-current measurement
- the simulated gain behaviour is consistent with the intended feedback network and suitable for prototyping

---

## Circuit Schematic

![Photodiode TIA Proteus Simulation](../images/tia-simulation-proteus.png)

*Proteus schematic used for the initial validation of the MCP6002-based photodiode transimpedance amplifier.*

---

## Simulated Configuration

- **Op-amp:** MCP6002  
- **Supply:** 5 V  
- **Reference voltage:** 2.5 V  
- **Feedback resistor:** 100 kΩ  
- **Feedback capacitor:** 22 pF  
- **Photodiode input current range tested:** 1 nA to 5 µA

---

## Simulation Results

| Photodiode Current | Simulated Output Voltage |
|--------------------|--------------------------|
| 1 nA               | 2.52453 V                |
| 10 nA              | 2.52543 V                |
| 100 nA             | 2.53443 V                |
| 1 µA               | 2.62443 V                |
| 5 µA               | 3.02443 V                |

---

## Result Interpretation

The output voltage increased with photodiode current as expected, confirming the intended **current-to-voltage conversion behaviour** of the TIA stage.

With **Rf = 100 kΩ**, the expected transimpedance gain is approximately:

- **1 µA → 0.1 V**
- **5 µA → 0.5 V**

This matches the observed trend in the simulation, where the output rose from approximately **2.52 V** at very low current to **3.02 V** at **5 µA**.

A small DC offset was present at the lowest current levels, but the incremental response remained consistent with the expected gain behaviour. For this early-stage validation, the important result was that the front-end responded in a predictable and usable way across the tested current range.

---

## Engineering Takeaways

- A basic **single-supply TIA** can be used to convert small photodiode current into a practical voltage signal
- Biasing the op-amp around **mid-supply** provides a useful operating point for low-current optical sensing in a 5 V system
- The selected **100 kΩ feedback resistor** produced the expected first-order gain relationship in simulation
- This project established a credible starting point for later hardware prototyping and further work on optical measurement electronics

---

## Conclusion

This initial validation confirmed that the proposed **MCP6002-based transimpedance stage** behaves as expected and is suitable as a first analogue front-end for photodiode-based measurement.

Although this stage represents an early simulation step rather than a full hardware characterisation, it already demonstrates the core behaviour needed for a practical optical sensing chain: low-level current conversion, controlled gain, and a stable single-supply operating point.
