# SatNOGS Rotator Firmware for Arduino UNO/CNC Shield, for DIRECT CONNECTION TO PC via serial

Firmware [SatNOGS Rotator Controller Based on Arduino UNO and CNC V3 Shield](https://wiki.satnogs.org/SatNOGS_Arduino_Uno/CNC_Shield_Based_Rotator_Controller).

Repository includes all source files for the SatNOGS rotator controller Firmware, based on the Arduino UNO using the CNC v3 Shield, instead of the custom SatNOGS PCB.

Electronics can be found on [satnogs-rotator-controller](https://wiki.satnogs.org/SatNOGS_Arduino_Uno/CNC_Shield_Based_Rotator_Controller)

This repository is a fork of [https://gitlab.com/Quartapound/satnogs-rotator-firmware](https://gitlab.com/Quartapound/satnogs-rotator-firmware)

## Building instructions
In order to use this code, you need to
 * Install Arduino IDE
 * In the IDE, open stepper_motor_controller.ino
 * Make sure that the sketchbook location under `Settings...` points to the repository root.
 * Under `Sketch/Include library/Manage libraries` install `AccelStepper 1.64`
 * Connect the board via USB, make sure it's detected by the IDE. 
 * `Sketch/Upload` or press the -> button in the toolbar.

## Hamlib configurtation
Hamlib will bridge between the Arduino board that implements the `Easycomm` interface and Gpredict. From Gpredict's point hamlib will act as an 'antenna rotator'.

```
> brew install hamlib
...
> rotctld -m 202 -r /dev/cu.usbmodem101  -s 9600 -T 127.0.0.1 -t 4533 -C timeout=500 -C retry=0 -vvvvvvvv
...
```

I got `/dev/cu.usbmodem101` from the Arduino IDE's `Tools` menu under `Port`, it's also in a dropdown in the toolbar.


## Configure the rotator in Gpredict
Under `Preferences / Interfaces` click [Add New]

```
Name: my-rotator
Host: localhost
Port: 4533
```

## License

[![Libre Space Foundation](https://img.shields.io/badge/%C2%A9%202014--2018-Libre%20Space%20Foundation-6672D8.svg)](https://librespacefoundation.org/)

Licensed under the [GPLv3](LICENSE)
