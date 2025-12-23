---
title: Thermistor (Temperature Sensor)
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x Thermistor
- 1x 10kΩ Resistor (Brown-Black-Orange)
- 3x Male-to-Male Jumper Wires

### Connections
Using the breadboards, connect the thermistor to the ESP32 as follows:

- **Thermistor Leg 1 (any leg of the thermistor)** → ESP32 D34
- **Thermistor Leg 1 **→ **10kΩ** **Resistor **→ **GND**
- **Thermistor Leg 2 (the other leg)** → **3V3**

### Code
#### Upload the following code onto the ESP32:
```c
const int thermistorPin = 34;           // Pin connected to the thermistor
const float nominalResistance = 10000;  // 10k ohms at 25°C
const float nominalTemperature = 25;    // Nominal temperature in Celsius
const float bCoefficient = 3950;        // B-coefficient (value depends on the
thermistor)

void setup() {
  Serial.begin(115200);  // Start the serial communication at 115200 baud rate
}

void loop() {
  int sensorValue = analogRead(thermistorPin);  // Read the analog value from GPIO

  // Convert the sensor value to voltage (ESP32 uses 12-bit ADC range: 0 to 4095)
  float voltage = sensorValue * (3.3 / 4095.0);  // Assuming 3.3V reference and
```

12-bit ADC

```c
  // Avoid invalid calculations if the voltage is zero or too high
  if (voltage <= 0 || voltage >= 3.3) {
    Serial.println("Invalid reading");
    delay(1000);  // Wait for a second before reading again
    return;
  }

  // Calculate the resistance of the thermistor
  float resistance = nominalResistance * (3.3 / voltage - 1);

  // Avoid taking a log of zero or negative values (which can cause NaN)
  if (resistance <= 0) {
    Serial.println("Invalid resistance");
    delay(1000);
    return;
  }

  // Calculate the temperature in Kelvin using the Steinhart-Hart equation
  float temperatureK = 1 / (1 / (nominalTemperature + 273.15) + (log(resistance /
nominalResistance) / bCoefficient));

  // Convert temperature from Kelvin to Celsius
  float temperatureC = temperatureK - 273.15;

  // Print the temperature to the Serial Monitor
  Serial.println(temperatureC);  // Show temperature in Celsius
  delay(1000);                   // Wait for a second before reading again
}
```

### Explanation
In this setup, the thermistor is directly connected to the ESP32’s analog input pin (GPIO 34). The thermistor's resistance changes as the temperature varies, and the ESP32 reads this change as a varying voltage. Using the voltage from GPIO 34, we can calculate the thermistor’s resistance, and then use the known characteristics of the thermistor to convert that resistance into a temperature value.

When you upload and run the code, the ESP32 will read the analog value, which corresponds to the voltage change due to the thermistor’s varying resistance. The code then calculates the resistance and converts it into a temperature in Celsius using the thermistor's B-coefficient and nominal resistance. This value will be displayed on the Serial Monitor.

### Results
Once you have uploaded the code, open the Serial Monitor in the Arduino IDE. You will see the temperature readings in degrees Celsius. These readings will change as you expose the thermistor to different temperatures, allowing you to monitor temperature changes in real-time.

This approach allows you to directly measure and display the temperature using the thermistor's characteristics and the ESP32’s analog-to-digital conversion.

### Try for Yourself
1. Try comparing your thermistor readings with a DHT11 sensor to see how the temperature values from both sensors differ and evaluate their accuracy.