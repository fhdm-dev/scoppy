---
title: Pico GPIOs
---


| GPIO | Input/Ouput | Summary | Description |
| --- | --- | --- | --- |
| 0 & 1 | Output              | UART TX & RX      | Some diagnostic information is written to the UART including error messages if scoppy enounters an unrecoverable error |
| 2 & 3 | Input - pulled down | CH1 Voltage Range | Currently selected voltage range for channel 1 |
| 4 & 5 | Input - pulled down | CH2 Voltage Range | Currently selected voltage range for channel 2 |
| 6 to 13 | Input | Logic Analyzer inputs | Connect up to 8 digital sources (0V to 3.3V) |
| 22    | Output              | Test signal       | PWM 1kHz 50% duty cycle - can be connected directly to either of the ADC inputs
| 26    | Input               | CH1 ADC input         | Connect the +ve output of your analog frontend (or signal source) here. Connect the ground of the analog frontend (or signal source) to GND.
| 27    | Input               | CH2 ADC input         | Connect the +ve output of your analog frontend (or signal source) here. Connect the ground of the analog frontend (or signal source) to GND.

> Please note that the test signal and voltage range GPIO assignments changed in version 4 of the firmware (previously they were GPIO 16 and 22 for the test signal, 3 and 4 for the channel 1 voltage range and 6 & 7 for the channel 2 voltage range).
