---
title: Clock and Weather Station — ESP32-S3
---

# Clock and Weather Station — ESP32-S3

**Status:** Working prototype (validated). Project still open: final integration pending **populated PCB** + **3D-printed enclosure**.  
**Focus:** Embedded UI + indoor sensing + online local forecast + time accuracy + battery operation.

---

## Objective

Build a reliable **digital clock** that also displays:
- **Online local weather forecast** for my area (rain probability + wind speed/direction) to improve forecast accuracy.
- **Real indoor conditions** inside my garden office (temperature + humidity), so the display reflects what’s actually happening in the workspace.

---

## System Overview

This is a single-node embedded system based on an **ESP32-S3**, with:
- **Display:** ILI9341 TFT (SPI) for a clear glanceable UI
- **Sensors:** AHT20 (temperature/humidity) + BMP280 (pressure)
- **Connectivity:** Wi-Fi on-demand for:
  - **NTP time sync (UK timezone, GMT/BST)**
  - **Open-Meteo** forecast fetch (rain probability, wind speed/direction)
- **Power:** 2×18650 + MP1584EN buck regulator, with **battery voltage monitoring**

---

## Evidence (Photos)

### Working display (time + indoor + forecast)
![Display](../images/clock-weather-station/display.jpg)

### Hardware / build photo
![Hardware](../images/clock-weather-station/hardware.jpg)

---

## Circuit Schematic

Schematic showing the main components and interconnections:

![Schematic](../images/clock-weather-station/schematic.png)

---

## Hardware (Main Components)

- **MCU:** ESP32-S3 (N16R8)
- **TFT display:** ILI9341 (SPI)
- **Sensors:** AHT20 + BMP280
- **Power:** 2×18650 + MP1584EN (buck)
- **Battery monitoring:** resistor divider → ADC input (firmware calibrated)

---

## Forecast Data Source (Open-Meteo)

Forecast values are obtained via **Open-Meteo** for the configured location:
- **Rain probability (%)**
- **Wind speed (km/h)**
- **Wind direction (degrees → cardinal)**

This online forecast is paired with indoor measurements to give both:
- *what the weather is likely to do outside (forecast)*, and
- *what is happening inside the office right now (measured)*.

---

## Low-Power Approach

The project is designed to be battery-friendly:
- **Wi-Fi is enabled only when needed** (time sync / forecast fetch), not continuously.
- **Deep sleep** is used as the primary low-power mode (wake policy depends on configuration and switch/timer strategy).
- Battery voltage is monitored and displayed using a stable reading (calibration + smoothing in firmware).

---

## PCB Iterations

### 1) Discarded PCB (too compact)
This version was discarded because component spacing was too tight for comfortable assembly and rework.

![PCB discarded](../images/clock-weather-station/pcb-discarded.png)

### 2) Recommended PCB (assembly-friendly, work in progress)
This is the recommended direction: improved spacing and layout to support final assembly and enclosure integration.

![PCB recommended (WIP)](../images/clock-weather-station/pcb-recommended-wip.png)

---

## What I Learned

- Combining **online forecast** with **local indoor sensing** creates a more useful display than either alone.
- Time accuracy is a solved problem *if you respect power*: periodic **NTP** sync + proper timezone rules works reliably.
- Early PCB iterations are expected — spacing, serviceability and assembly comfort matter as much as “it fits”.

---

## Next Steps

- Finish routing/DRC on the recommended PCB, manufacture and populate it.
- Validate power (buck + battery monitoring) under real battery conditions.
- Design and print a **3D enclosure** with serviceability in mind (battery access, switch/USB access).
- (Optional) Add a small measurement section: current draw in idle / Wi-Fi fetch / deep sleep.

---
