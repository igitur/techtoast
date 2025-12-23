---
title: Push Button
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x Push Button & Button Cap
- 1x 10kΩ Resistor (Brown-Black-Orange)
- 3x Male-to-Male Jumper Wires

### Connections
Using the breadboards, connect the Push Button to the ESP32 as follows:

- **Pin 1** → Not used
- **Pin 2 (next to Pin 1)** → ESP32 D21
- **Pin 3 (diagonally across from Pin 2)** → ESP32 3V3
- **Pin 4 (next to Pin 3)** → 10kΩ resistor → ESP32 GND

### Code
#### Upload the following code onto the ESP32:
#define BUTTON_PIN 21  // Pin connected to the push button #define LED_PIN 2      // Pin connected to an LED

```c
void setup() {
  pinMode(BUTTON_PIN, INPUT);  // Set button pin as input
  pinMode(LED_PIN, OUTPUT);    // Set LED pin as output
}

void loop() {
  int buttonState = digitalRead(BUTTON_PIN);  // Read button state
  if (buttonState == HIGH) {
    digitalWrite(LED_PIN, HIGH);  // Turn LED on
  } else {
    digitalWrite(LED_PIN, LOW);   // Turn LED off
  }
}
```

### Explanation
The **Push Button** is a simple switch that completes a circuit when pressed. In this setup, the button connects the ESP32 D21 pin to 3**V3** when pressed, and it pulls the pin to **GND** when not pressed. The **10kΩ resistor** is used as a pull-down resistor to ensure that the input pin reads LOW when the button is not pressed.

In the code, the ESP32 reads the state of the button and performs an action based on whether the button is pressed or not. When the button is pressed, the ESP32 turns on an LED connected to another GPIO pin (for this example, the built-in LED on D2).

### Results
Once the code is uploaded, the ESP32 will monitor the button state. When you press the button, the built-in LED will light up, and it will turn off when the button is released.

### Try for Yourself
1. Modify the code to turn on and off the LED with different timing intervals (e.g., blink it on and off).
2. Use the button to trigger other actions, such as controlling a buzzer.