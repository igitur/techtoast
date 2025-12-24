---
title: Simple Web Server
---

Here's a simple tutorial to set up a web server using an ESP32. This project will allow you to create a basic web page hosted on the ESP32, which you can access from any device connected to the same network.

### Components Needed
- 1x ESP32
- 1x USB Programming Cable

### Connections
Since this is a simple web server example, there are no additional components that require connections to the ESP32. Just use the USB Programming Cable cable to power the ESP32.

### How to Install the Library
The ESP32 uses the WiFi library, which is already included in the Arduino IDE when you install the ESP32 board package.

### Code
#### Upload the following code onto the ESP32:

```c
#include <WiFi.h>
#include <WebServer.h>

// Replace with your network credentials
const char* ssid = "your_SSID";
const char* password = "your_PASSWORD";

WebServer server(80);  // Create a web server on port

// Function to handle the root request
void handleRoot() {
  server.send(200, "text/html", "<h1>Welcome to ESP32 Web Server</h1>");
}

void setup() {
  // Start the serial communication
  Serial.begin(115200);

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
  Serial.println(WiFi.localIP());

  // Define the root route
  server.on("/", HTTP_GET, handleRoot);

  // Start the web server
  server.begin();
}

void loop() {
  // Handle client requests
  server.handleClient();
}
```

### Explanation
- The ESP32 connects to your Wi-Fi network using the credentials provided (ssid and password).
- The WebServer library is used to create a simple server on port 80.
- The handleRoot function sends a basic HTML response when the root URL is accessed.
- Once connected to Wi-Fi, the ESP32 will print its IP address to the serial monitor.
- The web server listens for incoming requests and handles them with the handleClient function.

### Results
Once the code is uploaded, open the serial monitor. When the ESP32 connects to Wi-Fi, it will display its IP address. Enter this IP address into a browser on any device connected to the same network, and you should see the message **"Welcome to ESP32 Web Server"**.

### Try for Yourself
- Experiment with adding more routes to the web server, such as:
  - /status to show the current status of the ESP32.
  - /temperature if you add a sensor to the board.
- Customize the HTML page to make it more interactive, such as adding buttons to control GPIO pins.