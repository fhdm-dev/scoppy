---
title: Analog Front-End
---

### Examples
[Some analog front end designs](./Analog-Front-End-Examples)

### Measuring different voltage ranges
To measure different voltage ranges (eg. -5V to +5V or 0V to 0.1V etc) than the default (0-3.3V) you will need to add additional circuitry in front of the Pico to attenuate/amplify the signal and/or provide an appropriate voltage offset so that the voltage at the ADC pins of the Pico is between 0 and VREF (by default VREF is 3.3V).

If you decide to add an analog front-end, the Scoppy app needs to be configured so that it will display the correct voltage. You do this by tapping on the Channel badge at the bottom of the screen, tap Settings and then Voltage ranges. You can enter up to 4 voltage ranges per channel.

### Voltage range selection
If more than one voltage range is required then you will need to design your analog front-end so that it either:
* applies voltages to the voltage range pins to indicate to the firmware (and app) which voltage range is selected (eg. via a mechanical switch)
* OR
* reads the values of the voltage range pins and sets the range of the front-end accordingly (eg. via an analog switch such as a CD4052)

If using the latter method, you will need to compile the firmware with AUTO_VOLTAGE_RANGE defined.

### Voltage range GPIOs

Your front-end indicates the currently selected voltage range via GPIOs 2 & 3 for Channel 1 and GPIOs 4 & 5 for Channel 2. The logic levels at these pins and the corresponding voltage range id is shown in the tables below. By default these pins are pulled down to LOW so if you do nothing then voltage range 0 is selected.

| GPIO 2 | GPIO 3 | Ch 1 Voltage Range |
| --- | --- | --- |
| LOW | LOW | 0 |
| LOW | HIGH | 1 |
| HIGH | LOW | 2 |
| HIGH | HIGH | 3 |

| GPIO 4 | GPIO 5 | Ch 2 Voltage Range |
| --- | --- | --- |
| LOW | LOW | 0 |
| LOW | HIGH | 1 |
| HIGH | LOW | 2 |
| HIGH | HIGH | 3 |

If using the AUTO_VOLTAGE_RANGE method then the above pins are configured as outputs. The logic levels at these pins will change to indicate the 
voltage range selected by the app (this happens automatically when the Volts/Div changes in the app).

<br>
{% include see-also.md %}
