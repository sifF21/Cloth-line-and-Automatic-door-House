
# Smart Home Automation: Wiring Diagram & Circuit Documentation

## Pin Configuration Summary

```
Arduino Uno Pin Assignments:
==============================
POWER PINS:
  - 5V (Red)    → Power supply for servos, LED, buzzer
  - GND (Black) → Ground for all components

ANALOG PINS:
  - A0  → Water Sensor (analog input)

DIGITAL PINS:
  - 6   → Door Servo Signal (PWM)
  - 7   → LED Positive (PWM)
  - 8   → Buzzer Positive (PWM)
  - 9   → Clothes Line Servo Signal (PWM)
  - 10  → HC-SR04 Trigger Pin (Output)
  - 11  → HC-SR04 Echo Pin (Input)
```

## Detailed Wiring Diagram

### 1. Water Sensor Connection
```
Water Sensor (Analog):
  - VCC   → Arduino 5V
  - GND   → Arduino GND
  - OUT   → Arduino A0 (Analog Input)

[Power Supply] ──[5V]──→ Water Sensor VCC
                         Water Sensor GND ←──[GND]
                         Water Sensor OUT ←──[A0]
```

### 2. Clothes Line Servo Motor
```
Servo Motor (Clothes Line):
  - Orange/Yellow (Signal) → Arduino Pin 9
  - Red (5V)               → Arduino 5V
  - Brown (GND)            → Arduino GND

                        ┌─────────────┐
                        │   Servo 1   │
                        │ Clothes Line│
     Arduino Pin 9 ────→│ Signal(O)   │
     Arduino 5V   ────→│ VCC   (R)   │
     Arduino GND  ────→│ GND   (B)   │
                        └─────────────┘
```

### 3. Door Servo Motor
```
Servo Motor (Door):
  - Orange/Yellow (Signal) → Arduino Pin 6
  - Red (5V)               → Arduino 5V
  - Brown (GND)            → Arduino GND

                        ┌─────────────┐
                        │   Servo 2   │
                        │    Door     │
     Arduino Pin 6 ────→│ Signal(O)   │
     Arduino 5V   ────→│ VCC   (R)   │
     Arduino GND  ────→│ GND   (B)   │
                        └─────────────┘
```

### 4. LED Indicator
```
LED (5V):
  - Positive (Long leg) → Arduino Pin 7
  - Negative (Short leg) → Arduino GND (through 220Ω resistor)

                    [220Ω Resistor]
                           │
     Arduino Pin 7 ─────→ [+] LED [-] ─────→ Arduino GND
```

### 5. Buzzer
```
Buzzer (5V):
  - Positive (Red/+) → Arduino Pin 8
  - Negative (Black/-) → Arduino GND

     Arduino Pin 8 ─────→ [+] Buzzer [-] ─────→ Arduino GND
```

### 6. Ultrasonic Sensor HC-SR04
```
HC-SR04 Sensor:
  - VCC   → Arduino 5V
  - GND   → Arduino GND
  - TRIG  → Arduino Pin 10
  - ECHO  → Arduino Pin 11

                    ┌──────────────┐
                    │  HC-SR04     │
                    │ (Ultrasonic) │
     Arduino 5V ───→│ VCC          │
     Arduino GND ──→│ GND          │
     Arduino Pin 10→│ TRIG         │
     Arduino Pin 11←│ ECHO         │
                    └──────────────┘
```

## Complete Wiring Table

| Component | Pin Type | Arduino Pin | Connection |
|-----------|----------|-------------|------------|
| Water Sensor | VCC | 5V | Power |
| Water Sensor | GND | GND | Ground |
| Water Sensor | OUT | A0 | Analog Input |
| Clothes Line Servo | Signal | 9 | PWM Output |
| Clothes Line Servo | VCC | 5V | Power |
| Clothes Line Servo | GND | GND | Ground |
| Door Servo | Signal | 6 | PWM Output |
| Door Servo | VCC | 5V | Power |
| Door Servo | GND | GND | Ground |
| LED | Positive | 7 | PWM Output (with 220Ω resistor) |
| LED | Negative | GND | Ground |
| Buzzer | Positive | 8 | PWM Output |
| Buzzer | Negative | GND | Ground |
| HC-SR04 | VCC | 5V | Power |
| HC-SR04 | GND | GND | Ground |
| HC-SR04 | TRIG | 10 | Output |
| HC-SR04 | ECHO | 11 | Input |

## Power Distribution

```
                    ┌─────────────────┐
                    │  USB Power or   │
                    │  External Power │
                    │  Supply (5V)    │
                    └────────┬────────┘
                             │
                    ┌────────┴────────┐
                    │    Arduino 5V   │
                    │    Arduino GND  │
                    └────────┬────────┘
                             │
            ┌────────────────┼────────────────┐
            │                │                │
      Water Sensor      Servos (x2)      LED/Buzzer
      (VCC + GND)      (VCC + GND)       (GND only)
```

## Assembly Instructions

### Step 1: Power Supply Setup
1. Connect 5V power supply to Arduino (via USB or external power)
2. Ensure all GND connections are connected together (common ground)

### Step 2: Sensor Connections
1. Connect water sensor to A0 (analog input)
2. Connect HC-SR04 TRIG to Pin 10 and ECHO to Pin 11

### Step 3: Servo Motors
1. Connect clothes line servo to Pin 9 (signal), 5V, and GND
2. Connect door servo to Pin 6 (signal), 5V, and GND
3. **Important:** Make sure servos have stable 5V power

### Step 4: Output Components
1. Connect LED to Pin 7 with 220Ω resistor in series to GND
2. Connect buzzer to Pin 8, negative to GND
3. Connect LED to Pin 7, negative to GND

### Step 5: Final Check
- Verify all connections match the wiring table
- Check for any loose connections
- Ensure all GND connections are properly grounded
- Test power supply before uploading code

## Important Notes

⚠️ **Power Considerations:**
- Servo motors draw significant current. Use a separate 5V power supply if possible
- If using Arduino USB power for servos, they may not operate smoothly
- Always use a current-limiting resistor (220Ω) with the LED to prevent burnout

⚠️ **HC-SR04 Sensor:**
- Requires 5V power supply
- ECHO pin outputs 5V signal; if using Arduino 3.3V-only board, use voltage divider
- Place sensor facing the area where objects will be detected

⚠️ **Servo Motors:**
- Ensure servo horns are properly attached
- Test servo movement before final installation
- Position servos for proper mechanical operation

## Breadboard Layout Example

```
[5V Supply] ────┬──── [Servo 1 VCC]
                 │
                 ├──── [Servo 2 VCC]
                 │
                 ├──── [Water Sensor VCC]
                 │
                 └──── [HC-SR04 VCC]

[GND Supply] ───┬──── [Servo 1 GND]
                 │
                 ├──── [Servo 2 GND]
                 │
                 ├──── [Water Sensor GND]
                 │
                 ├──── [HC-SR04 GND]
                 │
                 ├──── [LED GND] (through 220Ω resistor)
                 │
                 └──── [Buzzer GND]
```

## Testing the Wiring

After assembly, test each component:

1. **LED Test:** Should turn on via Pin 7
2. **Buzzer Test:** Should make sound via Pin 8
3. **Water Sensor Test:** Monitor A0 value with Serial Monitor
4. **HC-SR04 Test:** Monitor Pin 10/11 with Serial Monitor
5. **Servo Tests:** Should move to positions via Pin 6 and Pin 9

Upload the Arduino code and check Serial Monitor output for verification.
