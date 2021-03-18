# Installation

## Installation Instructions
### 1. Install the Android App
NOTE: The Android App will be available soon.
Install the [Scoppy Android app](https://play.google.com/store/apps/details?id=xyz.fhdm.scoppy) from the Play Store. Once installed you can explore some of the capabilities of the app by selecting the demo mode. To do this, tap the 'USB' badge at the bottom left of the screen. Then tap 'Change input'.

### 2. Install the Firmware
Copy the [pico-scoppy-v1.uf2](https://scoppy.fhdm.xyz/downloads/scoppy-pico-v1.uf2) file onto your Pico. The onboard LED should start blinking.

### 3. Connect the Pico to your Phone/Tablet
Attach the small end of the OTG adapter cable to the USB input of the Android device (do NOT plug it into the USB socket of the Pico!). The other end attaches to a regular USB-A to USB-Micro cable which is plugged into the Pico.

Once you open the app and a connection is established between the Pico and the Scoppy app the onboard LED should stop blinking.

Note. If you selected the Demo mode in step 1, you'll need to change the input back to USB.

### 4. Start Scoppying!
Attach one probe (wire) to GPIO26 of the Pico and the other to ground. This will allow you to measure signals between 0V and 3.3V. Of course the signal voltage should be within the allowed range of the ADC pins of the RP2040. See section 5.2.3 of the RP2040 Datasheet for more information.

## Measuring different voltage ranges (optional)
To measure different voltage ranges (eg. -5V to +5V or 0V to 0.1V etc) you will need to add additional circuitry between the probes and the ADC of the Pico to attenuate/amplify the signal and/or provide an appropriate voltage offset (More information and examples will be provided in the near future).

If you decide to add an analog frontend, the Scoppy app needs to be configured so that it will display the correct voltage. You do this by tapping on the Channel badge at the bottom of the screen, tap Settings and then Voltage ranges. Repeat this for each channel. Support for multiple voltage ranges is coming soon.
