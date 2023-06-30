---
title: Using the FSCOPE-500K and DSO-500K
---

> Note. The FSCOPE-500K was previously known as the FSCOPE-250K. Both boards are exactly the same.

The [_FSCOPE-500K_](https://store.fhdm.xyz/fscope-500k) is a 2 channel oscilloscope analog front end for use with the Raspberry Pi Pico or Pico W and the Scoppy Android app.
Assembly instructions are [here](fscope-500k).
   
The [_DSO-500K_](https://store.fhdm.xyz/dso-500k) is a fully assembled version of the FSCOPE-500K using a Pico W. 

### Using the FSCOPE-500K and DSO-500K

#### Connecting to your Phone/Tablet

If you have a DSO-500K or an FSCOPE-500K with a Pico W, then please see [Getting started with Scoppy and the Pico W](./Getting-started-with-the-Pico-W) for instructions on how to establish a wireless connection between the board and the Scoppy app on your phone/tablet.

Otherwise, attach the small end of an OTG adapter cable/adapter to the USB input of the Android device (do NOT plug it into the USB socket of the FSCOPE/DSO board) and plug the other end of the adapter into a USB cable. This cable then plugs into the micro-USB connector on the FSCOPE/DSO board.

Once you open the app and a connection is established between the Pico and the Scoppy app the onboard LED should stop blinking. You may need to tap the 'Run' button in the app if the scope is currently stopped (Scoppy will either be RUNNING or STOPPED. This status is displayed at the top right of the grid).

#### Connecting the signal source

The signal source can be connected to either the header pins labeled CH1 and CH2 or a BNC connector (if fitted).

> Note that all GND pins/connections are connected together internally. If using two channels, the (probe) GND wires for each channel must be at the same potential (because they are effectively shorted together). 

> For each channel the center of the BNC connector and the corresponding header pin input are also connected internally. It it recommended you use either the BNC connector or the header pin input but NOT both at the same time.

#### Input voltage ranges

The FSCOPE-500K and DSO-500K will automatically change the input voltage range (sensitivity) as you adjust the volts/div setting in the app. The best vertical resolution is
obtained by adjusting volts/div so that the trace fills most of the screen vertically (assuming the vertical position is 0). Further increases in volts/div
may result in the signal being clipped.
    
When the voltage range changes you'll probably see the trace momentarily 'jump'. This is expected.   
   
The currently selected voltage range can be seen on the channel badge at the bottom of the app screen (a number between 0 and 3). To manually select a voltage range, tap the channel badge and then tap 'Select input voltage range'.   
   
The actual values of the voltage ranges are uploaded to the app from the Pico when the board is connected to the Android device.
If you make changes to the voltage ranges in the app they will be lost when the board is next connected. 

#### Signal generator

>  If you have Rev. 2 of the FSCOPE board please see [FSCOPE-250K-Rev2](fscope-250k-rev2)
 
The output from the Scoppy signal generator is accessed via the two SIG pins at H12 on the board.
   
The upper pin (LP) is used when you want the signal to be fed through the low-pass RC filter (eg. when 'Sine Wave (PWM)' is selected as the signal type in the Scoppy app). When using the SIG LP pin, the two pins of H4 need to be connected with a jumper.

The lower SIG pin (DIRECT) is used for direct access to the signal generator output. Note: If the 2 pins of H4 are connected this will affect the output of the signal generator and so the jumper on these pins should be removed when using the SIG DIRECT pin.

#### AC/DC Coupling

The pins marked DC are used to select AC or DC coupling. Connect the pins with a jumper for DC coupling. Leave the pins unconnected for AC coupling.

#### 10X Probes

The board is compatible with 10X probes. The probe attenuation can be set in the app by tapping the channel badge at the bottom of the screen
and then tapping 'Settings' and 'Probe'.
   
10X probes may need to be compensated to match in the input capacitance of the oscilloscope. [This video](https://www.youtube.com/watch?v=ke7ST2CUxNo) by R&S explains probe compensation in detail.

#### Board Dimensions
See [here](/wiki/fscope-dso-500k-dimensions)

#### Enclosures
See [here](/wiki/fscope-dso-500k-enclosures)

#### Unpopulated holes/pads

>  If you have Rev. 2 of the FSCOPE board please see [FSCOPE-250K-Rev2](fscope-250k-rev2)
<br>
>  If you have Rev 4, 4a or 4b please see [FSCOPE-500K 4b](fscope-dso-500k-4b-unpopulated)

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
Restart/Reset. Shorting these will restart the DSO-500K. A momentary switch could be soldered to these holes/pads to make it easier to restart the oscilloscope. Double clicking the switch will cause the Pico (or Pico W) to enter USB mass storage mode.

_H7, H15_ 
<br>
For connecting external Wi-Fi and Trigger LEDS if the board is to be enclosed in a case.

_H9, R32_ 
<br>
For connecting an external status LED if the board is to be enclosed in a case (no firmware support for this as yet).

_AP/ST_
<br>
Reserved for future use. We might add support for switching between AP and Station modes by the press of a button attached to these pads.


#### Miscellaneous

The holes at the corners of the board are 3.3mm (130 mil).

### Updating the Firmware

Instructions are on the [Installation & Getting Started](../wiki/Installation-&-Getting-Started) page.

#### FSCOPE-500K
The firmware file for the Pico is named scoppy-fscope-500k-vNN.uf2 and the file for the Pico W is named scoppy-fscope-500k-picow-vNN.uf2 (where NN is the version number).

#### FSCOPE-500K
See [here](/dso-500k).

### Trimmer capacitor adjustment

The green trimmer capacitors on the board were adjusted before the board was shipped but if you find your square waves are not looking very square then adjusting them
might help. 

> Note. If a jumper is connecting the pins on H4 then the this will affect the output of the signal generator. Remove the jumper before performing the trimmer capacitor adjustment.

Instructions for adjusting the trimmer capacitors can be found in the [FSCOPE assembly instructions](fscope-500k).

### Help and Support
Visit the [FHDM TECH forum](https://fhdm.boards.net/)

## See also
{% include wifi-links.md %}
<br>
{% include scoppy-links.md %}
