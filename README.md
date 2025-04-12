# ITPicoTester
Pico HIL CI: On each push, a self‑hosted GitHub Action builds the student’s C firmware with CMake, flashes two real Raspberry Pi Pico boards (DUT &amp; tester), runs a Python‑driven GPIO blink test, and reports pass/fail results automatically.

# Pico HIL CI Pipeline

A turnkey GitHub‑driven hardware‑in‑the‑loop (HIL) testing framework for Raspberry Pi Pico C projects. On every push, your self‑hosted runner will:

1. **Checkout & build** the student’s C firmware using CMake & GNU Arm toolchain  
2. **Flash** two real Pico boards over USB:  
   - **DUT** (Device Under Test) runs the student’s blink firmware  
   - **Tester** runs a small test harness that can drive/read GPIOs  
3. **Exercise & verify** the blink pattern via a Python script over USB‑serial  
4. **Report** pass/fail back to GitHub Actions

---

## Features

- **Automated build** with Pico SDK & CMake  
- **Self‑hosted runner** for USB‑attached hardware  
- **HIL test harness** in C (or MicroPython) on the tester Pico  
- **Python validation** of GPIO waveforms  
- **Zero‑touch**: students simply push code and get immediate feedback  

---

## Prerequisites

- A Linux machine with USB ports  
- Two Raspberry Pi Pico boards (DUT + Tester)  
- GitHub repository with a **self‑hosted runner** labeled `self-hosted,linux,pico`  
- Installed dependencies on runner:  
  ```bash
  sudo apt update
  sudo apt install -y cmake gcc-arm-none-eabi build-essential libnewlib-arm-none-eabi python3-serial
