# Smart Home Automation: Clothes Line and Automatic Door

Arduino project for automated clothes line and automatic door system based on rain sensor and distance sensor.

## Description

This system is designed to automatically raise the clothes line when rain starts falling and open a door automatically when an object approaches. This project uses:

- Moisture/water sensor (analog input)
- Ultrasonic sensor HC-SR04
- 2 servo motors
- LED indicator
- Buzzer
- Arduino

## Features

- Clothes line automatically rises when water sensor value exceeds a certain threshold
- Clothes line lowers back when there is no rain
- Door automatically opens when an object is detected within 6 cm range
- Door closes back after 3 seconds
- LED and buzzer are used as status indicators

## Components Used

- Arduino Uno (or compatible board)
- Servo motor for clothes line
- Servo motor for door
- Analog water sensor
- Ultrasonic sensor HC-SR04
- 5V LED
- Buzzer
- Jumper wires and breadboard

## Pin Wiring

| Component | Arduino Pin |
| --- | --- |
| Water Sensor | A0 |
| Clothes Line Servo | 9 |
| Door Servo | 6 |
| Buzzer | 8 |
| LED | 7 |
| HC-SR04 Trigger | 10 |
| HC-SR04 Echo | 11 |

## How It Works

### 1. Automatic Clothes Line
- Water sensor value is measured on every loop cycle.
- If water sensor >= 300, the system assumes it's raining and raises the clothes line.
- If not raining, the clothes line stays in the lowered position.

### 2. Automatic Door
- HC-SR04 sensor monitors object distance.
- If distance <= 6 cm, the door opens to 90°.
- After 3 seconds, the door closes back.

### 3. Indicators
- LED turns on when door opens.
- Buzzer indicates rain condition and plays a chime when door opens.

## File Structure

- `Kode Arduino` — main Arduino program code file
- `README.md` — project documentation

## How to Run

1. Open `Kode Arduino` file in Arduino IDE.
2. Make sure board and serial port are correctly selected.
3. Upload the program to Arduino.
4. Connect all components according to the pin wiring diagram.
5. Run the system and observe the automatic responses.

## Notes

- The `batasAir` and `batasJarak` threshold values can be adjusted according to your needs.
- Use a stable power supply to ensure proper servo and component operation.
- For real-world use, it is recommended to add reinforced casing and cable protection.

## License

This project was created for learning purposes and the development of simple home automation systems.

## Author

Created by `sifF21`.
