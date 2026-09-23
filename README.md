# CHILL-Controlled-Heating-for-Ice-Load-Limitations-
Automated rooftop deicing system utilizing load-cell force feedback and SSR power control to minimize energy consumption during snow accumulation.

Snow accumulation on rooftops poses significant structural risks in cold climates, yet cost-effective automated mitigation systems remain inaccessible for residential applications. This paper presents CHILL (Controlled Heating for Ice Load Limitations), a microcontroller based system integrating real-time gravimetric load sensing with threshold driven resistive heating to mitigate rooftop snow loads. A strain-gauge load cell interfaced through an HX711 24-bit ADC continuously monitors snow load on a 0.33 × 0.33 m stainless steel prototype panel. When the measured load exceeds 20 kg, an Arduino Uno actuates a JQC-3F(T73) relay to energize a 700 W nichrome heating element for a fixed 180-second interval; if the load remains above threshold after a 60-second cooling period, the cycle repeats. Meltwater is directed through integrated drainage to a reuse reservoir. System performance was evaluated across three metrics: load measurement accuracy (±2% full-scale, 19.6 kg measured vs 20 kg actual), snow load reduction efficiency (41.6% per cycle under controlled conditions), and specific energy consumption (35.0 Wh per 180-second cycle; 15,000 J/kg). Results confirm practical feasibility for residential snow management at substantially lower cost and complexity than commercial deicing alternatives. Future work will address scalability to full scale roof panels and outdoor validation under natural snowfall conditions.

   <img width="580" height="123" alt="image" src="https://github.com/user-attachments/assets/ce160943-e4df-45a1-8453-aa4328170a02" />



