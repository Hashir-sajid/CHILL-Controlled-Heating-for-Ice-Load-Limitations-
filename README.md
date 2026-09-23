# CHILL(Controlled Heating for Ice Load Limitations)
Automated rooftop deicing system utilizing load-cell force feedback and SSR power control to minimize energy consumption during snow accumulation.

Snow accumulation on rooftops poses significant structural risks in cold climates, yet cost-effective automated mitigation systems remain inaccessible for residential applications. This paper presents CHILL (Controlled Heating for Ice Load Limitations), a microcontroller based system integrating real-time gravimetric load sensing with threshold driven resistive heating to mitigate rooftop snow loads. A strain-gauge load cell interfaced through an HX711 24-bit ADC continuously monitors snow load on a 0.33 × 0.33 m stainless steel prototype panel. When the measured load exceeds 20 kg, an Arduino Uno actuates a JQC-3F(T73) relay to energize a 700 W nichrome heating element for a fixed 180-second interval; if the load remains above threshold after a 60-second cooling period, the cycle repeats. Meltwater is directed through integrated drainage to a reuse reservoir. System performance was evaluated across three metrics: load measurement accuracy (±2% full-scale, 19.6 kg measured vs 20 kg actual), snow load reduction efficiency (41.6% per cycle under controlled conditions), and specific energy consumption (35.0 Wh per 180-second cycle; 15,000 J/kg). Results confirm practical feasibility for residential snow management at substantially lower cost and complexity than commercial deicing alternatives. Future work will address scalability to full scale roof panels and outdoor validation under natural snowfall conditions.

   <img width="580" height="123" alt="image" src="https://github.com/user-attachments/assets/ce160943-e4df-45a1-8453-aa4328170a02" />

   Controlled Heating for Ice Load Limitation (CHILL): A Force-Feedback Rooftop Deicing Framework.

   This paper presented CHILL, a low-cost microcontroller-based system for automated rooftop snow load management, integrating strain-gauge load sensing (HX711, Arduino Uno), electromechanical relay switching (JQC-3F(T73)), and 700 W resistive nichrome heating in a closed loop architecture that activates heating exclusively when the measured snow load exceeds a structurally derived threshold of 20 kg.

Experimental evaluation across five ice block trials demonstrated a mean per-trial load reduction of 41.6% and a load measurement accuracy of ±2.0% full scale. Heat transfer analysis confirmed that the 180 second heating window is analytically consistent with the combined sensible and latent energy demand (Q_total ≈ 51,149 J) under a conservative loss factor of f = 2.5. Energy consumption is 35.0 Wh per cycle, with an estimated upper bound daily consumption of 0.350 kWh under extreme (10-cycle) loading. Mean specific energy consumption across trials is 18,748 J/kg.

Principal limitations are: (i) bench-scale testing with laboratory-formed ice rather than natural snowfall; (ii) single ambient temperature condition; and (iii) absence of a formal uncertainty analysis per GUM. Future work will address cold chamber outdoor validation (−25°C to −5°C), a temperature adaptive heating window, inline energy metering (PZEM-004T), and scaling to full residential panel dimensions.

CHILL offers a practical, low-cost pathway to residential snow load management where commercial deicing infrastructure is economically infeasible, with the added benefit of meltwater recovery an increasingly relevant consideration in regions subject to variable snowfall patterns.

<img width="184" height="229" alt="image" src="https://github.com/user-attachments/assets/9b9a08a0-be79-4899-80ab-77a16efa5b87" />
<img width="693" height="217" alt="image" src="https://github.com/user-attachments/assets/06d50fc3-a5ed-4552-9ef3-ac23c759d59d" />



## 🔒 Copyright & Intellectual Property

© 2026 Hashir Sajid. All rights reserved.

This repository and its contents (including firmware code, schematics, CAD designs, and documentation) are published strictly for portfolio, educational, and peer-review viewing purposes (e.g., academic evaluation and graduate admissions review).




