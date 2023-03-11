---
title: FSCOPE/DSO-500K Revision 4b and lower
---

### Unpopulated holes/pads

>  If you have Rev. 2 of the FSCOPE board please see [FSCOPE-250K-Rev2](fscope-250k-rev2)

There will be some unpopulated holes/pads on your board. Depending on your board revision these may include:

_H9, H10_
<br>
These are tiny prototyping areas. One hole is connected to GND. The others are not connected to anything.

_R32, R33_
<br>
Extra current limiting resistors for the Wi-Fi and Trigger LEDS. Add resistors here (and possibly remove R30/R31) to adjust
LED brightness.

_SWCLK, SWDIO_
<br>
Debug headers

_H11_
<br>
Not used

_+3.3V, VSYS_
<br>
Test points

_-2.5V_
<br>
Test point for the -2.5V rail. Do not draw current from this rail as it will adversely affect the performance
of the oscilloscope.

_H17, RESTART_
<br>
Shorting these will restart the Pico (W). A momentary switch could be soldered to these holes/pads to make it easier to restart
the oscilloscope.

_H7, H15, R35, R36_ 
<br>
For connecting external Wi-Fi and Trigger LEDS if the board is to be enclosed in a case.

_H16, R32_ 
<br>
For connecting an external status LED if the board is to be enclosed in a case (no firmware support for this as yet).

## See also
{% include wifi-links.md %}
<br>
{% include scoppy-links.md %}
