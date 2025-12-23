---
title: ESP32: Active Buzzer
---

## ESP32: Active Buzzer

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x Active Buzzer (the buzzer with legs of different length)
- 2x Male-to-Male Jumper Wires

### Connections
Using the breadboards, connect the Active Buzzer to the ESP32 as follows:

- **+ (Long Pin)** → ESP32 D18
- **- (Short Pin)** → ESP32 GND

### Code
#### Upload the following code onto the ESP32:
#define BUZZER_PIN 18  // Pin connected to the buzzer

```c
void setup() {
  pinMode(BUZZER_PIN, OUTPUT);  // Set buzzer pin as output
}

void loop() {
  digitalWrite(BUZZER_PIN, HIGH);  // Turn buzzer on
  delay(1000);                     // Wait for 1 second
  digitalWrite(BUZZER_PIN, LOW);   // Turn buzzer off
  delay(1000);                     // Wait for 1 second
}
```

### Explanation
The **Active Buzzer** has a built-in oscillator, so it only requires a simple high or low signal from the ESP32 to produce a sound. When the ESP32 outputs a HIGH signal on the designated pin, the buzzer will emit a continuous sound, and when the signal is LOW, the buzzer will stop.

In this code, the **Active Buzzer** is turned on and off at regular intervals using the **digitalWrite()** function. This is a simple way to control the buzzer without needing to generate speciﬁc frequencies, unlike a passive buzzer.

### Results
Once the code is uploaded, you will hear the Active Buzzer emit a continuous sound for one second, followed by a pause. The cycle repeats indeﬁnitely.

### Try for Yourself
1. Change the **delay** times to make the buzzer sound for longer or shorter periods.