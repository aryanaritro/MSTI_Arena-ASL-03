# Test Results — Challenge #03

## Test Environment

- Simulator: Wokwi
- Board: Arduino Uno
- Input: One pushbutton on D12 (PB4)
- Outputs: Four LEDs on D8–D11 (PB0–PB3)

## Functional Test Results

| Test | Expected Result | Observed Result | Status |
|---|---|---|---|
| Initial state | Counter starts at 0 (`0000`) | Simulation started with the LEDs representing zero | PASS |
| Button press | Counter increments once per accepted press | Counter incremented sequentially | PASS |
| Binary LED display | LEDs show the 4-bit counter value | LED pattern followed the counter value | PASS |
| Decimal Serial output | Serial Monitor prints the decimal count | Decimal values printed from 1 through 15, then 0 | PASS |
| Binary Serial output | Serial Monitor prints a 4-bit binary value | Binary values printed beside decimal values | PASS |
| Counter rollover | After 15 (`1111`), next count is 0 (`0000`) | Output reached 15 and then returned to 0 | PASS |
| Button debounce / release handling | One accepted count per press; wait for release | Firmware uses a 50 ms debounce and waits for release | PASS |

## Observed Serial Output

```text
1 = 0001
2 = 0010
3 = 0011
4 = 0100
5 = 0101
6 = 0110
7 = 0111
8 = 1000
9 = 1001
10 = 1010
11 = 1011
12 = 1100
13 = 1101
14 = 1110
15 = 1111
0 = 0000
```

## Verification Scope

The above results are based on the reported successful Wokwi simulation. No separate physical-hardware test is documented here.
