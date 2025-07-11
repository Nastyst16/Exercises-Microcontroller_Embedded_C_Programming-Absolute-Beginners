# 💡 STM32F4 - Bare Metal LED ON Example

This project demonstrates how to turn on an LED connected to pin **PD12** of the **STM32F407VG** microcontroller using **bare-metal C**, without relying on HAL or CMSIS libraries.

---

## 📄 Description

This example directly accesses the memory-mapped peripheral registers to:

1. Enable the **GPIOD** peripheral clock.
2. Configure **PD12** as a general purpose output.
3. Set **PD12** high, turning the LED on.

---

## 🔧 How it works

```
*pClkCtrlreg |= 0x08;
```
Enables the clock for GPIOD by setting bit 3 in RCC_AHB1ENR.

```
*pPortDModeReg &= ~(0b11 << 24);
*pPortDModeReg |=  (0b01 << 24);
```
Clears and sets the mode bits (24-25) to 0b01, which configures PD12 as output.

```
*pPortDOutReg |= 1 << 12;
```
Sets bit 12 of GPIOD_ODR to 1, driving PD12 high (LED ON).

## 📁 Memory Addresses Used

| Register      | Address      | Description                         |
|---------------|--------------|-------------------------------------|
| RCC_AHB1ENR   | 0x40023830   | Enables GPIOD peripheral clock      |
| GPIOD_MODER   | 0x40020C00   | Configures PD12 as output           |
| GPIOD_ODR     | 0x40020C14   | Sets PD12 high (LED ON)             |
