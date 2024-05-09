---
title: Erase RPi Pico and Pico W flash storage 
---

This document describes how to erase all of the data from the Rasperry Pi Pico and Pico W flash storage.

1. Download the [flash_nuke.uf2](https://datasheets.raspberrypi.com/soft/flash_nuke.uf2)
 file to your computer. The file is available from Raspberry Pi at this location:
<br>
[https://datasheets.raspberrypi.com/soft/flash_nuke.uf2](https://datasheets.raspberrypi.com/soft/flash_nuke.uf2)

2. While holding down the BOOTSEL button on the Pico, connect the Pico to your computer with a USB cable.

3. The Pico should appear on your computer as mass storage device. Copy the flash_nuke.uf2 file to this device.

4. After about 10 seconds the Pico should appear once again as a mass storage device.

You can check that the flash has been erased successfully by plugging in the Pico WITHOUT pressing the BOOTSEL button.
The Pico should appear as mass storage device and the LED on the Pico should NOT be on or blinking.


<br>
{% include see-also.md %}
