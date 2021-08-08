> If you are actually looking for the Scopy Oscilloscope by Analog Devices you can find it [here](https://wiki.analog.com/university/tools/m2k/scopy/oscilloscope).

# Scoppy
Scoppy is an oscilloscope and logic analyzer that consists of an Android App for your phone/tablet and firmware for your Raspberry Pi Pico. Signals are measured by the Pico and the waveforms are displayed on the Android device. No programming is required and both the app and firmware are free to download.

The aim of the Scoppy project is to give electronics novices and hobbyists access to an ultra cheap oscilloscope that is useful for viewing low voltage, low frequency signals. Scoppy is also a logic analyzer with a sample rate of 20MS/s.

See the [Wiki](https://github.com/fhdm-dev/scoppy/wiki) for documentation and [Discussions](https://github.com/fhdm-dev/scoppy/discussions) for ... well ... discussing Scoppy.

## What you'll need
* An Android device that's running Android version 6.0 (Marshmallow) or higher. The device must also support USB OTG (On-The-Go) - most modern phones/tablets do (if you don't see the app when browsing the Play Store then your device probably doesn't support this feature)
* A USB OTG adapter/cable compatible with your phone/tablet
* A Rasperry Pi Pico board

> Important

> Please use the latest versions of the App (v1.012) and Firmware (v5). Older versions of the firmware may not work with the latest version of the app and vice versa


## Quick Start

### 1. Install the Scoppy Android App
Install the [Scoppy Android app](https://play.google.com/store/apps/details?id=xyz.fhdm.scoppy) from the Play Store.

### 2. Install the firmware onto your Pico

> Please note that some pin assignments changed in version 4 of the firmware. The test signal is now on GPIO22 and the voltage range pins are now GPIO2 to GPIO5

Download the firmware onto your computer. It is here: [pico-scoppy-v5.uf2](https://scoppy.fhdm.xyz/downloads/scoppy-pico-v5.uf2).
Press the bootsel button on your Pico and connect it to your computer. Copy the pico-scoppy-v5.uf2 file onto your Pico. The onboard LED should start blinking.

### 3. Connect the Pico to your Phone/Tablet
Attach the OTG adapter/cable to the USB input of the Android device. The other end attaches to the USB cable you have connected to your Pico.

### 4. Start Scoppying!
Attach the +ve output of your signal source to GPIO26 of the Pico and the ground to gnd. This will allow you to measure signals between 0V and 3.3V. Of course the signal voltage should be within the allowed range of the ADC pins of the RP2040. See section 5.2.3 of the RP2040 Datasheet for more information. For Channel 2, connect the signal to GPIO27. You might want to insert a current limiting resistor (eg 100R) between the signal source and the pico ADC, just to be safe.

If you don't have a suitable signal source you can view the test signal on GPIO 22 (on older versions of the firware the test signal was on GPIO 16 and 18) by connecting it directly to the ADC pins (GPIO 26 and 27). GPIO 22 is a 1kHz square wave with a duty cycle of 50%.

## Logic Analyzer
To use Scoppy as a logic analyzer tap the Menu button and then the Mode button and tap 'Logic Analyzer'. The logic analyzer inputs are GPIOs 6 to 13. Please remember to only apply voltages of between 0 and 3.3V to these pins.

## Detailed installation instructions
See the [Wiki](https://github.com/fhdm-dev/scoppy/wiki) for more detailed installation instructions.

## Measuring different voltage ranges (oscilloscope mode)
To remove the 0-3.3V input voltage limitation (and do whatever signal conditioning magic takes your fancy) you’ll need to add an [analog front end](https://github.com/fhdm-dev/scoppy/wiki/Analog-Front-End). This can be as simple as a voltage divider or as complex as you want it to be. The [Wiki](https://github.com/fhdm-dev/scoppy/wiki) contains some [examples](https://github.com/fhdm-dev/scoppy/wiki/Analog-Front-End-Examples) of simple (naive?) AFE designs and you are encouraged to share your own front end designs and ideas with other Scoppiers. Just head to the [forum](https://github.com/fhdm-dev/scoppy/discussions).

## Tips
* If the traces or grid lines look too narrow then you can change the width in Settings (tap Menu to see the Settings option)
* Long-pressing most of the control buttons will set the corresponding setting to a default value eg. long-pressing the horizontal position button will reset the horizontal position back to zero. Long-pressing the trigger level button will set the trigger level to the centre of the waveform.
* Long-pressing any of the +/- buttons will continuously change the corresponding value. The longer you press it the faster the value will change.
* Tapping/dragging anything on the grid won't work! That functionality is yet to be implemented. For now you need to use the control buttons.


## Quirks
* If the screen turns off or the app is no longer in the foreground the run mode will change to STOPPED (to prevent draining the battery). You will need to tap RUN to restart the scope.
* The OFF trigger mode prevents all triggering and Scoppy will set the horizonal position so that it is displaying the most recent samples (it normally tries to find a trigger point near the centre of the sample record). This may or may not be useful for viewing very slowly changing signals.

## Troubleshooting
* If the Pico doesn't seem to be connecting try the following:
    * tap STOP and then RUN
    * OR
    * unplug the USB cable and plug it back in
* If your phone has a Micro-USB connecter then check that the Micro-USB plug of the OTG cable/adapter is plugged into the phone and not into the Pico.
* If it's still not working then it's possible that your phone/tablet doesn't support USB OTG. You can test this by attaching a USB thumb drive to the OTG cable/adapter. You should be able to browse the files on the drive.

## Missing Functionality
I'll look at adding the following if there is enough interest in the app:

* Better touch interface eg. dragging the trigger indicator to change trigger level and swiping to change horizontal position.
* More trigger settings eg. falling edge
* Cursors

## Specifications (oscilloscope)
* Max. Sampling Rate: 500kS/s (shared between channels)
* Time/Div: 5us - 20secs
* Memory depth depends on sampling rate. It ranges between 2kpts (shared between channels) and 20kpts in Run mode and up to 100kpts for Single shot captures.

## Specifications (logic analyzer)
* Max. Sampling Rate: 21MS/s (per channel)
* Time/Div: 50ns - 100ms

## Known Bugs
* When long-pressing the + or - buttons, moving your finger laterally will have the same effect as lifting your finger off the button. The only workaround is to keep your finger stready when long-pressing these buttons.

## Advertising and in-app purchase
The free version of the app is limited to one channel in oscilloscope mode and two channels in logic analyser mode. A single banner ad may be displayed at the top of the screen (but no popups I promise!). To enable the extra channel(s) and remove all advertising, a small in-app purchase is required (approx. US$1 for a yearly subscription or US$2 for a lifetime purchase - exact price depends on your location). The one-channel version of the app is completely free (two channels in oscilloscope mode) and all functionality is available without restriction.

## Gallery
![Scoppy App](images/scoppy-v2-single-capture.jpg)
Part way through a single capture. 

![Scoppy Development](images/development1.jpg)
Scoppy under development. From left to right: Arduino Uno, [AD9833 waveform generator](https://www.instructables.com/Simple-AD9833-Based-Signal-Generator/) and associated paraphenalia, Pico acting as debugger, Pico running an early version of the scoppy-pico firmware, the Scoppy app on a Nokia 2.1


[More photos are here...](https://github.com/fhdm-dev/scoppy/wiki/Gallery)

