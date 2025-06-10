# 🛠️ MCP_CAN Multilanguage Sniffer

Basic CAN bus sniffer using MCP2515 with serial output and multi-language support.  
Simple setup via `config.h` — no need to modify the main source file.

---

## ⚙️ Hardware Requirements

- CAN module based on **MCP2515** on **UNO Shield**
- Arduino-compatible board (e.g., Uno, Nano)
- Module clock: **16 MHz** (can be adjusted)

---

## 🚀 Quick Setup

0. Install https://github.com/coryjfowler/MCP_CAN_lib
1. Clone or download the project
2. Open `config.h`
3. Set the following:
   - Serial baudrate (`SERIAL_SPEED`)
   - CAN baudrate (`CAN_SPEED`)
   - MCP Clock (`MCP_CLOCK`)
   - Language (`LOCALE`)
4. Compile and upload on your board

---

## 🌐 Supported Languages

Set your preferred language by editing the `LOCALE` value in `config.h`:

```c
#define LOCALE IT  // Italian
//#define LOCALE FR  // French
//#define LOCALE ES  // Spanish
//#define LOCALE DE  // German
//#define LOCALE PT  // Portuguese
//#define LOCALE NL  // Dutch
//#define LOCALE EN  // English (default)
```
---
## OUTPUT

Each received CAN frame is printed to the serial port in the format:

```c
ID: 0x123  DLC: 8  Data: 0x11 0x22 0x33 0x44 0x55 0x66 0x77 0x88
```
Note: Due to library internals, extended IDs may appear to start with 0x8 or 0x9. This is not a bug — just a display artifact from the 29-bit format.

---
## License

1. License Grant

This software is provided free of charge and may be used for personal and non-commercial purposes only. Any commercial use, distribution, or resale of this software is strictly prohibited without the explicit written consent of the author.

2. Restrictions

Redistribution of the software is allowed only in its original, unmodified form and for non-commercial purposes.

3. Disclaimer of Warranty

This software is provided "as is", without any express or implied warranties. The author assumes no responsibility for any damages, direct or indirect, that may arise from the use of this software.

4. Liability Limitation

By using this software, you agree that the author is not liable for any issues, malfunctions, data loss, or damages caused by its use.
