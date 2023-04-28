---
title: DSO500K-U
---

> The DSO500K-U is powered by a Raspberry Pi RP2040 Microcontroller as used on the Raspberry Pi Pico. References to Pico in this documentation also apply to the DSO500K-U

### Connecting to your Phone/Tablet

Attach the small (male) end of an OTG cable/adapter to the USB input of the Android device (do NOT plug it into the USB socket of the DSO500K-U!). 
Plug a standard USB cable (Type-A to Micro-USB) into the other end of the OTG cable/adapter . Attach the other end of the USB cable to the micro-USB connector on the DSO500K-U board.

#### RUN

Once you open the Scoppy app and a connection is established between the DSO500K-U and the app, the status LED should stop blinking. You may need to tap the 'Run' button in the app if the scope is currently stopped (Scoppy will either be RUNNING or STOPPED. This status is displayed at the top right of the grid).

### Connecting the signal source

The signal source can be connected to either the header pins labeled CH1 and CH2 or a BNC connector (if fitted).

> Note that all GND pins/connections are connected together internally. If using two channels, the (probe) GND wires for each channel must be at the same potential (because they are effectively shorted together). 

> For each channel the center of the BNC connector and the corresponding header pin input are also connected internally. It it recommended you use either the BNC connector or the header pin input but NOT both at the same time. If you have installed BNC connectors it might be prudent to remove the header pins.

### Input voltage ranges

The DSO500K-U will automatically change the input voltage range (sensitivity) as you adjust the volts/div setting in the app. The best vertical resolution is
obtained by adjusting volts/div so that the trace fills most of the screen vertically (assuming the vertical position is 0). Further increases in volts/div
may result in the signal being clipped.
    
When the voltage range changes you'll probably see the trace momentarily 'jump'. This is expected.   
   
The currently selected voltage range can be seen on the channel badge at the bottom of the app screen (a number between 0 and 3). To manually select a voltage range, tap the channel badge and then tap 'Select input voltage range'.   
   
### Signal generator

The output from the Scoppy signal generator is accessed via the SIG pin.

### AC/DC Coupling

The pins marked DC are used to select AC or DC coupling. Connect the pins with a jumper for DC coupling. Leave the pins unconnected for AC coupling.

### 10X Probes

The board is compatible with 10X probes. The probe attenuation can be set in the app by tapping the channel badge at the bottom of the screen
and then tapping 'Settings' and 'Probe'.
   
The frequency compensation of 10X probes will need to be adjusted to match in the input capacitance of the oscilloscope (as is the case with all oscilloscopes).

This oscilloscope is NOT suitable for measuring high (eg. mains) voltages. 

### Board Dimensions
See [here](/wiki/fscope-dso-500k-dimensions)

#### Enclosures
See [here](/wiki/fscope-dso-500k-enclosures)

### Unpopulated holes/pads

There will be some unpopulated holes/pads on your board. Depending on your board revision these may include:

_G_
<br>
Ground/GND

_D7 to D0_
<br>
Logic analyzer inputs. Maximim 3.3V.

_Ext_
<br>
Reserved for future use.

_H13_
<br>
Reserved for future use.

_STATUS_
<br>
Can be connected to an LED if the DSO500K-U is to be placed in an enclosure.

_H15 (Trigger)__
<br>
Can be connected to an LED if the DSO500K-U is to be placed in an enclosure.

_H4 (Sig. Gen)__
<br>
Can be wired to a connector if the DSO500K-U is to be placed in an enclosure.

_+3.3V, VSYS_
<br>
Test points

_-2.5V_
<br>
Test point for the -2.5V rail. Do not draw current from this rail as it will adversely affect the performance
of the oscilloscope.

_H18_
<br>
Test points

### Updating the Firmware

Download the firmware file onto your computer.
[scoppy-dso500k-u-v16.uf2](https://github.com/fhdm-dev/scpdl1/raw/master/a/v16/scoppy-dso500k-u-v16.uf2)

Short the BOOT pins with a jumper (or hold down the BOOLSEL button if fitted) while connecting the DSO500K-U to your computer with a USB cable.
The DSO500K-U will appear as a mass storage device.

!!! Remove the jumper from the BOOT pins (or release the BOOLSEL button if fitted).

Copy the firmware file to the mass storage device. The status LED on the DSO500K-U should start blinking. If not, ensure you have removed the jumper from
the BOOT pins. 

### Trimmer capacitor adjustment

The green trimmer capacitors on the board were adjusted before the board was shipped but if you find your square waves are not looking very square then adjusting them
might help. 

TODO

### Help and Support
Visit the [FHDM TECH forum](https://fhdm.boards.net/)

## See also
{% include wifi-links.md %}
<br>
{% include scoppy-links.md %}
