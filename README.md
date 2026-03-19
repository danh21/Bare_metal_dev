# 📦 Project Name

> Bare-metal embedded development.

---

## 📚 Table of Contents

- [📦 Project Name](#-project-name)
  - [📚 Table of Contents](#-table-of-contents)
  - [📝 About](#-about)
  - [✨ Features](#-features)
  - [🚀 Getting Started](#-getting-started)
    - [Prerequisites](#prerequisites)
    - [Source](#source)
    - [Usage](#usage)
    - [Reference](#reference)

---

## 📝 About

> Investigate build procedure and linker script for bare metal embedded systems (ARM Cortex Mx)

---

## ✨ Features

- ✅ Bare-metal development (startup code, linker script, led driver, blinky sample app)
- ✅ Debug printf using semi-hosting

---

## 🚀 Getting Started

### Prerequisites

- List software dependencies or system requirements here:
  - GNU Arm Embedded Toolchain (arm-none-eabi-gcc, arm-none-eabi-gdb)
  - Make utility
  - OpenOCD
  - PuTTY

### Source

| File                  | Description |
|-----------------------|-------------|
| Makefile              | Build script for compiling source files and linking into ELF binaries. |
| source/main.c         | Main application code implementing a simple task scheduler for ARM Cortex-M. |
| source/led.c          | LED control functions for STM32 board. |
| source/led.h          | Header file with LED definitions and function prototypes. |
| source/main.h         | Header file with main application constants and macros. |
| source/stm32_startup.c| Startup code for initializing the STM32 microcontroller. |
| source/stm32_ls.ld    | Linker script defining memory layout for STM32. |
| source/syscalls.c     | System call implementations for bare-metal environment. |

### Usage

- Build normal project: **make**
- Build project combined with semi-hosting: **make semi**
- Clear build artifacts: **make clean**
- Open Command Prompt, setup OpenOCD server: **make load**
- Solution 1: Open another Command Prompt, setup GDB connection: **arm-none-eabi-gdb**
  - Connect to OpenOCD server via port 3333: **target remote localhost:3333**
  - Flash executable: **monitor flash write_image erase out/final.elf** or **monitor flash write_image erase out/final_sh.elf** (enable semihosting)
  - [optional] Enable semihosting: **monitor arm semihosting enable**
  - Reset board: **monitor reset**
- Solution 2: Use PuTTY
  - Host Name (or IP address): **localhost**
  - Port: **4444**
  - Connection type: **Telnet**
  - Saved Sessions, create new and save
  - **Open**
  - Flash executable: **flash write_image erase out/final.elf** or **flash write_image erase out/final_sh.elf** (enable semihosting)
  - [optional] Enable semihosting: **arm semihosting enable**
  - Reset board: **reset**

### Reference

- https://www.udemy.com/course/embedded-system-programming-on-arm-cortex-m3m4/?referralCode=12E4B80663C357C4F867