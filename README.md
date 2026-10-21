# MCP_CAN Sniffer

Basic CAN bus sniffer using MCP2515 with serial output. Italian and English status messages.
Setup is done via `config.h`, so the main sketch does not need to be modified.

---

## Hardware Requirements

- CAN module based on **MCP2515** on **UNO Shield** (random equivalent it's ok)
- Arduino-compatible board (e.g., Uno, Nano)
- MCP2515 oscillator: **16 MHz** or **8 MHz** (set `MCP_CLOCK_MHZ`)

---

## Quick Setup

0. Install the library: https://github.com/coryjfowler/MCP_CAN_lib
1. Clone or download the project
2. Open `config.h`
3. Set the following:
   - Language (`LOCALE`): `IT` or `EN`
   - Bus to sniff (`BUS`): `BUS_BH`, `BUS_C1`, `BUS_C2` or `BUS_CUSTOM`
   - Custom speed (`CUSTOM_SPEED`), used only with `BUS_CUSTOM`
   - MCP2515 clock (`MCP_CLOCK_MHZ`): `8` or `16`
   - Serial baudrate (`SERIAL_SPEED`) and CS/INT pins if your shield differs
4. Compile and upload to your board

---

## Bus Selection

| Option       | Speed    | Notes                   |
|--------------|----------|-------------------------|
| `BUS_BH`     | 125 kbps |                         |
| `BUS_C1`     | 500 kbps |                         |
| `BUS_C2`     | 500 kbps | Same speed as C1       |
| `BUS_CUSTOM` | Custom   | Value of `CUSTOM_SPEED` |

```c
#define BUS BUS_BH
```

---

## Languages

Set `LOCALE` in `config.h`:

```c
#define LOCALE IT  // Italian
//#define LOCALE EN  // English
```

Any other value causes a compile-time error.

---

## Output

Each received frame is printed on one line:

```
timestamp -> ID 0xXXX DLC:X 0xXX 0xXX ...
```

- **timestamp**: microseconds since boot (`micros()`)
- **ID**: hexadecimal, uppercase. Standard IDs (11 bit) use 3 digits, extended IDs (29 bit) use 8 digits
- **DLC**: number of data bytes
- **bytes**: hexadecimal, uppercase, 2 digits each

Example:

```
1234567 -> ID 0x0FA DLC:2 0x01 0xFF
1234568 -> ID 0x7A0 DLC:8 0x00 0x11 0x22 0x33 0x44 0x55 0x66 0x77
1234569 -> ID 0x18DAF110 DLC:8 0x02 0x10 0x03 0x00 0x00 0x00 0x00 0x00
```

Startup messages (`LABEL_START`, `LABEL_CAN_OK`, etc.) are printed before the frames, so filter out lines that do not start with a digit if your parser needs clean data.

---

## Initialization

If the MCP2515 is not detected, the sketch retries up to `CAN_INIT_MAX_TRIES` times (default 50) and then stops. Reset the board after fixing the wiring.

---

## License

Custom Non-Commercial License
Copyright (c) 2025 Giampiero

1. License Grant

This software is provided free of charge and may be used strictly for personal, educational, or non-commercial purposes.
Any commercial use, resale, or distribution of this software, whether in original or modified form, is strictly prohibited without the explicit written consent of the author.

2. Restrictions

Redistribution is permitted only in its original, unmodified form, and exclusively for non-commercial use.
You may not sublicense, sell, or bundle this software in any product or service intended for commercial distribution.

3. Disclaimer of Warranty

This software is provided "as is", without any express or implied warranties, including but not limited to merchantability, fitness for a particular purpose, or non-infringement.
Use it at your own risk.

4. Limitation of Liability

In no event shall the author be held liable for any damage, data loss, malfunction, or legal claims resulting from the use, misuse, or inability to use this software.

For commercial licensing inquiries, please contact the author.
