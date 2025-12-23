---
title: ESP32: Sound Sensor
---

## ESP32: Sound Sensor

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x Sound Sensor Module
- 3x Male-to-Male Jumper Wires

### Connections
Using the breadboard, connect the Sound Sensor Module to the ESP32 as follows:

- **+ (VCC)** → ESP32 3V3
- **G (GND)** → ESP32 GND
- **A0 (Analog Output)** → ESP32 D32

### Code
#### Upload the following code onto the ESP32:
```c
int sensorPin = 32;   // ADC1 pin for sound sensor
int ledPin = 2;       // LED pin
int sensorValue = 0;  // Variable to store sensor reading
int threshold = 2000; // Adjust this based on your sensor's noise level

void setup() {
  Serial.begin(115200);
  pinMode(ledPin, OUTPUT);
}
void loop() {
  sensorValue = analogRead(sensorPin);
  Serial.println(sensorValue);

  if (sensorValue > threshold) {
    digitalWrite(ledPin, HIGH); // Turn LED on if sound is loud
  } else {
    digitalWrite(ledPin, LOW);  // Turn LED off if quiet
  }

  delay(10); // Small delay for stability
}
```

### Explanation
The **Sound Sensor** is an analog/digital sensor that uses a **condenser microphone** to detect changes in environmental noise. It is commonly used to identify sounds above a certain level. The module includes a **potentiometer** to adjust the noise detection threshold.

#### It provides two outputs:
1. **A0 (Analog Output):** This gives values representing the detected noise level. These values depend on the supplied voltage and potentiometer position, making it difficult to reconstruct actual audio.
2. **DO (Digital Output):** This provides a **HIGH signal** when the sound level exceeds the threshold set by the potentiometer.

In the following **Arduino sketch**, we’ll measure noise levels using the **analog output (A0)** of the Sound Sensor.

Before testing, you must **calibrate the module** using the **potentiometer**:

1. **Upload the code** and open the **Serial Monitor**.
2. Observe the **analog values** printed on the screen.
3. If the value is **far from 2000**, adjust the potentiometer:
  - **Turn clockwise** if the value is **too low**.
  - **Turn counter-clockwise** if the value is **too high**.
4. **Keep adjusting until the analog value stabilizes just below 2000 in a quiet environment.** You may need to turn the potentiometer up to 20 times. To make precise adjustments, we recommend removing the module, turning the potentiometer **three times**, reinserting it, and then checking the reading.
5. Once set, **speak near the microphone** and check if the **onboard led lights up** when the noise level increases.

### Results
After calibration, the **LED on Pin 2** will turn on when the **sound level exceeds 2000**. The Serial Monitor will display the real-time noise intensity values, allowing you to ﬁne-tune the detection threshold.

### Try for Yourself
1. Adjust the potentiometer on the sound sensor module to set a different sound threshold.
2. Modify the code to perform speciﬁc actions, such as triggering an alarm or sending notiﬁcations, based
  - n the sound intensity.