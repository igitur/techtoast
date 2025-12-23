---
title: ESP32: Tilt Switch
---

## ESP32: Tilt Switch

### Components Needed
- 1x ESP32
- 1x Programming Cable
- 1x Double Width Breadboard
- 1x Tilt Switch
- 1x 10kΩ Resistor
- 3x Male-to-Male Jumper Wires

### Connections
Using the breadboards, connect the tilt switch to the ESP32 as follows:

- **Tilt Switch Leg 1 (any leg of the Tilt Switch)** → ESP32 D34
- **Tilt Switch Leg 1 **→ **10kΩ** **Resistor **→ **GND**
- **Tilt Switch Leg 2 (the other leg)** → **3V3**

### Code
#### Upload the following code onto the ESP32:
```c
int tiltPin = 34;  // Pin connected to the tilt switch

void setup() {
  // Start the Serial communication
  Serial.begin(115200);

  // Set the tilt switch pin as input
  pinMode(tiltPin, INPUT);
}

void loop() {
  // Read the state of the tilt switch
  int tiltState = digitalRead(tiltPin);

  if (tiltState == HIGH) {
    // If the switch is resting (connected to GND)
    Serial.println("Tilt Switch is Resting");
  } else {
    // If the switch is tilted (connected to 3.3V)
    Serial.println("Tilt Switch is Tilted");
  }

  delay(500);  // Wait for half a second before checking again
}
```

### Explanation
In this setup, the tilt switch has two pins:

- **Pin 1** is connected to both the ESP32 digital input pin (GPIO 34) and a 10kΩ pull-down resistor to GND.
- **Pin 2** is connected to the 3.3V (VCC) of the ESP32.

The pull-down resistor ensures that when the tilt switch is resting (in the off position), the input pin (GPIO 34) will read LOW. When the tilt switch is tilted, Pin 1 is pulled HIGH due to the connection to the 3.3V (VCC).

The ESP32 continuously checks the state of the tilt switch, printing a message to the Serial Monitor depending

  - n whether the switch is resting or tilted. The code uses digitalRead() to check the state of the tilt switch and

prints either "Tilt Switch is Resting" or "Tilt Switch is Tilted."

### Results
Once you upload the code, open the Serial Monitor. You will see **"Tilt Switch is Resting"** when the tilt switch is in the resting position. When the switch is tilted, the message will change to **"Tilt Switch is Tilted."**

### Try for Yourself
1. Modify the code to control an LED or another device based on the tilt switch’s state.
2. Experiment with different ways to trigger actions based on the switch’s position.