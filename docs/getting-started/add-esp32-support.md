---
title: Add ESP32 Support
---

# Step 2: Add ESP32 Support to the Arduino IDE

By default, the Arduino IDE doesn't support ESP32 boards. You need to add the ESP32 board package.

## Add ESP32 Board Manager URL

1. **Open the Arduino IDE**

2. **Go to File > Preferences** (or Arduino > Preferences on macOS)

3. In the "Additional Board Manager URLs" field, add the following URL:
   ```
   https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
   ```

4. **If you already have other URLs** in this field, separate them with commas:
   ```
   https://example.com/package_example_index.json,https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
   ```

5. **Click OK** to save the preferences

## Install the ESP32 Board Package

1. **Go to Tools > Board > Boards Manager**

2. In the search bar, type "**ESP32**"

3. Find the **"esp32 by Espressif Systems"** package

4. **Click the "Install" button**

5. Wait for the installation to complete - this may take a few minutes depending on your internet connection

## Verify Installation

1. Go to **Tools > Board**
2. You should now see **"ESP32 Arduino"** in the list
3. Expand it to see the available ESP32 boards

## Troubleshooting

If you encounter issues:

- **"Error downloading..."**: Check your internet connection and try again
- **Installation hangs**: Close and reopen the Arduino IDE, then try again
- **URL not accepted**: Make sure you've copied the URL exactly as shown above

## Next Step

Once the ESP32 board package is installed, proceed to [Connect Your ESP32](../getting-started/connect-esp32.md).