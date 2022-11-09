---
title: FSCOPE-250K REV. 2
---

> The following information is for Revision 2 of the FSCOPE-250K board - see the back of the board for the revision number

<br>

### Using the Signal generator

The output from the Scoppy signal generator is accessed via the two SIG1 pins at H12 on the board.
   
The upper pin (LP) is used when you want the signal to be fed through the low-pass RC filter (eg. when 'Sine Wave (PWM)' is selected as the signal type in the Scoppy app). When using the SIG1 LP pin, the top two pins of H4 need to be connected with a jumper.

The lower SIG1 pin (DIRECT) is used for direct access to the signal generator output.  When using the SIG1 DIRECT pin, the lower two pins of H4 need to be connected with a jumper. Note: if the upper 2 pins of H4 are connected this will affect the output of the signal generator and so the jumper on these pins should be removed when using the SIG1 DIRECT pin. 


### Trimmer capacitor adjustment

Feed a 1kHz square wave into the CH1 input (using jumper wires or 1X probes - do NOT use 10X probes). If the waveform displayed in the app doesn't look square then adjust the trimmer capacitor (C15) until it does. You'll need a small screwdriver to do the adjustment. Screwdrivers like those supplied with oscilloscope probes should work.

You can use the Scoppy signal generator to generate the 1kHz square wave as follows:
#### If you have Rev. 2 of the FScope board (see the back of the board for the Revision number):
1. Connect the two bottom pins on H4 with a jumper. If there is a jumper on the top row then remove that.
2. Connect the lower SIG1 pin (DIRECT) on H2 to CH1 with a jumper wire. 
3. You should see a square wave in the Scoppy app. Ensure the volts/div for CH1 is greater than 600mV (input voltage range 0) otherwise the signal might get clipped.

#### If you have Rev. 3 or later of the FScope board:
1. If there is a jumper on H4 then remove that.
2. Connect the lower SIG pin (DIRECT) on H2 to CH1 with a jumper wire. 
3. You should see a square wave in the Scoppy app. Ensure the volts/div for CH1 is greater than 600mV (input voltage range 0) otherwise the signal might get clipped.
   
Repeat the procedure for CH2 (the trimmer capacitor for CH2 is labeled C32).

### Miscellaneous

H9, H10 - these are tiny prototyping areas. One hole is connected to GND. The others are not connected to anything.

H7, C28 and H6 - for a second signal generator (not implemented) - these will be removed in the next revision of the board.

CN1 and U7 - For attaching an IDC connector and 5V->3.3V level shifter (SN74CB3T3245DWR). Allows the Scoppy logic analyzer to be used with 5V circuits. This will be removed in future revisions of the the board.

H4 - The bottom row is not actually necessary and will be removed in the next revision of the board.

The holes at the corners of the board are 4mm (160 mil).

<br>
{% include see-also.md %}
