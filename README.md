# Analog-LPG-detection-system

## Project Objective
The goal of this project was to design and develop a precise analog measuring instrument for Liquefied Petroleum Gas (LPG) using the **MQ-6 gas sensor**. This project focuses on the **signal conditioning** and **mathematical modeling** required to convert raw sensor resistance into accurate concentration levels measured in parts per million (ppm).

## Technical Specifications
* **Sensor:** MQ-6 Gas Sensor (Non-module version).
* **Detection Range:** 200 – 10,000 ppm.
* **Accuracy:** ±10%.
* **Operating Voltage:** 5V DC.
* **Analog Output:** 0.2V – 4V based on gas concentration.

## Signal Processing Design
To ensure industrial-grade accuracy, the following signal conditioning stages were implemented:

* **Temperature Compensation:** Integrated a **20kΩ NTC Thermistor** and a **20kΩ fixed resistor** to stabilize the load resistance ($R_L$), compensating for sensor sensitivity fluctuations due to environmental temperature changes.
* **Noise Filtration (Low Pass Filter):** Designed an RC filter with a **10kΩ resistor** and **0.1µF capacitor** to achieve a cutoff frequency ($f_c$) of **159.15 Hz**, effectively reducing high-frequency noise and voltage fluctuations.
* **Amplification Stage:** Utilized an **LM358 Operational Amplifier** with feedback resistors ($R_f=10k\Omega$, $R_{in}=10k\Omega$) to provide a gain of **2**, mapping the sensor output to a usable range.
* **Comparator & Alert System:** A **10kΩ trimmer potentiometer** sets a reference voltage ($V_{ref}$) for the comparator, triggering a **LED indicator** when the concentration exceeds the safety threshold.

## Mathematical Modeling
The concentration is estimated using the power-law relationship derived from curve fitting the MQ-6 sensitivity characteristics:

$$PPM = \left( \frac{R_s}{A \cdot R_0} \right)^{\frac{1}{B}}$$

* **Parameters:** $A = 186.51$ and $B = -0.7465$.
* **Correction:** To ensure fresh air (0.88V) corresponds to 0 ppm, the final output is shifted by subtracting the baseline 13.61 ppm.



## Repository Contents
*  LPG DETECTION.pdf: Full technical project report.
*  LPG DETECTION.jpg: Physical implementation of the signal conditioning circuit on a breadboard, featuring the MQ-6 sensor, LM358 Op-Amp, and the RC filter network.
