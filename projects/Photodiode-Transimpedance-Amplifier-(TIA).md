# Photodiode Transimpedance Amplifier (TIA) — Initial Simulation Validation

This simulation was used to validate the basic transimpedance amplifier (TIA) stage for the optical power measurement system. The objective was to confirm that a small photodiode current could be converted into a measurable output voltage using a single-supply op-amp configuration.

The circuit was built around the **MCP6002** operating from a **5 V supply**, with a **2.5 V reference** applied to the non-inverting input. A photodiode current was then applied at the inverting input, with the output voltage following the approximate transimpedance relationship:

`Vout ≈ Vref + (IPD × Rf)`

## Simulated Configuration

- **Op-amp:** MCP6002
- **Supply:** 5 V
- **Reference voltage:** 2.5 V
- **Feedback resistor:** 100 kΩ
- **Feedback capacitor:** 22 pF
- **Photodiode input current range tested:** 1 nA to 5 µA

## Simulation Results

| Photodiode Current | Simulated Output Voltage |
|--------------------|--------------------------|
| 1 nA               | 2.52453 V                |
| 10 nA              | 2.52543 V                |
| 100 nA             | 2.53443 V                |
| 1 µA               | 2.62443 V                |
| 5 µA               | 3.024 V                  |

## Result Interpretation

The output voltage increased with photodiode current as expected, showing the correct **current-to-voltage conversion behaviour** for the TIA stage.

Using **Rf = 100 kΩ**, the expected gain is approximately:

- **1 µA → 0.1 V**
- **5 µA → 0.5 V**

This matches the observed trend in the simulation, where the output rose from approximately **2.52 V** at very low current to **3.02 V** at **5 µA**.

A small DC offset was present at the lowest current levels, but the incremental response remained consistent with the expected transimpedance gain.

## Conclusion

The simulation confirmed that the proposed TIA topology can convert photodiode current into a measurable voltage using a **single-supply MCP6002-based design**. This provided a practical starting point for the real breadboard implementation and initial hardware validation.
