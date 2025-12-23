---
title: Water Level Sensor
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x Water Level Sensor
- 3x Male-to-Female Jumper Wires

### Connections
Using the breadboard, connect the Water Level Sensor to the ESP32 as follows:

- **- (GND)** → ESP32 GND
- **+ (VCC)** → ESP32 3.3V
- **S (Signal)** → ESP32 D34

### Code
#### Upload the following code onto the ESP32:
```c
const int sensorPin = 34;    // Water Level Sensor Signal Pin
const int ledPin = 2;        // ESP32 onboard LED pin
const int threshold = 1000;  // Threshold for water level (adjust as needed)

void setup() {
  pinMode(sensorPin, INPUT);  // Configure the sensor pin as input
  pinMode(ledPin, OUTPUT);    // Configure the onboard LED as output
  Serial.begin(115200);
}
void loop() {
  int waterLevel = analogRead(sensorPin);  // Read water level from the sensor

  Serial.print("Water Level: ");
  Serial.println(waterLevel);

  if (waterLevel > threshold) {
    // Water level is above the threshold
    digitalWrite(ledPin, HIGH);  // Turn on LED
    Serial.println("Water level HIGH!");
  } else {
    // Water level is below the threshold
    digitalWrite(ledPin, LOW);  // Turn off LED
    Serial.println("Water level LOW.");
  }

  delay(500);  // Delay for stability
}
```

### Explanation
The water level sensor works by detecting the presence of water through its sensor pins. When the probe (S) detects water, the sensor sends a signal to the ESP32 through the S pin, which can be read as a HIGH or LOW state.

The ESP32 is programmed to monitor the input from the S pin and take action accordingly. In this case, we are reading the input to determine if the water is detected and then printing the result to the Serial Monitor.

The code initializes the sensor on GPIO 34, reads the sensor data, and sends the status of the water level (HIGH

  - r LOW) to the Serial Monitor. This allows you to monitor the water level in real time.

### Results
After uploading the code, open the Serial Monitor in the Arduino IDE to observe the water level readings. The

  - nboard LED of the ESP32 will turn on when the water level surpasses the set threshold.

### Try for Yourself
1. Adjust the threshold value in the code to suit different water level ranges.
2. Modify the code to take actions, such as activating a pump or sending alerts, based on the water level readings.