# System Architecture

## Overview

The system is a 4-bit binary click counter implemented on an Arduino Uno (ATmega328P). A pushbutton connected to D12 increments the counter. Four LEDs connected to D8–D11 display the current count in binary.

## Functional Flow

1. The microcontroller initializes the serial interface.
2. `DDRB` configures PB0–PB3 as outputs and PB4 as an input.
3. `PORTB` enables the internal pull-up on PB4 and initializes the LED outputs to `0000`.
4. The main loop checks PB4 through `PINB`.
5. When a press is detected, the firmware applies a 50 ms debounce delay and checks the button again.
6. The 4-bit counter increments. After 15, it wraps to 0.
7. A single `PORTB` register write updates the four LED outputs while keeping the PB4 pull-up enabled.
8. The Serial Monitor prints the decimal count and its 4-bit binary representation.
9. The firmware waits for button release before accepting the next press.

## Register Responsibilities

| Register | Use |
|---|---|
| `DDRB` | Sets PB0–PB3 as outputs and PB4 as input. |
| `PORTB` | Sets the LED output bits and enables the PB4 internal pull-up. |
| `PINB` | Reads the pushbutton state on PB4. |

## Counter Representation

The counter is restricted to four bits, so its range is 0–15. The low four bits are sent to PB0–PB3, with PB0 representing the least significant bit (LSB) and PB3 the most significant bit (MSB).

## Serial Output

Each accepted press prints the decimal count followed by its four-bit binary value, for example:

```text
1 = 0001
2 = 0010
3 = 0011
...
15 = 1111
0 = 0000
```
