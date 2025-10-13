# GautamOS v5.4 Ultimate Edition

**A versatile Arduino-based operating system with games, music, and utility features.**

**Developed by Gautam Krishna MV & Gaurav Co. Technologies (2025)**
[![Arduino Uno](https://img.shields.io/badge/Arduino-Uno-blue)](https://www.arduino.cc) [![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)GautamOS v5.4 Ultimate Edition

GautamOS v5.4 is a lightweight, interactive OS for the Arduino UNO, featuring Snake and Pong games, nostalgic Mario and Sonic music, a notepad with HTML rendering, a calculator, distance sensing, and LED control. Optimized for memory and speed, it offers an engaging experience for hobbyists.

## Features

- **Games**:
  - **Snake**: Navigate a 10x10 grid to eat food (`F`), avoiding walls and self-collision. Three difficulty levels (Easy: 600ms, Medium: 400ms, Hard: 200ms) with high score tracking. Controls: W (Up), A (Left), S (Down), D (Right), END to quit.
  - **Pong**: Move a paddle to hit a ball in a 10x5 grid, scoring points per hit. Controls: A (Left), D (Right), END to quit.
- **Music**:
  - Mario and Sonic themes as non-blocking background music during games.
  - Foreground music playback with `MUSICUI` command (Mario theme).
- **Notepad**: Store and render up to 20 lines with basic HTML tags (`<h1>`, `<p>`, `<b>`, `<i>`).
- **Calculator**: Perform basic arithmetic (addition, subtraction, multiplication, division).
- **Distance Sensor**: Measure distance using HC-SR04 sensor with alerts for objects within 20 cm.
- **LED Control**: Toggle or adjust LED blink rate (10-2000 ms).

## Hardware Requirements

- Arduino UNO
- HC-SR04 Ultrasonic Sensor (Trig: Pin 9, Echo: Pin 10)
- Piezo Buzzer (Pin 8)
- LED (Pin 13, built-in)
- USB connection for Serial Monitor (9600 baud)

## Setup Instructions

1. **Open in Arduino IDE**:
   - Load `GautamOS_v5.4_Snake_Pong.ino` in the Arduino IDE.
2. **Connect Hardware**:
   - Wire the HC-SR04 sensor (Trig to Pin 9, Echo to Pin 10).
   - Connect the piezo buzzer to Pin 8.
   - Use the built-in LED on Pin 13.
3. **Upload and Run**:
   - Upload the sketch to your Arduino UNO.
   - Open the Serial Monitor (9600 baud) to interact with GautamOS.

## Usage

- **Access Commands**:
  - Type `HELP` in the Serial Monitor to view all commands.
- **Commands**:
  - `HELP`: Display available commands.
  - `LED`: Toggle the LED.
  - `MUSICUI`: Play Mario theme.
  - `STOP`: Stop music playback.
  - `EDIT`: Enter notepad mode (type `END` to exit).
  - `SHOW`: Display notepad contents.
  - `RUN`: Render notepad as HTML.
  - `DISTANCE`: Toggle distance sensor.
  - `BLINKRATE`: Set LED blink rate (10-2000 ms).
  - `CALC`: Perform arithmetic (e.g., `5+7`).
  - `DIFFICULTY EASY/MEDIUM/HARD`: Set Snake game difficulty.
  - `GAME SNAKE`: Start Snake game.
  - `GAME PONG`: Start Pong game.

## Optimizations

- **Memory**:
  - Reduced note definitions to only those used in Mario and Sonic themes.
  - Stored song arrays in PROGMEM to minimize SRAM usage.
  - Limited snake length to 50 to prevent memory overflow.
  - Minimized String object usage in critical loops.
- **Performance**:
  - Reduced `loop()` delay to 5ms for faster response.
  - Lowered game input polling delay to 20ms for smoother gameplay.
  - Used `pgm_read_word` for efficient PROGMEM access.
  - Optimized game logic to reduce redundant calculations.

## Contributing

Contributions are welcome! Fork the repository, make changes, and submit a pull request. Test your code on an Arduino UNO for compatibility.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments

- Inspired by classic arcade games and retro music.
- Developed for educational and hobbyist purposes.
