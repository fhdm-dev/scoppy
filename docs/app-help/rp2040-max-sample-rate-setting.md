---
title: RP2040 Maximum Sample Rate Setting
---

> This feature is only available in version 1.030 (or higher) of the Scoppy Android app when version 17 (or higher) of the firmware is installed.  Version 1.030 of the Android app will be available soon. The latest firmware can be found [here](../wiki/firmware-versions).

## About

The RP2040 datasheet states that the clock source for the built-in ADC must be 48MHz and that each ADC conversion takes 96 clock cycles.
This gives a maximum sample rate of 500kS/s (ie. 48000000 % 96 = 500000). This in turn limits the maximum bandwidth achievable by a Scoppy oscilloscope<sup>1</sup>.

However, if we ignore the datasheet and clock the ADC at a higher rate then we can achieve sample rates of up to 2.0MS/s with negligible affects on
performance. The setting described here allows us to do just that.

The Scoppy Android app allows us to choose from 3 different values for the maximum sample rate. They are:
* 500kS/s - The default - the ADC is clocked at 48MHz
* 1.3MS/s - The ADC is clocked at 125MHz
* 2.0MS/s - The ADC is clocked at 192MHz


## How to access and modify the RP2040 Maximum Sample Rate setting

From the _MENU_ tap the _SETTINGS_ button and then tap _RP2040 SETTINGS_ and then _Max. Sample Rate_.

Tap your desired setting and then OK. The new maximum sample rate setting will take effect within a few seconds.

## FAQ
### Does changing the maximum sample rate affect the accuracy of the oscilloscope?
We have found very little difference between the 3 available sample rates. We will be publishing some test results soon. However, performance
may depend on the analog front-end used to drive the ADCs of the RP2040.

### Will the ADC perform as per the RP2040 datasheet specifications at the higher sample rates?
Unlikely. The higher sample rates are outside of the recommended range specified in the RP2040 datasheet and so the specifications stated
in the datasheet will not apply.

### Does this setting affect the Logic Analyzer?
Changing the maximum sample rate to 1.3MS/s will not have any affect when using the Logic Analyzer mode. The 2.0MS/s setting will increase
the maximum Logic Analyzer sample rate from 25MS/s to 38MS/s. 

### Is the setting stored on the RP2040 (flash) or the Android app?
The setting is stored in the Android app and so it will need to be modified on each Android device.

### What is the maximum sample rate when two oscilloscope channels are enabled?
When both channels are enabled the maximum sample rate is halved. The maximum samples rates for the three possible settings are thus
250kS/s, 625kS/s and 1MS/s when using two channels.

## Footnotes
<sup>1</sup>This only applies when the Scoppy firmware is running on an RP2040 and is sampling using the built in ADCs. Future versions of the firmware
may become available that either use an external ADC or target different MCUs.

## See also
{% include scoppy-links.md %}
