---
title: Installation
---


### 1. Install the Android App
Install the [Scoppy Android app](https://play.google.com/store/apps/details?id=xyz.fhdm.scoppy) from the Play Store.

### 2. Install the Firmware
Push and hold the BOOTSEL button on the Pico, then connect it to your computer using a micro USB cable. Release BOOTSEL once the drive RPI-RP2 appears on your computer. Download and copy the [pico-scoppy-v7.uf2](https://fhdm-dev.github.io/downloads/scoppy-pico-v7.uf2) file onto your Pico

The onboard LED should start blinking.

## Connections
### 1. Connect the Pico to your Phone/Tablet
Attach the small end of the OTG adapter cable/adapter to the USB input of the Android device (do NOT plug it into the USB socket of the Pico!). Uplug the USB cable from your computer (the one used in step 2) and plug it into the other end of the OTG adapter/cable.

Once you open the app and a connection is established between the Pico and the Scoppy app the onboard LED should stop blinking. You may need to tap the 'Run' button in the app if the scope is currently stopped (Scoppy will either be RUNNING or STOPPED. This status is displayed at the top right of the grid).

### 2. Connect the test signal
A 1kHz test signal is generated on GPIO 22 (on older versions of the firmware the test signal was on GPIO 16). The inputs for Channel 1 & 2 are GPIOs 26 and 27 respectively. So to view the test signal on Channel 1 of the scope connect GPIO 22 directly to GPIO 26. Hopefully you'll now see some sort of waveform in the app. The horizontal scale will probably be wrong so adjust this using the 'Horizontal' + and - buttons. See [Using the App](./Using-the-App) for more details.


![](https://github.com/fhdm-dev/scoppy/blob/main/images/phone-scoppy-v2-test-signal-1.jpg?raw=true)
Test signal connected to GPIO 26. Horizontal time/div needs adjusting.





### 3. Connect a real signal source
#### Oscilloscope mode
You are now ready to measure signals between 0V and 3.3V from a real signal source. Of course the signal voltage should be within the allowed range of the ADC pins of the RP2040. See section 5.2.3 of the RP2040 Datasheet for more information.

If the test signal from step 2 (above) is still connected to GPIO 26 or 27 then disconnect it. Attach the positive terminal of your signal source to GPIO 26 and the other to ground. To display a signal on Channel 2 use GPIO 27.

#### Logic analyzer mode
To use Scoppy as a logic analyzer tap the Menu button and then the Mode button. Select Logic Analyzer. The logic analyzer inputs are GPIOs 6 to 13 (0V to 3.3V).

## Using the app
See [Using the App](./Using-the-App)


