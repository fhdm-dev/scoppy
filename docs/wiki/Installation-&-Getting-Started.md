---
title: Installation
---


### 1. Install the Android App
Install the [Scoppy Android app](https://play.google.com/store/apps/details?id=xyz.fhdm.scoppy) from the Play Store.

### 2. Download the Firmware

Different firmware is available for the Pico and Pico W. The Pico firmware is not compatible with the Pico W and vice versa.
Download the firmware by selecting one of the following links.

Pico: [scoppy-pico-v11.uf2](https://fhdm-dev.github.io/downloads/scoppy-pico-v11.uf2)
<br>
Pico W: [scoppy-pico-wireless-v13.uf2](https://fhdm-dev.github.io/downloads/scoppy-pico-wireless-v13.uf2)

If you have an [FHDM FSCOPE](https://store.fhdm.xyz/fscope-500k) board then you will need to use one of these:
<br>
FSCOPE with Pico: [scoppy-pico-fscope-250k5-v11.uf2](https://fhdm-dev.github.io/downloads/scoppy-pico-fscope-250k5-v11.uf2)
<br>
FSCOPE with Pico W: [scoppy-pico-wireless-fscope-250k5-v13.uf2](https://fhdm-dev.github.io/downloads/scoppy-pico-wireless-fscope-250k5-v13.uf2)

If you have an [FHDM DSO-500K](https://store.fhdm.xyz/dso-500k) oscilloscope then you will need to use the
[scoppy-pico-wireless-fscope-250k5-v13.uf2](https://fhdm-dev.github.io/downloads/scoppy-pico-wireless-fscope-250k5-v13.uf2) firmware file.
<br>

### 3. Install the Firmware
Push and hold the BOOTSEL button on the Pico, then connect it to your computer using a micro USB cable. Release BOOTSEL once the drive RPI-RP2 appears on your computer. Copy the uf2 file to your Pico.   

The onboard LED should start blinking.

### 4. Connect the Pico or Pico W to your Phone/Tablet

If you have a Pico W, then please see [Getting started with Scoppy and the Pico W](./Getting-started-with-the-Pico-W). Once connected, continue to Step 2 below.

If you have a Pico, attach the small end of the OTG adapter cable/adapter to the USB input of the Android device (do NOT plug it into the USB socket of the Pico!). Uplug the USB cable from your computer (the one used in step 2) and plug it into the other end of the OTG adapter/cable.

Once you open the app and a connection is established between the Pico and the Scoppy app the onboard LED should stop blinking. You may need to tap the 'Run' button in the app if the scope is currently stopped (Scoppy will either be RUNNING or STOPPED. This status is displayed at the top right of the grid).


### 5. Connect a signal source
Attach the +ve output of your signal source to GPIO26 of the Pico and the ground to gnd. This will allow you to measure signals between 0V and 3.3V. Of course the signal voltage should be within the allowed range of the ADC pins of the RP2040. See section 5.2.3 of the RP2040 Datasheet for more information. For Channel 2, connect the signal to GPIO27. 

> You might want to insert a current limiting resistor (eg 100R) between the signal source and the pico ADC (GPIO26/27) to limit the current through the Pico ESD diodes in case you accidentally apply a voltage higher than 3.3V.

If you don't have a suitable signal source you can view the test signal on GPIO 22 by connecting it directly to the ADC pins (GPIO 26 and 27). GPIO 22 is a 1kHz square wave with a duty cycle of 50%.

To measure signals outside of the 0 to 3.3V range of the Pico ADCs you will need some form of circuitry between your signal source and the Pico ADC. See the [Analog Front-End](../wiki/Analog-Front-End) documentation for more information.

<br>
![](https://github.com/fhdm-dev/scoppy/blob/main/images/phone-scoppy-v2-test-signal-1.jpg?raw=true)
Test signal connected to GPIO 26. Horizontal time/div needs adjusting :)

<br>
### Logic Analyzer Mode
To use Scoppy as a logic analyzer tap the Menu button and then the Mode button and tap 'Logic Analyzer'. The logic analyzer inputs are GPIOs 6 to 13. Please remember to only apply voltages of between 0 and 3.3V to these pins.

<br>
{% include see-also.md %}
