# HC-12_WirelessModule_with_PICO
## Introduction
The HC-12 wireless serial port communication module is a multichannel embedded wireless data transmission module. Its wireless working frequency band is 433.4-473.0MHz. Multiple channels can be set, with a channel stepping of 400kHz, giving a total of 100 channels. The maximum transmitting power of the module is 100mW (20dBm), and the receiving sensitivity is -117dBm at a baud rate of 5000bps in the air. Communication distance is 1000m (FU3 mode at 4800bps serial speed) in open space, 1800m in FU4 mode at reduced baud rate and volume of data).

There is an MCU inside the module, so the user does not need to program the radio section separately, with transparent half-duplex serial transmission provided for receiving and sending serial port data, making the HC-12 easy to interface with. The module adopts multiple serial port transparent transmission modes that are user-selected by AT commands according to usage requirements. The average working current of the four modes FU1, FU2, FU3, and FU4 in the idle state are: 3.6mA, 80uA, 16mA, and 16mA respectively, and the maximum working current in any mode is 100mA (in the transmitting state).

| | |
| :---: |:---: |
| <img src="https://github.com/Aarushraj-Puduchery/HC-12_WirelessModule_with_PICO/assets/97360295/db5280c9-9d2e-48e4-9b95-146595e2a4bc" width="60%" height="60%" align="middle" /> | <img src="https://github.com/Aarushraj-Puduchery/HC-12_WirelessModule_with_PICO/assets/97360295/1fae761a-b3d4-478f-b5fc-9d04ada1ca39" width="70%" height="70%" align="middle" /> |


## Features
- Long-distance wireless transmission (FU3: 1000m in open space, baud rate 5000bps in the air. FU4: 1800m in open space, 500bps baud rate in the air).
- Working frequency range (433.4-473.0MHz, with 100 communication channels).
- Maximum 100mW (20dBm) transmitting power (8 levels of power can be set).
- Built-in MCU performs communication with an external device through a serial port, no programming or configuration is required for basic use.
- The number of bytes transmitted continuously is unlimited (FU1 and FU3 modes only).
- Update the software version through the serial port.

## Applications
- Wireless sensor
- Community building security
- Robot wireless control
- Industrial RC and telemetry
- Automatic data acquisition
- Container information management
- Wireless acquisition of gas meter data
- Vehicle keyless entry system

## Dimensions
<img src="https://github.com/Aarushraj-Puduchery/HC-12_WirelessModule_with_PICO/assets/97360295/e503cdb6-272b-4e29-88f7-52f3f5cf2a54" width="60%" height="60%" />

## Pins
| Pin | Definition | I/O direction | Notes |
| :---: | :---: | --- | --- |
| 1 | Vcc | | Power supply input, DC3.2V-5.5V, with loadcapacity not less than 200mA. |
| 2 | GND | | Common ground |
| 3 | RxD | Input (weak pullup) | UART data input, TTL level. 1k resistor connected in series inside the module |
| 4 | TxD | Output | UART data output, TTL level. 1k resistor connected in series inside the module |
| 5 | SET | Input (10k pullup) | Parameter setting control pin, active low level. 1k resistor connected in series inside the module |
| 6 | ANT | Input/Output | 433MHz antenna pin |
| 7 | GND | | Common ground | 
| 8 | GND | | Common ground |
| 9 | NC | | No connection, used in mechanical fixing, compatible with HC-11 module pin position |
| ANT1 | ANT | Input/Output | IPEX20279-001E-03 antenna socket |
| ANT2 | ANT | Input/Output | 433MHz spring antenna solder eye |

## Components List
|  Name  | Cost | Quantity | Total Cost | Link |
| ---- | :---: | :---: | :---: | --- |
| HC-12 433 SI4463 Wireless Serial Module | ₹320.00 | 2 | ₹640.00| https://robu.in/product/hc-12-433-si4463-wireless-serial-module/?gad_source=1&gclid=Cj0KCQiA3uGqBhDdARIsAFeJ5r3qYy1WscdOc2q7FYOl8ERYIw0gDUuHKtn998-JeqdGaER6zpC9TesaAhDJEALw_wcB |
| Raspberry Pi Pico | ₹350.00 | 2 | ₹700.00| https://robu.in/product/raspberry-pi-pico/?gad_source=1&gclid=Cj0KCQiA3uGqBhDdARIsAFeJ5r3-VE4EZzcFEQSOocyBp4e2ovNoOmH6XuQLWQgfg-l3qTryTRqOnJAaAlVUEALw_wcB |
| PS2 Joystick Module Breakout Sensor | ₹34.00 | 1 | ₹34.00| https://robu.in/product/joystick-module-ps2-breakout-sensor/ |
_________________

# Raspberry Pi Pico Pinout
<img src="https://github.com/Aarushraj-Puduchery/HC-12_WirelessModule_with_PICO/assets/97360295/95a822ca-70a6-4bae-acca-d4913d014764" width="60%" height="60%" />

_________________

# Simple Implementation with PICO
Let's get started with HC-12, we will be using two HC-12 Modules and Two Raspberry Pi PICO for this Tutorial

HC-12 is Connected to Pico using UART Communication Protocol.
PICO has Two UART i.e. UART0 and UART1. HC-12 is connected to either of these two UART PINS.

For more information about how UART works Refer to - https://www.geeksforgeeks.org/universal-asynchronous-receiver-transmitter-uart-protocol/

<img src="https://github.com/Aarushraj-Puduchery/HC-12_WirelessModule_with_PICO/assets/97360295/2e6c225a-12d0-4e47-9444-67eff10edfe2" width="60%" height="60%" />

> [!NOTE]
> Remember the UART Pin you have connected UART0 or UART1, Based on that we need to define the function in the Program.
> Also Make sure that TX and RX must be Connected with RX and TX of PICO(Reverse).

## Circuit Diagram
<img src="https://github.com/Aarushraj-Puduchery/HC-12_WirelessModule_with_PICO/assets/97360295/b9be211f-8e3c-4558-a3db-68e2596a828a" width="100%" height="100%" />

## Coding
### Transmitter



