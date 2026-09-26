// CHILL Controlled Heating for Ice Load Limitations
// Arduino Mega version

#include "HX711.h"


#define HX711_DOUT_PIN 3    
#define HX711_SCK_PIN  2    
#define RELAY_CTRL_PIN 7    


HX711 scale;

float calibrationFactor = -7050.0;   
const float limitKg = 2.0;           

const unsigned long HEATER_ON_MS = 60UL * 1000UL;
const unsigned long COOLDOWN_MS  = 60UL * 1000UL;

const uint8_t HX711_AVG_SAMPLES = 10;



enum SystemState {
  IDLE,
  HEATING,
  WAITING
};

SystemState state = IDLE;
unsigned long stateStartTime = 0UL;


void setup() {
  Serial.begin(9600);
  delay(50);

  scale.begin(HX711_DOUT_PIN, HX711_SCK_PIN);
  delay(200);

  Serial.println(F("Taring scale. Remove all load."));
  scale.set_scale();
  scale.tare(20);
  Serial.println(F("Tare complete."));

  scale.set_scale(calibrationFactor);

  pinMode(RELAY_CTRL_PIN, OUTPUT);
  digitalWrite(RELAY_CTRL_PIN, LOW);   

  Serial.println(F("CHILL system ready"));
  Serial.print(F("Calibration factor: "));
  Serial.println(calibrationFactor);
  Serial.print(F("Trigger threshold: "));
  Serial.println(limitKg);
}


void loop() {
  float weightKg = readWeightKg();

  Serial.print(F("Weight: "));
  Serial.print(weightKg, 3);
  Serial.println(F(" kg"));

  unsigned long now = millis();

  switch(state) {

    case IDLE:
      if (weightKg >= limitKg) {
        relayOn();
        state = HEATING;
        stateStartTime = now;
        Serial.println(F("State HEATING. Relay ON."));
      }
      break;

    case HEATING:
      if (weightKg < limitKg) {
        relayOff();
        state = WAITING;
        stateStartTime = now;
        Serial.println(F("Weight dropped. Relay OFF. WAITING."));
        break;
      }

      if (now - stateStartTime >= HEATER_ON_MS) {
        relayOff();
        state = WAITING;
        stateStartTime = now;
        Serial.println(F("Heat cycle complete. Relay OFF. WAITING."));
      }
      break;

    case WAITING:
      if (now - stateStartTime >= COOLDOWN_MS) {
        state = IDLE;
        Serial.println(F("Cooldown finished. Back to IDLE."));
      }
      break;
  }

  delay(500);
}


float readWeightKg() {
  if (!scale.is_ready()) {
    Serial.println(F("HX711 not ready"));
    return 0.0;
  }

  ## 🔒 Copyright & Intellectual Property

© 2026 Hashir Sajid. All rights reserved.

  long avgReading = scale.read_average(HX711_AVG_SAMPLES);
  float weight = (float)avgReading / calibrationFactor;
  return weight;
}

void relayOn() {
  dig
