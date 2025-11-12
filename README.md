# Nautilus Mainboard PCB
## Overview
This PCB houses an [STM32H7B0RBT6](https://www.st.com/resource/en/datasheet/stm32h7b0ab.pdf) together with a [CM4](https://pip-assets.raspberrypi.com/categories/634-raspberry-pi-compute-module-4/documents/RP-008168-DS-1-cm4-datasheet.pdf?disposition=inline). The STM32 is primarily used for communication over CanOpen with all the other PCBs while the CM4 is intended to run higher level calculations and then being shut off again. The CM4 is connected to an SSD. The CM4 and STM are connected over Uart (RX, TX) closely for communication and there is an integrated option for the STM to power off and on the CM4. (Currently the CM4's RUN_PG is connected to the STM32's pin number 10.) The STM has a crystal while the CM4 currently does not have one since it was not requested.

Additionally the mainboard provides two IMUs ([BMI088](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bmi088-ds001.pdf)) that can be accessed over I^2C by the STM32. Those components house accelerometers and gyroscopes for orientation and movement detection and listen to the following addresses:
- Accelerometer: 0x18, 0x19
- Gyroscope: 0x68, 0x69

The Power supply is primarily provided by the UUV's battery lines (5V, 3.3V and GND) but the board also accepts USB-C 2.0 for both data and power inputs (only powering the CM4 and nothing else) or the 3.3V Power supply over the STM programmer pins. (only powers the STM32) The power logic is achieved using three [TPS2121RUXT](https://www.ti.com/lit/ds/symlink/tps2120.pdf?ts=1761678178328) (one for 5V, one for 3.3V and one for the GPIO reference of both microcontrollers.)

> [!CAUTION]
> The Power supply logic can be bypassed completely by soldering on 0 Ohm resistors on the designated spots for both 5V and 3.3V, but this still needs to be worked on.

### WIP

Differential pairs have been routed and matched in length but the trace widths still need to be recalculated and adjusted.

The whole board works on 2 layers with an additional ground layer in mind (until now 1 free layer)

If someone wants to write a better README, feel free to do so, I'd appreciate it.

This PCB has not yet been reviewed or tested.