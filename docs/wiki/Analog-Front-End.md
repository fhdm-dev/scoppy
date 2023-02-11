---
title: Analog Front-End
---

## Examples
[Some analog front end designs](./Analog-Front-End-Examples)

## Voltage Ranges

### What are voltage ranges?

A voltage range refers to the minimum and maximum voltages that can be applied to the input of the oscilloscope without the signal being clipped.
It can also be thought of as a sensitivity level.

Multiple voltage ranges are used to maximimize the vertical resolution of the oscilloscope.
Scoppy supports up to 8 voltage ranges and they are numbered 0 to 7. A single range is selected at any one time. This will normally be
the smallest range that will accomodate the signal being measured.

For example, if we have an analog front end with voltage ranges of 0-10V, 0-5V and 0-2V then when measuring a signal with a maximum amplitude of
1.5V we would select the 0-2V range. If measuring a signal with a maximum amplitude of 3.5V we would use the 0-5V range and when measuring
a signal with a maximum amplitude of 7V we would use the 0-10V range.

### Voltage ranges and the oscilloscope analog front end
To measure different voltage ranges (eg. -5V to +5V or 0V to 0.1V etc) than the default (0-3.3V) you will need to add additional circuitry in front of the Pico to attenuate/amplify the signal and/or provide an appropriate voltage offset so that the voltage at the ADC pins of the Pico is between 0 and ADC_VREF (by default ADC_VREF is 3.3V).

You will need to design your analog front-end so that it either:
* allows selection of the voltage range by the user (eg. using a mechanical switch). The front end will also need to set the appropriate values at the voltage range pins of the Pico so that the firmware and app know which voltage range is currently selected
* OR
* reads the values of the voltage range pins and sets the range of the front-end accordingly (eg. via an analog switch such as a CD4052)

If using the latter method, you will need to configure the _Auto Voltage Range Pins_ setting to the appropriate value (see below).

You can also specify a Vref value for each range. This will result in a (PWM) voltage being generated at the configured GPIO.
The Vref GPIOs are configured via the [Firmware GPIO Settings](../app-help/firmware-gpio-settings). The Vref can be used to provide an
appropriate offset voltage used to ensure that the voltage at the Pico ADC is between 0 and 3.3V. Of course you will need to provide
circuity to convert the PWM 'voltage' to DC (eg. a low pass filter).

### Voltage Range Configuration

#### Firmware

To store the voltage range configuration on the firmware, tap the connection badge at the bottom-left of the screen, then tap _Connected device_, _Firmware settings_, _Channels_ and then the channel you wish to configure.You can enter up to 8 voltage ranges per channel. If using more than 4 voltage ranges you will need to enable the extra voltage range pin in the 
[Firmware GPIO Settings](../app-help/firmware-gpio-settings).

For each range the following values can be configured:
<br>
<br>
__Min. Voltage__
<br>
The input voltage that will result in 0V being present at the ADC.

__Max. Voltage__
<br>
The input voltage that will result in ADC_VREF (3.3V by default) being present at the ADC.

__Vref - 1X (V)__
<br>
The Vref to be generated when the probe setting is set to 1X. This can be left blank.

__Vref - 10X (V)__
<br>
The Vref to be generated when the probe setting is set to 10X. This can be left blank.

When more than one voltage range has been configured, the currently selected voltage range will be displayed in the channel badge in the app. 

#### App

The voltage range settings can also be stored in the app rather then the firmware. To do this, tap the Channel badge, then _Settings_ and then _Voltage Ranges_. 

When the app connects to a Scoppy device (eg. a Pico or Pico W), the device firmware will upload its
voltage range settings (if any) to the app. This will overwrite the voltage range settings stored in the app and will result in
any changes you have made to the voltage range settings in the app being lost.

Selecting the 'Do not overwrite when device is connected' checkbox will prevent the voltage range settings in the app being overwritten by
the voltage range settings of the device firmware.  
   
Please note that not all Scoppy firmware contains voltage range settings (eg. the default scoppy-pico firmware). Any firmware built for
a specific analog front-end will most probably contain voltage range settings eg. firmware for [FSCOPE-500K](https://store.fhdm.xyz/fscope-500k) boards and the [DSO-500K](https://store.fhdm.xyz/dso-500k) oscilloscope.

### Voltage range GPIOs

You can configure up to 3 voltage range GPIOs per channel (for a maximum of 8 ranges). The voltage range GPIOs are used to either indicate to the firmware/app
which range has been selected (eg. if the range is selected by a mechanical switch) or for the firmware/app to control which range is
selected (eg. via a switch such as a CD4052). 

In the former case, the GPIOs are configured by the firmware as inputs. In the latter they are configured as outputs.

Each voltage range GPIO corresponds to a bit in the voltage range ID (which is a value between 0 and 7). The voltage range GPIOs
are configured via [Firmware GPIO Settings](../app-help/firmware-gpio-settings). These voltage range GPIOs are unsurprisingly named _Voltage range bit_ 0, 1 and 2.

The table below shows the default voltage range GPIO configuration and the voltage range ID that corresponds to the different logical
level combinations at the pins.

Note:
* bit 2 is disabled by default.
* each voltage range GPIO configured as an input is pulled low. If you connect nothing to these pins then range 0 is selected.


| GPIO 2 (CH1 bit 1)| GPIO 3 (CH1 bit 0)| CH 1 Voltage Range ID|
| --- | --- | --- |
| LOW | LOW | 0 |
| LOW | HIGH | 1 |
| HIGH | LOW | 2 |
| HIGH | HIGH | 3 |

| GPIO 4 (CH2 bit 1) | GPIO 5 (CH2 bit 0) | Ch 2 Voltage Range |
| --- | --- | --- |
| LOW | LOW | 0 |
| LOW | HIGH | 1 |
| HIGH | LOW | 2 |
| HIGH | HIGH | 3 |

### Auto Voltage Range Pins

This setting controls how many GPIOs are used as outputs. If used as an output the app/firmware controls the logic level at these pins and
the front-end hardware should select the correct range (eg. via an analog switch/mux such as a CD4052). If set to 1 then the Bit 0 voltage range GPIO will be an output. If 2 then Bit 0 and Bit 1 GPIOs will be outputs. If 3 then all 3 voltage range GPIOs will be outputs.

We call this 'Auto voltage range' because the voltage range will change automatically as the user changes the Volts/div in the app. If using 
the Auto voltage range feature, the app will allow the current range to be selected manually by tapping the channel badge and then tapping
_Select voltage range_.

If using the auto voltage range feature then the largest ranges should appear first in the configuration. eg. if you have ranges of 0-10V and 0-2V then the 0-10V range should be assigned to range ID 0 and the 0-2V range should be assigned to range ID 1.

#### Mixed auto and manual voltage range selection

An _Auto voltage range pins_ setting of 1 or 2 allows some of the voltage range GPIOs to be controlled by the firmware/app (outputs) and some to be 
controlled by the front end hardware (inputs). This can be used to design a front end for example that has a mechanical switch on the input to
select different attenuation levels - and an analog switch/mux that automatically changes the range within that attenuation level in response to the
Volts/Div setting changing within the app.

### Inverting Analog Front Ends

Scoppy supports inverting analog front ends ie. front ends that will result in 3.3V at the ADC at the minimum input voltage and 0V at the ADC
at the maximum input voltage. Simply select the _Inverting_ checkbox to enable this.


<br>
{% include see-also.md %}
