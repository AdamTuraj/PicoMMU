# PicoMMU

PicoMMU is a PCB designed to control a stepper motor and servo for a multi-material unit. It is compatible with Klipper firmware.
![A 3D render of the PCB](https://raw.githubusercontent.com/AdamTuraj/PicoMMU/refs/heads/main/images/3DView.png)

## Requirements

- A USB C cable to connect to your RPI / Printer
- A 12-24V power supply
- A TMC2209 (BTT Recommended)
- A stepper motor crimped with a 4 pin JST XH B4

## Flashing Klipper

1. Follow [this Klipper guide](https://www.klipper3d.org/Installation.html) on how to build the firmware. The first image shows the configuration settings and the second shows the "Optional Features" section.
  ![The configuration for Klipper. Select STMF042 as the chip, change "Bootloader Offset" to "No Bootloader" and under extra low-level configuration options change "Clock Reference" to "Internal Clock".](https://raw.githubusercontent.com/AdamTuraj/PicoMMU/refs/heads/main/images/klipper_config.png)
  ![The optional features section, should be all off as there is not enough flash memory to support all features.](https://raw.githubusercontent.com/AdamTuraj/PicoMMU/refs/heads/main/images/klipper_config_extra_features.png)
2. Once the firmware is build, put the chip into DFU mode by clicking the reset button while holding the boot button.
3. Run lsusb and take not of the numbers in this format: xxxx:xxxx.
4. Now use the following command to flash the firmware (replacing xxxx:xxxx with your MCU's ID): `make flash FLASH_DEVICE=xxxx:xxxx`.
5. Unplug and replug in the USB cord and your MCU should pop up in `ls /dev/serial/by-id/*`.

## License

This project is licensed under the MIT License.
