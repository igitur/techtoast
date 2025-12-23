---
title: ESP32: Light Sensor (Photoresistor)
---

## ESP32: Light Sensor (Photoresistor)

### Components Needed:
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x 10kΩ Resistor (Brown-Black-Orange)
- 1x Photoresistor (LDR)
- 3x Male-Male Jumper Wires

### Connections:
Using the breadboard, connect the LDR to the ESP32 as follows:

- **LDR Leg 1 (any leg of the LDR)** → ESP32 D34
- **LDR Leg 1 **→ **10kΩ** **Resistor **→ **GND**
- **LDR Leg 2 (the other leg)** → **3V3**

### Code:
#### Upload the following code onto the ESP32:
```c
// Define the LDR pin
int ldrPin = 34;  // You can change this to any analog-capable GPIO pin
int ldrValue = 0;

void setup() {
  // Start serial communication
  Serial.begin(115200);
}

void loop() {
  // Read the LDR value
  ldrValue = analogRead(ldrPin);

  // Print the LDR value to the Serial Monitor
  Serial.println(ldrValue);

  // Delay to prevent flooding the monitor
  delay(500);
}
```

### Explanation:
- The **LDR (Light Dependent Resistor)** is connected to **GPIO34** to measure light levels.
- In the **setup()**, serial communication is started at a baud rate of **115200**, which is the default for ESP32.
- In the **loop()**, the code reads the LDR value using analogRead(ldrPin) and stores it in ldrValue.
- It then prints the LDR value to the **Serial Monitor**.
- The delay(500) adds a 0.5-second pause between readings to avoid ﬂooding the monitor with data.

### Results:
You will see a continuous stream of numbers in the **Serial Monitor**, representing the light levels detected by the LDR. Higher numbers mean brighter light, and lower numbers mean dimmer light. The readings update every 0.5 seconds, giving you real-time feedback on the light intensity around the sensor.

### Try for yourself:
1. Create a light-controlled buzzer using the LDR and an active buzzer. When the light level drops below a certain threshold (for example, when it gets dark), the buzzer should turn on.
2. Create a day-night sensor using an LDR and an LED to automatically switch the LED on in low light conditions and off during the day.