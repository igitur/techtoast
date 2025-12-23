---
title: Setting Up & Writing Your First Program
---

# Setting Up & Writing Your First Program

Here’s a clear and concise guide to getting started with the Arduino IDE and ESP32:

### Step 1: Install the Arduino IDE
1. Download the Arduino IDE from the official Arduino website:

[https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)
2. Install the IDE by following the instructions for your operating system (Windows, macOS, or Linux).

### Step 2: Add ESP32 Support to the Arduino IDE
1. **Open the Arduino IDE.**
2. **Go to File > Preferences.**
  - In the "Additional Board Manager URLs" ﬁeld, add the following URL:

[https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json](https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json)
  - If there are multiple URLs, separate them with a comma.
3. **Click OK** to save the preferences.

### Step 3: Install the ESP32 Board Package
1. **Go to Tools > Board > Boards Manager.**
2. Search for "ESP32" in the search bar.
3. Click "Install" on the **"esp32 by Espressif Systems"** package.
4. Wait for the installation to complete.

### Step 4: Select the ESP32 Board
1. **Go to Tools > Board > ESP32.**
2. Select the “**ESP32 Dev Module**”. If this board gives an error in any of the following tutorials, change the board to the “**DOIT ESP32 DEVKIT V1**”.

### Step 5: Install the USB-to-Serial Driver (if necessary)
- If your computer does not recognize the ESP32, install the appropriate USB driver.
  - For boards using the **CP210x** chip: Download CP210x drivers here:

[https://drive.google.com/drive/folders/11AcB2xkQ5Xnx9VCZ0H-NXeFUSXAc_zY7?usp=drive_link](https://drive.google.com/drive/folders/11AcB2xkQ5Xnx9VCZ0H-NXeFUSXAc_zY7?usp=drive_link)

### Step 6: Connect the ESP32 to Your Computer
1. Use the USB programming cable to connect your ESP32 to your computer.
2. **Select the correct COM port:**
  - Go to **Tools > Port** and select the port your ESP32 is connected to.
  - To ﬁnd the correct COM port for your ESP32, plug the device into your computer via USB and
  - pen the Arduino IDE. Then, go to "Tools" > "Port" and note the available COM ports. Unplug the

ESP32, and check which COM port disappears from the list. Plug it back in, and the COM port that reappears is the correct one for your ESP32.

Select that port to upload your code.

### Step 7: Upload a Test Sketch
1. Open the **Blink example sketch**:
  - Go to **File > Examples > 01.Basics > Blink.**
2. Change the pin number to **2**, as the onboard LED of the ESP32 is typically connected to GPIO2:

```c
void setup() {
  pinMode(2, OUTPUT);
}

void loop() {
  digitalWrite(2, HIGH);  // Turn the LED on
  delay(1000);            // Wait for 1 second
  digitalWrite(2, LOW);   // Turn the LED off
  delay(1000);            // Wait for 1 second
}
```

3. Click the **Upload button** (the right-facing arrow).

### Step 8: Verify the Blink
1. After the upload is complete, the onboard LED on your ESP32 should start blinking.
2. If the LED blinks as expected, your setup is complete!