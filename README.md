# oled-hill-climb-game
ESP32 controlled hill climb racing game on 0.96inch oled display.
# Hill Climb 32 v2
A physics-based 2D hill climber game built for the ESP32 and a 0.96" SSD1306 OLED display. The repository includes two code versions to support playing with either analog joystick module or 5 push buttons.

## Game Features
* **Vehicles:** 8 playable vehicles (Jeep, Monster, Buggy, Tractor, Skyracer, Hippi Van, Tank, Supercar) with unique mass, engine, and suspension physics.
* **Stages:** 3 procedurally generated terrains (Countryside, Mountain, Highway).
* **Physics Engine:** Custom 2D physics simulating gravity, roll resistance, air drag, aerodynamic lift, and angular momentum.
* **Gameplay Mechanics:** Collect fuel to keep running and coins to score points; earn bonuses for flips and air time.
* **Persistent Data:** Best distances, vehicle/stage selections, and sound settings are saved to the ESP32 flash memory.
* **Audio:** Engine sounds and game melodies via a passive buzzer.

## Hardware Requirements
* ESP32 Development Module
* 0.96" I2C SSD1306 OLED Display
* Passive Buzzer
* Input Module: 5x Push Buttons OR 1x Analog Joystick module
* Breadboard and jumper wires

## Wiring Connections

### Display & Audio (Common for both versions)
| Component Pin | ESP32 Pin |
| OLED SDA | GPIO21 |
| OLED SCL | GPIO22 |
| OLED VCC | 3V3 |
| OLED GND | GND |
| Buzzer (+) | GPIO25 |
| Buzzer (-) | GND |

### Option 1: Joystick Setup
| Joystick Pin | ESP32 Pin |
| :--- | :--- |
| VRX (X-Axis) | GPIO34 |
| VRY (Y-Axis) | GPIO35 |
| SW (Switch) | GPIO32 |
| VCC | 3V3 |
| GND | GND |

### Option 2: Push Button Setup
Connect the following buttons between the ESP32 GPIO and GND (internal pull-ups are configured in the code).

| Button Action | ESP32 Pin |
| UP | GPIO32 |
| DOWN | GPIO33 |
| LEFT | GPIO26 |
| RIGHT | GPIO27 |
| OK | GPIO14 |

## Software Setup
* Install the `Adafruit GFX Library` and `Adafruit SSD1306` via the Arduino IDE Library Manager.
* `Wire.h` and `Preferences.h` are included by default in the ESP32 core.
* The I2C speed is configured to 400kHz by default, but can be adjusted to 800kHz (`I2C_SPEED`) in the code for smoother frame rates.