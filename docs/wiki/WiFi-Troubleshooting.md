---
title: Wi-Fi Troubleshooting
---

The first thing to check is the LED on the Pico W board. See the table below.

|LED Status|What does this mean?|Possible fixes 
|---|------|--------------
|Off|The board or firmware is not working|Ensure the board is powered on<br><br>Ensure the correct firmware has been copied to the board<br><br>Restart the Pico W
|4 blinks then pause|The scoppy firmware is in *access point mode* and is waiting for your phone/tablet to join its network|Go to Connections -> Wi-Fi in Android Settings and select the SCOPPY network
|3 blinks then pause|The Pico W has joined your local network and is trying to connect to the Scoppy app|Ensure the Connection Type in the app is set to Wi-Fi<br><br>Ensure the [Wi-Fi Connection settings](../app-help/WiFi-Connection-Settings) in the app are correct<br><br>Tap Run in the app<br><br>Tap the connection badge and then Reset Connection<br><br>Try exiting the app and reopening it<br><br>Disable Wi-Fi on the Android device and then enable it again<br><br>If all else fails try restarting the Android device and the oscilloscope
|2 blinks then pause|The scoppy firmware is trying to establish a connection to the app over USB<sup>2</sup>|If you want to use USB, ensure the Connection Type in the app is set to USB.<br><br>If you want to use Wi-Fi, wait 10 seconds and Scoppy will try and establish a connection over Wi-Fi (and the LED status will change). 
|Continuous fast blinking (5 per second)|The Pico W is trying to join your local network|Check that the SSID, password and authentication type in the _firmware settings_ are correct. To check these you'll need to connect via either USB or with the Pico W in _access point mode_.<br><br>Check that your network is compatible<sup>1</sup> with the wireless chip on the Pico W (especially that it is a 2.4GHz network, NOT 5GHz)
|Continuous slow blinking (1 per second)|The Scoppy firmware is trying to establish communication with the Scoppy app|Tap Run in the app<br><br>If all else fails try exiting the app and reopening it

#### <sup>1</sup>Network Compatibility

Wi-Fi 4 (802.11n), Single-band (2.4 GHz)

#### <sup>2</sup>Connection Sequence

When it first starts up, the Scoppy firmware will check if the Pico W is connected to an Android device via USB. If so it will try to connect to the Scoppy app
via USB. If a connection has not been established within 10 seconds, the firmware will attempt to make a connection via Wi-Fi.

Note: If the Pico W is powered by the USB port of a computer it may also attempt to connect via USB for a period of 10 seconds before switching to Wi-Fi. For the
fastest startup-up time the Pico W should be powered by a 5V DC source without active data lines (eg. a power plug or battery).

### Wi-Fi LED ###

A LED can connected to GPIO 14. If this LED is on or blinking then the Scoppy firmware is using Wi-Fi. If the LED is off then the firmware is using USB. 

### Serial output

The Scoppy firmware will print some diagnostic messages to UART0 on GPIO0 and GPIO1. This will include the current firmware settings. See the section _See "Hello World" UART output_ in the _Getting started with Raspberry Pi Pico_ guide for a primer on how to view the serial output of the Pico W.

## See also
{% include wifi-links.md %}

<br>
<br>
{% include scoppy-links.md %}
