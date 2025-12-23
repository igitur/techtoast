---
title: ESP32: 5 LEDs Running Left & Right
---

## ESP32: 5 LEDs Running Left & Right

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 5x Green LEDs
- 5x 220Ω Resistors
- 6x Male-to-Male Jumper Wires

### Connections
Using the breadboard, connect the LEDs to the ESP32 as follows:

#### Anodes:
- **LED 1 Anode (Long Leg)** → ESP32 D13
- **LED 2 Anode (Long Leg)** → ESP32 D12
- **LED 3 Anode (Long Leg)** → ESP32 D14
- **LED 4 Anode (Long Leg)** → ESP32 D27
- **LED 5 Anode (Long Leg)** → ESP32 D26

#### Cathodes:
- **LED 1 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 2 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 3 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 4 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 5 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- GND Rail → ESP32 GND

### Code
#### Upload the following code onto the ESP32:
```c
// Pin definitions for LEDs
int ledPins[] = { 13, 12, 14, 27, 26 };
int numLeds = 5;

void setup() {
  // Initialize all LED pins as outputs
  for (int i = 0; i < numLeds; i++) {
    pinMode(ledPins[i], OUTPUT);
  }
}

void loop() {
  // Running from left to right
  for (int i = 0; i < numLeds; i++) {
    digitalWrite(ledPins[i], HIGH);  // Turn on LED
    delay(200);                      // Wait for 200 milliseconds
    digitalWrite(ledPins[i], LOW);   // Turn off LED
  }

  // Running from right to left
  for (int i = numLeds - 1; i >= 0; i--) {
    digitalWrite(ledPins[i], HIGH);  // Turn on LED
    delay(200);                      // Wait for 200 milliseconds
    digitalWrite(ledPins[i], LOW);   // Turn off LED
  }
}
```

### Explanation
In this tutorial, we use 5 LEDs connected to the ESP32. The LEDs will turn on in sequence, ﬁrst running from left to right and then running from right to left.

#### The program:
1. Turns on the LEDs one by one from **LED 1** to **LED 5**.
2. After reaching **LED 5**, it will then turn the LEDs off and start again in the reverse direction, from **LED 5** to **LED 1**.

The sequence will repeat indeﬁnitely, creating a "running" effect.

### Results
Once you upload the code, the LEDs will light up one at a time, running left to right, and then reverse the sequence, running right to left.

### Try for Yourself
1. Experiment by changing the delay time to make the LEDs run faster or slower.
2. Modify the sequence to add a delay after all LEDs are lit up.