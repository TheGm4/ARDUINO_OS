# Tiny Arduino HTML Notepad OS

A compact "OS" for Arduino Uno managing an HTML notepad, LED control with adjustable blink rate, melody playback, and ultrasonic distance measurement with piezo warning. Uses `millis()` for non-blocking operation, no libraries. Control via Serial Monitor.

[![Arduino Uno](https://img.shields.io/badge/Arduino-Uno-blue)](https://www.arduino.cc) [![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## Features
- **HTML Notepad**: Store 20 lines, render `<h1>`, `<p>`, `<b>`, `<i>`, `<br>`.
- **LED**: Blinks at adjustable interval (default 500ms); toggle via command; solid during music.
- **Music**: Plays Kompa, Mario, Sonic on piezo buzzer.
- **Distance**: Measures every 2s when enabled; piezo beeps if object < 20 cm.
- **Serial Interface**: Command-line control, no buttons.

## Hardware Requirements
- Arduino Uno
- Piezo Buzzer (pin 8 to GND)
- HC-SR04 (Trig: pin 9, Echo: pin 10, VCC: 5V, GND)
- LED (built-in on pin 13)
- USB cable, Arduino IDE (1.8.19+)

## Setup
1. Clone/download:
   ```bash
   git clone https://github.com/TheGm4/first-ever-arduino-os.git
   ```
   Or ZIP [here](https://github.com/TheGm4/first-ever-arduino-os/archive/refs/heads/main.zip).
2. Open `OPERATING_SYSTEM.ino` in Arduino IDE.
3. Set **Tools > Board > Arduino Uno**, select port.
4. Upload code (**Sketch > Upload**).
5. Open Serial Monitor (**Tools > Serial Monitor**, 9600 baud, Newline):
   ```
   === Tiny GautamOs HTML Notepad OS BY GAUTAM KRISHNA MV (1st patreon GAURAV my own brother)===
   Commands: HELP, LED, MUSICUI, EDIT, SHOW, CLEAR, RUN, STOP, DISTANCE, BLINKRATE
   Gautam&Gaurav co. technologies>
   ```
6. Connect hardware:
   - Buzzer: Pin 8 to GND.
   - HC-SR04: Trig to 9, Echo to 10, VCC to 5V, GND.
   - LED: Built-in on pin 13 (no wiring needed).

## Usage
- Enter commands at `Gautam&Gaurav co. technologies>` (case-insensitive).
- `EDIT`: Add HTML lines; `END` to exit.
- `MUSICUI`: Select song; `STOP` to stop.
- `DISTANCE`: Toggle distance measurement; piezo warns if < 20 cm.
- `BLINKRATE`: Set LED blink interval (100–2000 ms).
- LED blinks; solid during music.

## Commands
| Command     | Description |
|-------------|-------------|
| `HELP`      | List commands, tags, songs. |
| `LED`       | Toggle LED. |
| `MUSICUI`   | Select song (KOMPA, MARIO, SONIC). |
| `STOP`      | Stop music. |
| `EDIT`      | Add HTML lines (max 20). |
| `SHOW`      | Show notepad content. |
| `CLEAR`     | Clear notepad. |
| `RUN`       | Render HTML. |
| `DISTANCE`  | Toggle distance measurement. |
| `BLINKRATE` | Set LED blink interval (100–2000 ms). |

## Supported HTML Tags
| Tag         | Input Example        | Output           |
|-------------|----------------------|------------------|
| `<h1></h1>` | `<h1>Title</h1>`     | `=== Title ===`  |
| `<p></p>`   | `<p>Text</p>`        | `Text`           |
| `<b></b>`   | `<b>Bold</b>`        | `**Bold**`       |
| `<i></i>`   | `<i>Italic</i>`      | `_Italic_`       |
| `<br>`      | `<br>`               | (Empty line)     |

## Supported Songs
| Song   | Description |
|--------|-------------|
| `KOMPA`| Kompa Passion riff. |
| `MARIO`| Super Mario Bros theme. |
| `SONIC`| Sonic the Hedgehog riff. |

## Examples
### Music
```plaintext
Gautam&Gaurav co. technologies> MUSICUI
Select: KOMPA, MARIO, SONIC
SONIC
Playing SONIC
Gautam&Gaurav co. technologies> STOP
Stopped music.
```

### HTML
```plaintext
Gautam&Gaurav co. technologies> EDIT
EDIT mode: Enter HTML. Type END.
<h1>Sonic</h1>
Added: <h1>Sonic</h1> (1/20)
<p>Fast!</p>
Added: <p>Fast!</p> (2/20)
END
Gautam&Gaurav co. technologies> RUN
---- Rendering HTML ----
=== Sonic ===
Fast!
------------------------
```

### Distance
```plaintext
Gautam&Gaurav co. technologies> DISTANCE
Distance enabled.
Distance: 25 cm
Distance: 15 cm
Warning: Object at 15 cm!
Gautam&Gaurav co. technologies> DISTANCE
Distance disabled.
```

### Blink Rate
```plaintext
Gautam&Gaurav co. technologies> BLINKRATE
Enter blink interval (100-2000 ms):
1000
Set blink interval to 1000 ms
Gautam&Gaurav co. technologies>
```

## Troubleshooting
- **No Serial**: Check USB/port, 9600 baud, Newline.
- **No Sound**: Verify buzzer (pin 8, GND). Test: `tone(8, 1000, 100);`.
- **Bad Distance**: Check HC-SR04 (Trig: 9, Echo: 10, VCC: 5V, GND). Range 2–400 cm.
- **No LED**: Verify built-in LED on pin 13.
- **Memory Warning**: Reduce `MAX` to 10 in `OPERATING_SYSTEM.ino`.

## Contributing
Fork, edit, submit PR. Report issues at [GitHub Issues](https://github.com/TheGm4/first-ever-arduino-os/issues).

## License
[MIT License](LICENSE)