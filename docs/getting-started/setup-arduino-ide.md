---
title: Install Arduino IDE
---

# Step 1: Install the Arduino IDE

The Arduino IDE (Integrated Development Environment) is the software you'll use to write code and upload it to your ESP32.

## Download the Arduino IDE

1. Go to the official Arduino website:
   [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)

2. Download the appropriate version for your operating system:
   - **Windows**: Download the Windows installer
   - **macOS**: Download the Mac version
   - **Linux**: Download the Linux 64-bit or 32-bit version (check your system architecture)

## Install the Arduino IDE

### Windows
1. Run the downloaded installer (.exe file)
2. Follow the installation wizard
3. Accept the license agreement
4. Choose installation options (defaults are usually fine)
5. Complete the installation

### macOS
1. Open the downloaded .dmg file
2. Drag the Arduino application to your Applications folder
3. If prompted about security, go to System Preferences > Security & Privacy and allow the app

### Linux
1. Extract the downloaded .tar.xz file:
   ```bash
   tar -xvf arduino-*.tar.xz
   ```
2. Move to a permanent location:
   ```bash
   sudo mv arduino-* /opt/arduino/
   ```
3. Run the install script:
   ```bash
   cd /opt/arduino
   sudo ./install.sh
   ```

## Verify Installation

1. Open the Arduino IDE
2. You should see a blank sketch with `setup()` and `loop()` functions
3. The interface should be responsive

## Next Step

Once you have the Arduino IDE installed, proceed to [Add ESP32 Support](../getting-started/add-esp32-support.md).