---
title: RGB LED
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x RGB LED
- 3x 220Ω Resistors (Red-Red-Brown)
- 4x Male-to-Male Jumper Wires

### Connections
Using the breadboard, connect the RGB LED to the ESP32 as follows:

- R → 220Ω Resistor → ESP32 D15
- **G **→ 220Ω Resistor → ESP32 D12
- **B **→ 220Ω Resistor → ESP32 D13
- **- (Cathode) **→ GND

### Code
#### Upload the following code onto the ESP32:
```c
// Pin definitions for RGB LED
int redPin = 15;
int greenPin = 12;
int bluePin = 13;

void setup() {
  // Initialize the RGB LED pins as outputs
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(bluePin, OUTPUT);
}

void loop() {
  // Red color
  digitalWrite(redPin, HIGH);
  digitalWrite(greenPin, LOW);
  digitalWrite(bluePin, LOW);
  delay(1000);  // Wait for 1 second

  // Green color
  digitalWrite(redPin, LOW);
  digitalWrite(greenPin, HIGH);
  digitalWrite(bluePin, LOW);
  delay(1000);  // Wait for 1 second
  // Blue color
  digitalWrite(redPin, LOW);
  digitalWrite(greenPin, LOW);
  digitalWrite(bluePin, HIGH);
  delay(1000);  // Wait for 1 second
}
```

### Explanation
#### In this setup:
- The RGB LED has four pins: **Red**, **Green**, **Blue**, and **Common Cathode**.
- Each colour pin is connected to an ESP32 pin (D15 for Red, D12 for Green, and D13 for Blue) with a

220Ω resistor to limit current and protect the LED.

- The **Common Cathode Pin** is connected to GND.

In the code, we turn each colour on sequentially with a delay of 1 second, cycling through red, green, and blue. The other pins are set LOW while the current colour is HIGH to ensure the correct colour is displayed.

### Results
Once the code is uploaded, the RGB LED will cycle through the colours Red, Green, and Blue, with each colour being displayed for 1 second.

### Try for Yourself
1. Modify the delay time to make the colours change faster or slower.
2. Experiment with blending the colours to create secondary colours (e.g., yellow by combining red and green).