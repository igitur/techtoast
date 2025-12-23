---
title: Passive Buzzer
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x Passive Buzzer (the buzzer with legs of equal length)
- 2x Male-to-Male Jumper Wires

### Connections
Using the breadboard, connect the Passive Buzzer to the ESP32 as follows:

- **+ (VCC Pin)** → ESP32 3V3
- **Other Pin** → ESP32 D18

### Code
#### Upload the following code onto the ESP32:
#define BUZZER_PIN 18  // Pin connected to the buzzer

```c
void setup() {
  pinMode(BUZZER_PIN, OUTPUT);  // Set buzzer pin as output
}

void loop() {
  tone(BUZZER_PIN, 1000);  // Play a 1000Hz tone
  delay(500);              // Wait for half a second
  noTone(BUZZER_PIN);      // Stop the tone
  delay(500);              // Wait for half a second
}
```

### Explanation
The **Passive Buzzer** produces sound when a voltage is applied to it. Unlike an active buzzer, which has an internal oscillator, a passive buzzer requires an external signal to generate sound. In this case, the ESP32 controls the buzzer using PWM (Pulse Width Modulation) to generate different tones.

The code uses the **tone()** function to generate a sound at a speciﬁc frequency, creating a melody. It ﬁrst plays a series of short beeps and then pauses, demonstrating how the buzzer can be controlled programmatically.

### Results
Once the code is uploaded, you should hear the passive buzzer emitting a series of beeps, as deﬁned by the frequencies in the code. You can experiment with different frequencies to create your own melody.

### Try for Yourself
1. Change the tone frequencies and durations to create your own sound sequence.