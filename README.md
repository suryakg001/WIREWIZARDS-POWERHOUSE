# Cold Storage Temperature Stability Monitor

An Arduino-based prototype that monitors cold-storage temperature and alerts the user when it moves outside the configured safe range of **4°C to 8°C**. The temperature is displayed on a 16×2 I2C LCD. A buzzer and warning LED indicate unsafe temperatures, while a DC fan turns on when the temperature rises above the upper limit.

## Features

- Reads temperature using a TMP36 sensor
- Displays temperature and system status on an I2C LCD
- Activates a warning LED and buzzer when the temperature is out of range
- Turns on a DC fan when the temperature is too high
- Uses separate switch-off thresholds to reduce rapid fan switching
- Can be simulated in Tinkercad Circuits

## Components

- Arduino Uno
- TMP36 temperature sensor
- 16×2 I2C LCD
- DC motor/fan
- NPN transistor and 1 kΩ resistor for motor control
- Diode across the motor
- Warning LED and 220 Ω resistor
- Low-temperature indicator LED and 220 Ω resistor
- Buzzer
- Jumper wires

## Temperature Logic

| Temperature | System response |
|---|---|
| Above 8°C | Displays “TOO HOT”; warning LED and buzzer turn on; fan turns on |
| Below 4°C | Displays “TOO COLD”; warning LED, buzzer, and low-temperature indicator turn on |
| Within 4°C–8°C | Displays “TEMP: STABLE”; alerts and fan turn off |

The fan switches off at 7.5°C, and the low-temperature indicator switches off at 4.5°C. These reset points help prevent rapid ON/OFF switching.

## Pin Connections

| Component | Arduino pin |
|---|---|
| TMP36 output | A0 |
| I2C LCD SDA | A4 |
| I2C LCD SCL | A5 |
| Warning LED | D9 |
| Buzzer | D8 |
| Fan transistor control | D10 |
| Low-temperature indicator LED | D6 |

Connect the TMP36 power pins and the LCD power pins according to their labels. Control the DC motor through the transistor; do not connect the motor directly to an Arduino output pin. Connect the motor diode across the motor terminals.

## How to Run

1. Open the circuit in Tinkercad Circuits.
2. Open the Arduino code editor and add the project code.
3. Start the simulation.
4. Change the TMP36 temperature in the simulator.
5. Check the LCD, warning LED, buzzer, and fan response at different temperatures.

## Limitations

This is a prototype demonstrated in Tinkercad. The simulated fan does not physically change the TMP36 temperature. The low-temperature LED indicates a heating response; it is not an actual heater. The current version uses threshold-based control and does not use machine learning.

## Project Purpose

The project demonstrates how continuous temperature monitoring and automatic alerts can help identify unsafe conditions in cold-storage environments.
