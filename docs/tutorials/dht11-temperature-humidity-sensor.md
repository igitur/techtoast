---
title: DHT11 Temperature & Humidity Sensor
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 1x DHT11 Module
- 3x Male-to-Male Jumper Wires

### Connections
Using the breadboard, connect the DHT11 module to the ESP32 as follows:

- **S (Signal Pin)** → ESP32 D32
- **+ (VCC Pin)** → ESP32 VIN
- **- (GND Pin)** → ESP32 GND

### How to Install the Library
To use the DHT11 module, you need to install the **DHT sensor library**.

1. Open the Arduino IDE.
2. Go to **Sketch** → **Include Library** → **Manage Libraries**.
3. In the Library Manager, search for "DHT sensor library".
4. Click **Install** to install the library.

### Code
#### Upload the following code onto the ESP32:
#include <DHT.h>

#define DHTPIN 32      // Pin connected to the DHT11 data pin #define DHTTYPE DHT11  // Define the sensor type

```c
DHT dht(DHTPIN, DHTTYPE);  // Initialize the DHT sensor

void setup() {
  Serial.begin(115200);
  dht.begin();  // Start the DHT sensor
}

void loop() {
  delay(2000);  // Wait for 2 seconds between readings

  // Read temperature as Celsius
  float temperature = dht.readTemperature();

  // Read humidity
  float humidity = dht.readHumidity();

  // Check if the readings are valid
  if (isnan(temperature) || isnan(humidity)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }

  // Print the temperature and humidity
  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.print("°C  Humidity: ");
  Serial.print(humidity);
  Serial.println("%");
}
```

### Explanation
The DHT11 Module is a temperature and humidity sensor that communicates with the ESP32 using a single- wire interface (signal pin S). The sensor sends a digital signal containing the temperature and humidity data, which the ESP32 can then read and display.

The code uses the **DHT sensor library** to read the temperature and humidity values. The ESP32 will read the data from the sensor every two seconds and print the values to the Serial Monitor. You can also modify the code to use the data for other applications, like controlling a fan or a heating system based on the temperature.

### Results
After uploading the code, open the **Serial Monitor** in the Arduino IDE. You should see the temperature and humidity values printed every two seconds. The values will be displayed in Celsius and percentage, respectively.

### Try for Yourself
1. Modify the code to print the temperature in Fahrenheit instead of Celsius.
2. Experiment with controlling an output device (like an LED or a relay) based on the humidity or temperature readings.