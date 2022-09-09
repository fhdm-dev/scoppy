---
title: Pico GPIOs
---

GPIOs used by the Scoppy firmware.
<br><br>

<!--
The Pico and Pico W Scoppy firmware is available in two different GPIO configurations. Choose whichever suits you best. If in doubt just use Default.
The firmware for the each configuration is available [here](../wiki/Installation-&-Getting-Started).

## Default
-->

| GPIO | Input/Ouput | Summary | Description |
| --- | --- | --- | --- |
| 0 & 1 | Output              | UART TX & RX      | Some diagnostic information is written to the UART including error messages if scoppy enounters an unrecoverable error |
| 2 & 3 | Input - pulled down | CH1 Voltage Range | Currently selected voltage range for channel 1 |
| 4 & 5 | Input - pulled down | CH2 Voltage Range | Currently selected voltage range for channel 2 |
| 6 to 13 | Input | Logic Analyzer inputs | Connect up to 8 digital sources (0V to 3.3V) |
| 14    | Output              | Wi-Fi Status | Connect to an LED to see if your Pico W is using wireless to connect to the Scoppy app | 
| 15    | Output              | Trigger | Connect to an LED to see when a trigger is fired | 
| 22    | Output              | Test signal       | PWM 1kHz 50% duty cycle - can be connected directly to either of the ADC inputs
| 26    | Input               | CH1 ADC input         | Connect the +ve output of your analog frontend (or signal source) here. Connect the ground of the analog frontend (or signal source) to GND.
| 27    | Input               | CH2 ADC input         | Connect the +ve output of your analog frontend (or signal source) here. Connect the ground of the analog frontend (or signal source) to GND.

<!--
## FScope

This firmware is configured to work with the [FScope](https://store.fhdm.xyz) range of boards. Feel free to use this if the pinout suits you better than the default.

| GPIO | Input/Ouput | Summary | Description |
| --- | --- | --- | --- |
| 0 & 1 | Output              | UART TX & RX      | Some diagnostic information is written to the UART including error messages if scoppy enounters an unrecoverable error |
| 6 to 13 | Input | Logic Analyzer inputs | Connect up to 8 digital sources (0V to 3.3V) |
| 14    | Output              | Wi-Fi Status | Connect to an LED to see if your Pico W is using wireless to connect to the Scoppy app | 
| 15    | Output              | Trigger | Connect to an LED to see when a trigger is fired | 
| 16    | Output              | Test signal       | PWM 1kHz 50% duty cycle - can be connected directly to either of the ADC inputs
| 18 & 19 | Input - pulled down | CH1 Voltage Range | Currently selected voltage range for channel 1 |
| 20 & 21 | Input - pulled down | CH2 Voltage Range | Currently selected voltage range for channel 2 |
| 26    | Input               | CH1 ADC input         | Connect the +ve output of your analog frontend (or signal source) here. Connect the ground of the analog frontend (or signal source) to GND.
| 28    | Input               | CH2 ADC input         | Connect the +ve output of your analog frontend (or signal source) here. Connect the ground of the analog frontend (or signal source) to GND.
-->

<br>
{% include see-also.md %}
