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
## 📤 OUTPUT

Each received CAN frame is printed to the serial port in the format:

```c
ID: 0x123  DLC: 8  Data: 0x11 0x22 0x33 0x44 0x55 0x66 0x77 0x88
```
Note: Due to library internals, extended IDs may appear to start with 0x8 or 0x9. This is not a bug — just a display artifact from the 29-bit format.

---
## 📄 License

Custom Non-Commercial License
Copyright (c) 2025 Giampiero

1. License Grant

This software is provided free of charge and may be used strictly for personal, educational, or non-commercial purposes.  
Any commercial use, resale, or distribution of this software—whether in original or modified form—is strictly prohibited without the explicit written consent of the author.

2. Restrictions

Redistribution is permitted only in its original, unmodified form, and exclusively for non-commercial use.  
You may not sublicense, sell, or bundle this software in any product or service intended for commercial distribution.

3. Disclaimer of Warranty

This software is provided "as is", without any express or implied warranties, including but not limited to merchantability, fitness for a particular purpose, or non-infringement.  
Use it at your own risk.

4. Limitation of Liability

In no event shall the author be held liable for any damage, data loss, malfunction, or legal claims resulting from the use, misuse, or inability to use this software.

For commercial licensing inquiries, please contact the author.

