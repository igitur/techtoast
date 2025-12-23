---
title: Components Reference
---

# Components Reference

This section provides detailed information about each component in your TechToast ESP32 Basic Starter Kit. Understanding these components will help you build better projects and troubleshoot issues.

## Categories

- [**Development Board**](#development-board) - The ESP32 microcontroller
- [**Prototyping Tools**](#prototyping-tools) - Breadboard, cables, and wires
  - [Breadboard Basics](breadboard-basics.md) - Learn how to use your breadboard effectively
- [**Sensors**](#sensors) - Input devices that measure the environment
- [**Output Devices**](#output-devices) - LEDs, displays, and buzzers
- [**Input Devices**](#input-devices) - Buttons, switches, and potentiometers
- [**Passive Components**](#passive-components) - Resistors and other basic components
- [**Accessories**](#accessories) - Documentation and reference cards

## Development Board

### ESP32 Development Board
The heart of your projects. This powerful microcontroller features:
- **Built-in Wi-Fi and Bluetooth** for wireless connectivity
- **Dual-core processor** for efficient multitasking
- **Ample GPIO pins** for connecting multiple components
- **Support for SPI, I2C, and UART** communication protocols
- **Low-power modes** for battery-powered applications

## Prototyping Tools

### Double-Width Breadboard
- **830 tie points** for building complex circuits
- **No soldering required** - perfect for prototyping
- **Standard spacing** for integrated circuits and components
- **Learn more**: See [Breadboard Basics](breadboard-basics.md) for detailed usage instructions

### USB Programming Cable
- **Micro-USB to USB-A** cable
- **Provides power** to the ESP32 (5V)
- **Transmits data** for uploading code
- **Durable construction** for repeated use

### Jumper Wires
- **10x Male-to-Male** - For breadboard connections
- **10x Male-to-Female** - For connecting to ESP32 pins
- **Pre-cut and stripped** - Ready to use

## Sensors

### IR Obstacle Avoidance Module
- **Infrared-based** object detection
- **Adjustable sensitivity** with onboard potentiometer
- **Digital output** (HIGH/LOW) for easy reading
- **Ideal for robotics** and navigation projects

### Soil Moisture Sensor
- **Measures water content** in soil
- **Analog and digital outputs**
- **Adjustable threshold** with potentiometer
- **Perfect for smart gardening** projects

### Sound Sensor
- **Condenser microphone** for sound detection
- **Analog output** for sound intensity
- **Digital output** with adjustable threshold
- **Great for voice-activated** projects

### Water Level Sensor
- **Detects water presence** and level
- **Analog output** for precise measurement
- **Corrosion-resistant** electrodes
- **Useful for weather stations** and liquid monitoring

### DHT11 Temperature and Humidity Sensor
- **Measures temperature** (0-50°C ±2°C accuracy)
- **Measures humidity** (20-90% ±5% accuracy)
- **Digital output** for easy reading
- **Low cost and reliable**

### Thermistor
- **Temperature-sensitive resistor**
- **Resistance changes** with temperature
- **Analog measurement** required
- **Good for temperature monitoring**

### Photoresistor (LDR)
- **Light-dependent resistor**
- **Resistance decreases** with more light
- **Analog measurement** required
- **Perfect for light-sensing** projects

## Output Devices

### 7-Segment Display
- **Single-digit** numeric display
- **7 segments + decimal point**
- **Common anode** configuration
- **Easy to control** with GPIO pins

### Passive Buzzer
- **Generates tones** with varying frequencies
- **Requires PWM signal** to produce sound
- **Can play melodies** and custom tones
- **Ideal for audio feedback**

### Active Buzzer
- **Built-in oscillator** produces continuous tone
- **Simple on/off control** (HIGH/LOW signal)
- **Louder output** than passive buzzer
- **Good for alarms** and notifications

### RGB LED
- **Single LED** with red, green, and blue elements
- **Common cathode** configuration
- **PWM control** for color mixing
- **Create any color** by combining intensities

### Single-Color LEDs
- **5x Red LEDs** - Standard indicators
- **5x Green LEDs** - Status/power indicators
- **5x Yellow LEDs** - Warning/attention indicators
- **Require current-limiting resistors** (220Ω recommended)

## Input Devices

### Push Buttons (6x)
- **Momentary switches** - only active when pressed
- **4-pin design** for breadboard compatibility
- **Require pull-up/down resistors** for reliable reading
- **Perfect for user input** and control

### Tilt Switch
- **Mercury or ball-bearing** based switch
- **Closes circuit** when tilted
- **Digital output** (HIGH/LOW)
- **Great for orientation** detection

### Potentiometer
- **10kΩ variable resistor**
- **Adjustable voltage divider**
- **Analog output** (0-3.3V)
- **Useful for dimming**, volume control, etc.

## Passive Components

### Resistors
- **10x 220Ω** - For current-limiting with LEDs
- **10x 1kΩ** - General purpose, pull-up/down resistors
- **10x 10kΩ** - General purpose, pull-up/down resistors

### Resistor Colour Card
- **Quick reference** for resistor values
- **Color code chart** for identification
- **Handy tool** for beginners

## Accessories

### PDF Instruction Manual QR Code Card
- **Scannable QR code** linking to full manual
- **Quick access** to digital documentation
- **Useful reference** when away from computer

## Next Steps

Now that you're familiar with the components:
- Check out the [tutorials](../tutorials/index.md) to learn how to use them
- Visit [Getting Started](../getting-started/index.md) if you haven't set up your environment yet
- Combine components to create your own projects!