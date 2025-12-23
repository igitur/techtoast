---
title: ESP32: Web Server to Control 5 LEDs with Slider
---

## ESP32: Web Server to Control 5 LEDs with Slider

In this tutorial, we'll learn how to create a simple web server on the ESP32 that allows you to control ﬁve LEDs using a slider on a webpage. By adjusting the slider, you can turn on and off a sequence of LEDs in real-time, with the number of LEDs lit depending on the slider’s position. This project is a great way to explore both web development and hardware control with the ESP32, while also learning how to map values and use sliders to interact with hardware components. Let’s dive in and get your ESP32 set up for some interactive LED fun!

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x Double Width Breadboard
- 5x Green LEDs
- 5x 220Ω resistors
- 6x Male-Male Jumper Wires

### Connections
Using the breadboard, connect the LEDs to the ESP32 as follows:

#### Anodes:
- **LED 1 Anode (Long Leg)** → ESP32 D13
- **LED 2 Anode (Long Leg)** → ESP32 D12
- **LED 3 Anode (Long Leg)** → ESP32 D14
- **LED 4 Anode (Long Leg)** → ESP32 D27
- **LED 5 Anode (Long Leg)** → ESP32 D26

#### Cathodes:
- **LED 1 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 2 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 3 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 4 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- **LED 5 Cathode (Short Leg)** → 220Ω Resistor → GND Rail
- GND Rail → ESP32 GND

### How to Install the Library
#### Make sure you have the necessary libraries:
- WiFi for Wi-Fi connectivity.
- WebServer for serving the web page.

You can install them from the Arduino Library Manager if not already installed.

### Code
Before uploading the code, **replace your_SSID and your_PASSWORD** with your actual Wi-Fi credentials.

#### Upload the following code onto the ESP32:
#include <WiFi.h> #include <WebServer.h>

```c
// Replace with your network credentials
const char* ssid = "your_SSID";
const char* password = "your_PASSWORD";

WebServer server(80);  // Create a web server on port

// Pin assignments for the 5 LEDs
const int ledPins[] = { 13, 12, 14, 27, 26 };
const int numLeds = 5;  // Number of LEDs

void setup() {
  // Start the serial communication
  Serial.begin(115200);
  // Set up the LED pins as outputs
```

### Explanation
```c
  for (int i = 0; i < numLeds; i++) {
    pinMode(ledPins[i], OUTPUT);
    digitalWrite(ledPins[i], LOW);  // Start with all LEDs off
  }

  // Connect to Wi-Fi
  WiFi.begin(ssid, password);
  Serial.print("Connecting to WiFi");

  // Wait for connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println();
  Serial.print("Connected to WiFi. IP Address: ");
  Serial.println(WiFi.localIP());

  // Define the root route
  server.on("/", HTTP_GET, handleRoot);

  // Define the route for controlling LED sequence
  server.on("/setBrightness", HTTP_GET, handleSetBrightness);

  // Start the web server
  server.begin();
}

void handleRoot() {
  String html = "<html><body>";
  html += "<h1>ESP32 Web Server with 5 LEDs Control</h1>";

  // Create the slider to control the LEDs
  html += "<label for=\"brightness\">Adjust LED Sequence:</label><br>";
```

  html += "<input type=\"range\" id=\"brightness\" name=\"brightness\" min=\"0\"

```c
max=\"100\" value=\"0\" oninput=\"updateLEDs(this.value)\">";
  html += "<span id=\"sliderValue\">0</span>%<br>";

  // Include a JavaScript to update the slider value and send it to the server
  html += "<script>";
  html += "function updateLEDs(value) {";
  html += "  document.getElementById('sliderValue').innerText = value;";
  html += "  fetch('/setBrightness?value=' + value);";
  html += "}";
  html += "</script>";

  html += "</body></html>";
  server.send(200, "text/html", html);
}
void handleSetBrightness() {
  String value = server.arg("value");  // Get the slider value from the URL
  int brightness = value.toInt();
  // Calculate how many LEDs should be on based on slider value
  int ledsOn = 0;

  if (brightness >= 0 && brightness < 20) {
    ledsOn = 0;
  } else if (brightness >= 20 && brightness < 40) {
    ledsOn = 1;
  } else if (brightness >= 40 && brightness < 60) {
    ledsOn = 2;
  } else if (brightness >= 60 && brightness < 80) {
    ledsOn = 3;
  } else if (brightness >= 80 && brightness < 100) {
    ledsOn = 4;
  } else if (brightness == 100) {
    ledsOn = 5;
  }

  // Turn LEDs on or off based on the slider value
  for (int i = 0; i < numLeds; i++) {
    if (i < ledsOn) {
      digitalWrite(ledPins[i], HIGH);  // Turn on the LED
    } else {
      digitalWrite(ledPins[i], LOW);  // Turn off the LED
    }
  }
  Serial.println(ledsOn);

  server.send(200, "text/plain", "LED sequence updated");
}

void loop() {
  // Handle client requests
  server.handleClient();
}
```

### Explanation
- The slider in the web interface will adjust the number of LEDs that are on in increments of 20%:
  - 0% → 0 LEDs on
  - 20% → 1 LED on
  - 40% → 2 LEDs on
  - 60% → 3 LEDs on
  - 80% → 4 LEDs on
  - 100% → All 5 LEDs on
- The slider value is sent to the server, which processes the request and updates the LEDs accordingly

using a simple if-else structure.

### Results
- Once you upload the code, open the **serial monitor** to see the ESP32's IP address.
- In a browser, go to the IP address shown in the serial monitor.
- You will see a slider. As you slide it, LEDs will turn on sequentially based on the value:
  - 0% → No LEDs on
  - 20% → First LED on
  - 40% → First two LEDs on
  - 60% → First three LEDs on
  - 80% → First four LEDs on
  - 100% → All ﬁve LEDs on

### Try for Yourself
- Try changing the number of LEDs based on the slider value in different patterns.
- Experiment with other types of controls, like adding fading effects or using different colours for each

LED.