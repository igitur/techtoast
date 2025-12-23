---
title: Connect ESP32
---

# Step 3: Connect Your ESP32 to Your Computer

Now that you have the Arduino IDE set up with ESP32 support, it's time to connect your ESP32 board.

## Physical Connection

1. **Use the USB programming cable** included in your kit
2. **Connect the USB end** to your computer
3. **Connect the micro-USB end** to your ESP32 board

## Install USB-to-Serial Driver (if necessary)

Some computers may not recognize the ESP32 immediately. If this happens, you may need to install a driver.

### Check if You Need a Driver

1. Connect your ESP32 to your computer
2. Open the Arduino IDE
3. Go to **Tools > Port**
4. If you see a COM port (Windows) or /dev/tty.* port (macOS/Linux) that wasn't there before, you don't need a driver
5. If no new port appears, you need to install a driver

### Install CP210x Driver (for most ESP32 boards)

Most ESP32 boards use the CP210x USB-to-serial chip. Download the driver from:

[https://drive.google.com/drive/folders/11AcB2xkQ5Xnx9VCZ0H-NXeFUSXAc_zY7?usp=drive_link](https://drive.google.com/drive/folders/11AcB2xkQ5Xnx9VCZ0H-NXeFUSXAc_zY7?usp=drive_link)

**Windows:**
1. Download the Windows driver
2. Run the installer
3. Restart your computer if prompted

**macOS:**
1. Download the macOS driver
2. Open the .dmg file
3. Run the installer package
4. You may need to allow the driver in System Preferences > Security & Privacy

**Linux:**
Most Linux distributions include the CP210x driver by default. If not, install it via your package manager:
```bash
sudo apt-get install brltty
```

## Select the Correct COM Port

1. **Open the Arduino IDE**
2. Go to **Tools > Port**
3. Select the port that corresponds to your ESP32

### Finding the Correct Port

If you're not sure which port is your ESP32:

1. Note all available COM ports
2. Unplug your ESP32
3. Check which port disappears from the list
4. Plug the ESP32 back in
5. The port that reappears is your ESP32

## Select the ESP32 Board

1. Go to **Tools > Board > ESP32 Arduino**
2. Select **"ESP32 Dev Module"**

   **Note:** If you encounter errors with "ESP32 Dev Module", try selecting **"DOIT ESP32 DEVKIT V1"** instead.

## Verify Connection

The ESP32 should now:
- Have a red power LED lit
- Be recognized by your computer
- Appear in the Arduino IDE port list

## Next Step

Now you're ready to [Upload Your First Program](../getting-started/first-program.md).