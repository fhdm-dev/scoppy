---
title: Using the FSCOPE-250K and DSO-500K
---

The [_FSCOPE-250K_](https://store.fhdm.xyz/fscope-250k) is a 2 channel oscilloscope analog front end for use with the Raspberry Pi Pico or Pico W and the Scoppy Android app.
   
The [_DSO-500K_](https://store.fhdm.xyz/dso-500k) is a fully assembled version of the FSCOPE-250K.

### Features and Specifications
- Input impedance: 1M Ohm / 22pF
- Four input voltage ranges (sensitivity levels): +-6V, +-2V, +-1V, +-0.5V
- Compatible with 10X probes
- Overvoltage protection (tested up to +-20V)
- Access to all pins of the Raspberry Pi Pico
- Signals can be input via 0.1" header pins or BNC connectors
- Built-in low pass filter enables generation of analog signals via PWM 
- AC and DC coupling of the input signals
<br>

### Using the FSCOPE-250K and DSO-500K

#### Connecting to your Phone/Tablet

If you have a DSO-500K or an FSCOPE-250K with a Pico W, then please see [Getting started with Scoppy and the Pico W](./Getting-started-with-the-Pico-W) for instructions on how to establish a wireless connection between the board and the Scoppy app on your phone/tablet.

Otherwise, attach the small end of an OTG adapter cable/adapter to the USB input of the Android device (do NOT plug it into the USB socket of the FSCOPE/DSO board) and plug the other end of the adapter into a USB cable. This cable then plugs into the micro-USB connector on the FSCOPE/DSO board.

Once you open the app and a connection is established between the Pico and the Scoppy app the onboard LED should stop blinking. You may need to tap the 'Run' button in the app if the scope is currently stopped (Scoppy will either be RUNNING or STOPPED. This status is displayed at the top right of the grid).

#### Connecting the signal source

The signal source can be connected to either the header pins labeled CH1 and CH2 or a BNC connector (if fitted). Note that all GND pins/connections are connected together internally.

#### Input voltage ranges

The FSCOPE-250K and DSO-500K will automatically change the input voltage range (sensitivity) as you adjust the volts/div setting in the app. The best vertical resolution is
obtained by adjusting volts/div so that the trace fills most of the screen vertically (assuming the vertical position is 0). Further increases in volts/div
may result in the signal being clipped.
    
When the voltage range changes you'll probably see the trace momentarily 'jump'. This is expected.   
   
The currently selected voltage range can be seen on the channel badge at the bottom of the app screen (a number between 0 and 3). To manually select a voltage range, tap the channel badge and then tap 'Select input voltage range'.   
   
The actual values of the voltage ranges are uploaded to the app from the Pico when the board is connected to the Android device.
If you make changes to the voltage ranges in the app they will be lost when the board is next connected. 

#### Signal generator (Rev 2)
__(the following applies to Rev. 2 of the FSCOPE board - see the back of the board for the revision number)__

The output from the Scoppy signal generator is accessed via the two SIG1 pins at H12 on the board.
   
The upper pin (LP) is used when you want the signal to be fed through the low-pass RC filter (eg. when 'Sine Wave (PWM)' is selected as the signal type in the Scoppy app). When using the SIG1 LP pin, the top two pins of H4 need to be connected with a jumper.

The lower SIG1 pin (DIRECT) is used for direct access to the signal generator output.  When using the SIG1 DIRECT pin, the lower two pins of H4 need to be connected with a jumper. Note: if the upper 2 pins of H4 are connected this will affect the output of the signal generator and so the jumper on these pins should be removed when using the SIG1 DIRECT pin. 

#### Signal generator  (Rev 3+)
__(the following applies to Rev. 3 and higher of the boards - see the back of the board for the revision number)__
 
The output from the Scoppy signal generator is accessed via the two SIG pins at H12 on the board.
   
The upper pin (LP) is used when you want the signal to be fed through the low-pass RC filter (eg. when 'Sine Wave (PWM)' is selected as the signal type in the Scoppy app). When using the SIG LP pin, the two pins of H4 need to be connected with a jumper.

The lower SIG pin (DIRECT) is used for direct access to the signal generator output. Note: If the 2 pins of H4 are connected this will affect the output of the signal generator and so the jumper on these pins should be removed when using the SIG DIRECT pin.

#### AC/DC Coupling

The pins marked DC are used to select AC or DC coupling. Connect the pins with a jumper for DC coupling. Leave the pins unconnected for AC coupling.

#### 10X Probes

The board is compatible with 10X probes. The probe attenuation can be set in the app by tapping the channel badge at the bottom of the screen
and then tapping 'Settings' and 'Probe'.
   
The frequency compensation of 10X probes will need to be adjusted to match in the input capacitance of the oscilloscope.

#### Miscellaneous

H9, H10 - these are tiny prototyping areas. One hole is connected to GND. The others are not connected to anything.

__Rev 2. only__

H7, C28 and H6 - for a second signal generator (not implemented) - these will be removed in the next revision of the board.

CN1 and U7 - For attaching an IDC connector and 5V->3.3V level shifter (SN74CB3T3245DWR). Allows the Scoppy logic analyzer to be used with 5V circuits. This will be removed in future revisions of the the board.

H4 - The bottom row is not actually necessary and will be removed in the next revision of the board.

The holes at the corners of the board are 4mm (160 mil).

__Rev 3. and later__

The holes at the corners of the board are 3.3mm (130 mil).

## See also
{% include wifi-links.md %}
<br>
{% include scoppy-links.md %}
