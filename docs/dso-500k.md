---
title: DSO-500K operating instructions
---

> The DSO-500K is powered by a Raspberry Pi Pico W. References to Pico or Pico W in this documentation also apply to the DSO-500K

### Connecting to your Phone/Tablet

The DSO-500K can communicate with your Android phone/tablet over Wi-Fi or via USB. We recommended connecting via USB first and then configuring the Wi-Fi connection.

#### USB
Attach the small (male) end of an OTG cable/adapter to the USB input of the Android device (do NOT plug it into the USB socket of the DSO-500K!). 
Plug a standard USB cable (Type-A to Micro-USB) into the other end of the OTG cable/adapter . Attach the other end of the USB cable to the micro-USB connector on the DSO-500K board.

_Please note that if a connection over USB hasn’t been established within 10 seconds the DSO-500K will start listening to connections over Wi-Fi (the Wi-Fi LED will blink). To try connecting via USB again the DSO-500K will need to be restarted (by disconnecting then reconnecting the USB cable)._

#### Wi-Fi
Please see [Getting started with Scoppy and the Pico W](./wiki/Getting-started-with-the-Pico-W) for instructions on how to establish a wireless connection between the DSO-500K and the Scoppy app on your phone/tablet.

#### RUN

Once you open the app and a connection is established between the DSO-500K and the Scoppy app the onboard LED should stop blinking. You may need to tap the 'Run' button in the app if the scope is currently stopped (Scoppy will either be RUNNING or STOPPED. This status is displayed at the top right of the grid).

### Connecting the signal source

The signal source can be connected to either the header pins labeled CH1 and CH2 or a BNC connector (if fitted).

> Note that all GND pins/connections are connected together internally. If using two channels, the (probe) GND wires for each channel must be at the same potential (because they are effectively shorted together). 

> For each channel the center of the BNC connector and the corresponding header pin input are also connected internally. It it recommended you use either the BNC connector or the header pin input but NOT both at the same time.

### Input voltage ranges

The DSO-500K will automatically change the input voltage range (sensitivity) as you adjust the volts/div setting in the app. The best vertical resolution is
obtained by adjusting volts/div so that the trace fills most of the screen vertically (assuming the vertical position is 0). Further increases in volts/div
may result in the signal being clipped.
    
When the voltage range changes you'll probably see the trace momentarily 'jump'. This is expected.   
   
The currently selected voltage range can be seen on the channel badge at the bottom of the app screen (a number between 0 and 3). To manually select a voltage range, tap the channel badge and then tap 'Select input voltage range'.   
   
### Signal generator

The output from the Scoppy signal generator is accessed via the two SIG pins at H12 on the board.
   
The upper pin (LP) is used when you want the signal to be fed through the low-pass RC filter (eg. when 'Sine Wave (PWM)' is selected as the signal type in the Scoppy app). When using the SIG LP pin, the two pins of H4 need to be connected with a jumper.

The lower SIG pin (DIRECT) is used for direct access to the signal generator output. Note: If the 2 pins of H4 are connected this will affect the output of the signal generator and so the jumper on these pins should be removed when using the SIG DIRECT pin.

> Please note there is a bug that will sometimes cause the firmware to hang when the signal generator output is changed from a Sine (PWM) wave to square wave. If this happens simply cycle the power to the DSO-500K.

### AC/DC Coupling

The pins marked DC are used to select AC or DC coupling. Connect the pins with a jumper for DC coupling. Leave the pins unconnected for AC coupling.

### 10X Probes

The board is compatible with 10X probes. The probe attenuation can be set in the app by tapping the channel badge at the bottom of the screen
and then tapping 'Settings' and 'Probe'.
   
The frequency compensation of 10X probes will need to be adjusted to match in the input capacitance of the oscilloscope.

### Board Dimensions
See [here](wiki/fscope-dso-500k-dimensions)

### Unpopulated holes/pads

> For board revision 4b and lower see [here](https://oscilloscope.fhdm.xyz/wiki/fscope-dso-500k-v2-usage)

There will be some unpopulated holes/pads on your board. Depending on your board revision these may include:

_+3.3V, VSYS_
<br>
Test points

_-2.5V_
<br>
Test point for the -2.5V rail. Do not draw current from this rail as it will adversely affect the performance
of the oscilloscope.

_H17_
<br>
Restart/Reset. Shorting these will restart the DSO-500K. A momentary switch could be soldered to these holes/pads to make it easier to restart the oscilloscope. Double clicking the switch will cause the Pico W on the DSO-500K to enter USB mass storage mode.

_H7, H15_ 
<br>
For connecting external Wi-Fi and Trigger LEDS if the board is to be enclosed in a case.

_H9, R32_ 
<br>
For connecting an external status LED if the board is to be enclosed in a case (no firmware support for this as yet).

### Updating the Firmware

Instructions are on the [Installation & Getting Started](./wiki/Installation-&-Getting-Started) page.

The firmware file is named scoppy-pico-wireless-fscope-250k5-vNN.uf2 (where NN is the version number).

### Trimmer capacitor adjustment

The green trimmer capacitors on the board were adjusted before the board was shipped but if you find your square waves are not looking very square then adjusting them
might help. 

> Note. If a jumper is connecting the pins on H4 then the this will affect the output of the signal generator. Remove the jumper before performing the trimmer capacitor adjustment.

Instructions for adjusting the trimmer capacitors can be found in the [FSCOPE assembly instructions](wiki/fscope-500k).

## See also
{% include wifi-links.md %}
<br>
{% include scoppy-links.md %}
