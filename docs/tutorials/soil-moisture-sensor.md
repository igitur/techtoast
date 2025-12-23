---
title: Soil Moisture Sensor
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x Soil Moisture Sensor Module + Probe
- 2x Female-to-Female Jumper Wires
- 4x Male-to-Female Jumper Wires

### Connections
1. Using the breadboard, connect the Soil Moisture Sensor Module to the ESP32 as follows:
- **VCC** → ESP32 3V3
- **GND** → ESP32 GND
- **DO (Digital Output)** → ESP32 D35
- **AO (Analog Output)** → ESP32 D34
2. Using the two female-female jumper wires, connect the Soil Moisture Sensor Module to the Soil Moisture Sensor Probe. Here, the polarity does not matter.

### Code
#### Upload the following code onto the ESP32:
```c
const int analogPin = 34;   // Soil moisture sensor AO pin
const int digitalPin = 35;  // Soil moisture sensor DO pin
const int ledPin = 2;       // ESP32 onboard LED pin

void setup() {
  pinMode(analogPin, INPUT);   // Configure analog pin as input
  pinMode(digitalPin, INPUT);  // Configure digital pin as input
  pinMode(ledPin, OUTPUT);     // Configure onboard LED pin as output
  Serial.begin(115200);
}

void loop() {
  int moistureValue = analogRead(analogPin);  // Read analog moisture level
  int dryStatus = digitalRead(digitalPin);    // Read digital signal

  Serial.print("Moisture Level (Analog): ");
  Serial.println(moistureValue);

  if (dryStatus == LOW) {
    // Soil is dry
    digitalWrite(ledPin, HIGH);  // Turn on LED
    Serial.println("Soil is Dry!");
  } else {
    // Soil is wet
    digitalWrite(ledPin, LOW);  // Turn off LED
    Serial.println("Soil is Wet.");
  }

  delay(1000);  // Delay for stability
}
```

### Explanation
The Soil Moisture Sensor Module measures the moisture level in the soil. It provides both an analog output (AO) that gives a range of values indicating the moisture level and a digital output (DO) that toggles between HIGH and LOW based on a preset threshold. The onboard potentiometer adjusts this threshold. This code reads the analog value from the AO pin to get a moisture level. If the moisture value falls below the threshold (e.g., 2500), the onboard LED lights up to indicate dry soil. The values are displayed in the Serial Monitor.

### Results
After uploading the code, open the Serial Monitor in the Arduino IDE to observe real-time moisture readings. The Serial Monitor will display the analog moisture value. If the soil moisture is below the threshold, the

  - nboard LED on the ESP32 will turn on to indicate that the soil is dry.

### Try for Yourself
1. Modify the code to trigger a watering system or send an alert when the soil is too dry.