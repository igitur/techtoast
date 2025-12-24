---
title: Web Server to Control an LED
---

Let's enhance the web server by adding an LED (we will use the built-in LED) to control it with a button on the web interface. The button will turn the LED on or off when pressed. Here’s how we can do that:

### Components Needed
- 1x ESP32
- 1x USB Programming Cable

### Connections
- We’ll be using the **built-in LED** on the ESP32, which is typically connected to **GPIO 2** (but this might vary

depending on the board). This eliminates the need for an external LED and connections.

### How to Install the Library
Make sure you have the WiFi and WebServer libraries installed, as mentioned earlier in the previous tutorial.

### Code
Before uploading the code, **make sure to replace your_SSID and your_PASSWORD** with your actual Wi-Fi network credentials.

#### Upload the following code onto the ESP32:

```c
#include <WiFi.h>
#include <WebServer.h>

// Replace with your network credentials
const char* ssid = "your_SSID";
const char* password = "your_PASSWORD";

WebServer server(80);  // Create a web server on port

// Pin assignment for the built-in LED
const int ledPin = 2;  // GPIO 2 is typically the built-in LED on the ESP32

// Variable to keep track of the LED state
bool ledState = LOW;

// Function to handle the root request
void handleRoot() {
  String html = "<html><body>";
  html += "<h1>ESP32 Web Server with Built-in LED Control</h1>";

  // Create a button to turn the LED ON/OFF
  if (ledState == LOW) {
    html += "<p><a href=\"/led/on\"><button>Turn LED ON</button></a></p>";
  } else {
    html += "<p><a href=\"/led/off\"><button>Turn LED OFF</button></a></p>";
  }

  html += "</body></html>";
  server.send(200, "text/html", html);
}

// Function to turn the LED on
void handleLedOn() {
  digitalWrite(ledPin, HIGH);
  ledState = HIGH;
  server.sendHeader("Location", "/");
  server.send(303);  // Redirect back to the main page
}

// Function to turn the LED off
void handleLedOff() {
  digitalWrite(ledPin, LOW);
  ledState = LOW;
  server.sendHeader("Location", "/");
  server.send(303);  // Redirect back to the main page
}

void setup() {
  // Start the serial communication
  Serial.begin(115200);

  // Set up the built-in LED pin
  pinMode(ledPin, OUTPUT);
  digitalWrite(ledPin, LOW);  // Start with the LED off

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

  // Define the LED control routes
  server.on("/led/on", HTTP_GET, handleLedOn);
  server.on("/led/off", HTTP_GET, handleLedOff);

  // Start the web server
  server.begin();
}

void loop() {
  // Handle client requests
  server.handleClient();
}
```

- The built-in LED is connected to **GPIO 2** (which is typical for many ESP32 boards, but verify if it’s

different for your speciﬁc model).

- The web server has a button that toggles the state of the built-in LED. If the LED is off, the button will say

"Turn LED ON", and vice versa.

- The **/led/on** route turns the LED on, while the **/led/off** route turns the LED off.
- The state of the LED is tracked with the ledState variable to ensure the button reﬂects the correct action

(on or off).

### Results
- Once the code is uploaded, open the serial monitor. When the ESP32 connects to Wi-Fi, it will display

its IP address.

- Open a browser and enter the IP address of the ESP32. You will see a button: **Turn LED ON** or **Turn LED**

**OFF** depending on the current state of the LED.

- Clicking the button will toggle the state of the built-in LED.

### Try for Yourself
- Add more buttons for additional actions, like controlling other pins or displaying information about the

device (e.g., temperature, humidity, etc.).

- Experiment with using more sophisticated HTML or adding CSS to style the page.