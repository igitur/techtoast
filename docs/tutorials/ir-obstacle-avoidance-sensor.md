---
title: ESP32: IR Obstacle Avoidance Sensor
---

## ESP32: IR Obstacle Avoidance Sensor

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x IR Obstacle Avoidance Sensor Module
- 3x Male-to-Male Jumper Wires

### Connections
Using the breadboard, connect the IR Obstacle Avoidance Sensor Module to the ESP32 as follows:

- **VCC **→ ESP32 3V3
- **GND **→ ESP32 GND
- **OUT** → ESP32 D23

### Code
#### Upload the following code onto the ESP32:
```c
const int sensorPin = 23;  // IR sensor OUT pin
const int ledPin = 2;      // ESP32 onboard LED pin

void setup() {
  pinMode(sensorPin, INPUT);  // Configure sensor pin as input
  pinMode(ledPin, OUTPUT);    // Configure onboard LED pin as output
  Serial.begin(115200);
}

void loop() {
  int sensorValue = digitalRead(sensorPin);  // Read sensor value

  if (sensorValue == LOW) {
    // Obstacle detected
    digitalWrite(ledPin, HIGH);  // Turn on LED
    Serial.println("Obstacle detected!");
  } else {
    // No obstacle
    digitalWrite(ledPin, LOW);  // Turn off LED
    Serial.println("No obstacle detected.");
  }
  delay(500);  // Small delay for stability
}
```

### Explanation
The IR Obstacle Avoidance Sensor Module uses an infrared transmitter and receiver to detect obstacles within its range. When an object is detected, the module outputs a low signal on the **OUT** pin. The ESP32 reads this signal and responds accordingly. In this code, the onboard LED of the ESP32 will turn on when an obstacle is detected and turn off otherwise.

### Results
After uploading the code, open the Serial Monitor in the Arduino IDE to see real-time obstacle detection messages. When the sensor detects an object, the ESP32's onboard LED will turn on, and the Serial Monitor will display **"Obstacle detected!"**. When no obstacle is present, the LED will remain off, and the Serial Monitor

#### will display "No obstacle detected."
### Try for Yourself
1. Modify the code to perform different actions when an obstacle is detected, such as triggering a buzzer
  - r sending a notiﬁcation.
2. Experiment with adjusting the sensitivity of the sensor using the onboard potentiometer.