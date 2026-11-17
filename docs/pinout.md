# Pinout — Challenge #03

## Arduino Uno Connections

| Arduino Digital Pin | ATmega328P Port Bit | Connected Component | Direction | Purpose |
|---|---|---|---|---|
| D8 | PB0 | LED 1 | Output | Binary bit 0 (LSB) |
| D9 | PB1 | LED 2 | Output | Binary bit 1 |
| D10 | PB2 | LED 3 | Output | Binary bit 2 |
| D11 | PB3 | LED 4 | Output | Binary bit 3 (MSB) |
| D12 | PB4 | Pushbutton | Input | Button input, active LOW |
| GND | — | Pushbutton | — | Other side of the button |

## Wiring Notes

- Each LED is connected to its assigned output pin with a current-limiting resistor.
- The pushbutton is connected between D12 (PB4) and GND.
- No external pull-up resistor is used for the button. The firmware enables the Arduino's internal pull-up through `PORTB`.
- Because the button is active LOW, a pressed button reads LOW at PB4.

## LED Bit Order

| Counter bit | AVR bit | Arduino pin | Weight |
|---|---|---|---:|
| LSB | PB0 | D8 | 1 |
| Bit 1 | PB1 | D9 | 2 |
| Bit 2 | PB2 | D10 | 4 |
| MSB | PB3 | D11 | 8 |
