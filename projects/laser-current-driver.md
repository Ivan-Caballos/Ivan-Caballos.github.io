---
title: Laser Diode Current Driver
---

# Laser Diode Current Driver (0–200 mA)

## Objective

Design and validate an adjustable precision constant-current driver suitable for laser diode applications, targeting a controllable range between 0 and 200 mA.

---

## Design Overview

The circuit is based on an op-amp controlled transistor configuration with a sense resistor used for current feedback.

Key elements:
- Op-amp for control loop
- Transistor (BD139 prototype stage)
- Sense resistor for current measurement
- Adjustable reference voltage

---

## Simulation (Proteus)

![Proteus Simulation](../laser-current-driver-proteus-simulation-v1.png)

Initial simulation used to validate current control behaviour before hardware prototyping.  
Focus areas included reference-to-current proportionality and supply behaviour under load.

---

## Practical Observations

During prototyping on breadboard:

- Supply voltage drop observed due to wiring resistance.
- PSU set to 5.25 V to obtain stable 5 V at circuit input.
- Current stability affected by cable length and contact resistance.
- Achieved measured output current: ~181 mA in current configuration.

---

## Validation Approach

- Compared theoretical calculations with simulation results.
- Measured real-world output current using multimeter.
- Observed system behaviour using oscilloscope.
- Identified voltage drop sources and wiring limitations.

---

## Lessons Learned

- Breadboard resistance significantly affects precision analog circuits.
- Short, rigid wiring improves stability.
- Power supply behaviour must be verified under load, not open-circuit.

---

## Next Iteration

- Improve PCB layout.
- Evaluate loop stability in more detail.
- Consider thermal behaviour at higher currents.
