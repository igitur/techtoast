---
title: First Program
---

# Step 4: Upload Your First Program

Now that your ESP32 is connected, let's upload a test program to make sure everything is working.

## The Blink Example

We'll use the classic "Blink" example, but modified for the ESP32's onboard LED.

### Open the Blink Example

1. **Open the Arduino IDE**
2. Go to **File > Examples > 01.Basics > Blink**

### Modify the Code for ESP32

The ESP32's onboard LED is typically connected to **GPIO 2**. Replace the code in the Blink example with:

```c
void setup() {
  pinMode(2, OUTPUT);  // Initialize digital pin 2 as an output
}

void loop() {
  digitalWrite(2, HIGH);  // Turn the LED on
  delay(1000);            // Wait for 1 second
  digitalWrite(2, LOW);   // Turn the LED off
  delay(1000);            // Wait for 1 second
}
```

### Upload the Code

1. **Click the Upload button** (right-facing arrow in the top left)
2. Wait for the upload to complete
3. You should see messages in the console at the bottom:
   - "Compiling sketch..."
   - "Uploading..."
   - "Done uploading."

## Verify the Blink

After the upload is complete:

1. Look at your ESP32 board
2. You should see a small blue LED blinking
3. It will turn on for 1 second, then off for 1 second, repeatedly

## Troubleshooting

If the LED doesn't blink:

### Check the LED Pin
- Some ESP32 boards have the onboard LED on a different pin
- Common alternatives: GPIO 5, GPIO 16, or GPIO 22
- Try changing `pinMode(2, OUTPUT)` to use a different pin number

### Check Upload Settings
1. Verify **Tools > Board** is set to "ESP32 Dev Module" (or "DOIT ESP32 DEVKIT V1")
2. Verify **Tools > Port** is set to the correct COM port
3. Verify **Tools > Upload Speed** is set to "921600" (or try "115200")

### Check Physical Connection
1. Make sure the USB cable is firmly connected
2. Try a different USB port on your computer
3. Try a different USB cable if available

## Success!

If the LED is blinking, congratulations! Your setup is complete and working correctly.

## What's Next?

Now that you've verified your setup:

1. **Explore the components** - Check out the [Components Reference](../components/index.md)
2. **Try a tutorial** - Start with something simple like [Push Button](../tutorials/push-button.md)
3. **Experiment** - Modify the blink code to change the timing or pattern

Remember to save your sketches regularly and have fun exploring!