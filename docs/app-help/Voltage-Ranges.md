---
title: Voltage Ranges
---

## What are voltage ranges?

A voltage range refers to the minimum and maximum voltages that can be applied to the oscilloscope without the signal being clipped.
Scoppy supports up to 4 voltage ranges.

See [Analog Front-End](../wiki/Analog-Front-End) for more information.

## Voltage range settings

### 'Do not overwrite when device is connected' checkbox
When the app connects to a Scoppy device (eg. a Pico or Pico W), the device firmware will upload its
voltage range settings (if any) to the app. This will overwrite the voltage range settings stored in the app and will result in
any changes you have made to the voltage range settings in the app being lost.

Selecting the 'Do not overwrite when device is connected' checkbox will prevent the voltage range settings in the app being overwritten by
the voltage range settings of the device firmware.  
   
Please note that not all scoppy firmware contains voltage range settings (eg. the default scoppy-pico firmware). Any firmware built for
a specific analog front-end will contain voltage range settings (eg. firmware for FScope boards). 

## See also
{% include scoppy-links.md %}
