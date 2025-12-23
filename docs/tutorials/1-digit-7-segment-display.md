---
title: 1-Digit 7-Segment Display
---

### Components Needed
- 1x ESP32
- 1x USB Programming Cable
- 1x 1-Digit 7-Segment Display (5161AS)
- 9x Male-to-Male Jumper Wires
- 1x 220Ω Resistor (Red-Red-Brown)
- 2x Breadboards

### Connections
Using the breadboard, connect the components to the ESP32 as follows:

- **Segment A** → ESP32 D18
- **Segment B** → ESP32 D19
- **Segment C** → ESP32 D21
- **Segment D** → ESP32 D22
- **Segment E** → ESP32 D23
- **Segment F** → ESP32 D25
- **Segment G** → ESP32 D26
- **Both Common Anodes (-)** → 220Ω Resistor → ESP32 3V3

### Code
#### Upload the following code onto the ESP32:
```
// Pin configuration for the 7-segment display
int segmentA = 18;
int segmentB = 19;
int segmentC = 21;
int segmentD = 22;
int segmentE = 23;
int segmentF = 25;
int segmentG = 26;

// Digits 0-9, where each bit represents a segment (A-G)
byte digits[] = {
```

  B1111110,  // 0   B0110000,  // 1   B1101101,  // 2   B1111001,  // 3   B0110011,  // 4   B1011011,  // 5   B1011111,  // 6   B1110000,  // 7   B1111111,  // 8   B1111011   //

```c
};

void setup() {
  // Set all segment pins as output
  pinMode(segmentA, OUTPUT);
  pinMode(segmentB, OUTPUT);
  pinMode(segmentB, OUTPUT);
  pinMode(segmentC, OUTPUT);
  pinMode(segmentD, OUTPUT);
  pinMode(segmentE, OUTPUT);
  pinMode(segmentF, OUTPUT);
  pinMode(segmentG, OUTPUT);
}

void loop() {
  for (int i = 0; i < 10; i++) {
    displayDigit(i);
    delay(1000);  // Delay for 1 second before showing next number
  }
}

void displayDigit(int digit) {
  byte segmentsState = digits[digit];

  // Control each segment based on the digit's binary value
  digitalWrite(segmentA, (segmentsState & B1000000) ? HIGH : LOW);  // Segment A
  digitalWrite(segmentB, (segmentsState & B0100000) ? HIGH : LOW);  // Segment B
  digitalWrite(segmentC, (segmentsState & B0010000) ? HIGH : LOW);  // Segment C
  digitalWrite(segmentD, (segmentsState & B0001000) ? HIGH : LOW);  // Segment D
  digitalWrite(segmentE, (segmentsState & B0000100) ? HIGH : LOW);  // Segment E
  digitalWrite(segmentF, (segmentsState & B0000010) ? HIGH : LOW);  // Segment F
  digitalWrite(segmentG, (segmentsState & B0000001) ? HIGH : LOW);  // Segment G
}
```

### Explanation
The **1-Digit 7-Segment Display (5161AS)** consists of 7 segments (labeled A-G) that can be individually controlled to display numbers from 0 to 9. Each segment is either turned **ON** or **OFF** to form the desired digit. This display uses a **common anode** conﬁguration, meaning the common pin is connected to a positive voltage (3.3V) and the individual segments are connected to GPIO pins of the ESP32. To turn a segment **ON**, the corresponding GPIO pin is set to **LOW** (active low), and to turn it **OFF**, the pin is set to **HIGH**.

The code uses speciﬁc GPIO pins on the ESP32 to control each segment of the display.

The program works by turning **ON** and **OFF** the segments in a speciﬁc pattern, depending on the digit to be displayed. It sequentially displays numbers from 0 to 9, using a binary representation of each digit where each bit corresponds to a segment (A-G). By checking the bits of the binary digit, the code determines which segments need to be activated and sets the corresponding GPIO pins to either **LOW** (turn segment ON) or **HIGH** (turn segment OFF).

### Results
After uploading the code, the 7-segment display will sequentially show the numbers 0 through 9. Each digit will be displayed for one second before moving on to the next. The display will show the correct segments for each number based on its binary pattern.

### Try for Yourself
1. Modify the code to display a custom number.
2. Try creating your own pattern on the display by changing the pin states.