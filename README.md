# Scoppy
Scoppy is a simple oscilloscope that consists of an Android App for your phone or tablet - and firmware for your Raspberry Pi Pico. No programming is required.

Signals are measured by the Pico and the waveform is displayed on the Android device.

## What you'll need
* An Android device that's running Android version 23 (Marshmallow) or higher. The device must also support USB OTG (On-The-Go) - most modern phones/tablets do
* A USB OTG adapter/cable. The small end should match the USB input on your Android device - most likely USB-Micro or USB-C.
* A Rasperry Pi Pico board
* Two jumper wires to act as probes

## What does it cost?
If you have the items listed above then nothing. If you don't want to see Ads in the app or you want to use 2 channels then you can pay a few dollars to upgrade to the premium version of the app.

USB OTG adapter cables can be bought for a few dollars.

## Quick Start
### 1. Install the Scoppy Android App
NOTE: The Android App will be available soon.
Install the [Scoppy Android app](https://play.google.com/store/apps/details?id=xyz.fhdm.scoppy) from the Play Store.

### 2. Install the firmware onto your Pico
Copy the [pico-scoppy-v1.uf2](https://scoppy.fhdm.xyz/downloads/scoppy-pico-v1.uf2) file onto your Pico. The onboard LED should start blinking.

### 3. Connect the Pico to your Phone/Tablet
Attach the OTG adapter/cable to the USB input of the Android device. The other end attaches to the USB cable you have connected to your Pico.

### 4. Start Scoppying!
Attach one probe (wire) to GPIO26 of the Pico and the other to ground. This will allow you to measure signals between 0V and 3.3V. Of course the signal voltage should be within the allowed range of the ADC pins of the RP2040. See section 5.2.3 of the RP2040 Datasheet for more information.

See [here](Install.md) for more detailed installation instructions.

## Measuring different voltage ranges
See [here](Install.md).
