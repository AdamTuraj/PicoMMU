# PicoMMU

PicoMMU is a PCB designed to control a stepper motor and servo for a multi-material unit. It is compatible with Klipper firmware.
![A 3D render of the PCB]()

## Requirements

- A USB C cable to connect to your RPI / Printer
- A 12-24V power supply
- A TMC2209 (BTT Recommended)
- A stepper motor crimped with a 4 pin JST XH B4

## Flashing Klipper

- Follow [this Klipper guide](https://www.klipper3d.org/Installation.html) on how to build the firmware. The configuration can be found below. Flashing will work a little different as there is no bootloader currently on the chip.
  ![The configuration for Klipper. Select STMF042 as the chip, change "Bootloader Offset" to "No Bootloader" and under extra low-level configuration options change "Clock Reference" to "Internal Clock"]()
- Once the firmware is build, put the chip into DFU mode by clicking the reset button while holding the boot button.
- Run lsusb and take not of the numbers in this format: xxxx:xxxx.
- Now use the following command to flash the firmware (replacing xxxx:xxxx with your MCU's ID): `make flash FLASH_DEVICE=xxxx:xxxx`.
- Unplug and replug in the USB cord and your MCU should pop up in `ls /dev/serial/by-id/*`.

## License

This project is licensed under the MIT License.
