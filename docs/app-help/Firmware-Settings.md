---
title: Firmware Settings
---

## How to access the Firmware Settings

To access the firmware settings, the Scoppy app must have established a connection to the Scoppy firmware on the Pico W (ie. the connection badge at the lower left of the app screen should show a status of _OK_). For help with this see [Getting started with Scoppy and the Pico W](../wiki/Getting-started-with-the-Pico-W).

Tap the connection badge at the the lower left of the screen and then tap _Connected device_ and then _Firmware settings_.

## Settings

### Device Name

The unique identifer of the device. Used with the _Scoppy device name_ connection method<sup>1</sup>. It is unlikely that you'll want to change this. 

### Wi-Fi Country

For optimum compatibility with your other Wi-Fi equipment select your country.

### Wi-Fi Mode

#### Access Point

The Pico W will function as an access point. To connect with the Scoppy app you'll need to select the SCOPPY network in Android Settings (Connections -> Wi-Fi)  

##### AP SSID

The SSID of the Pico W when operating in access point mode.

##### AP Password

The password of the Pico W access point.

##### AP Authorization Type

The authorization method used when the Pico W is in access point mode.

#### Station/Client

The Pico W will function as a Wi-Fi station (aka client). In other words, it will connect to your network just like any other device. This is probably the mode you want. 

##### SSID

The SSID of your network's Wi-Fi access point.

##### Password

The password used by your network's access point. This might also be referred to as a key.

##### Authorization Type

The method of security used by your access point. You should be able to find this in your access point's settings. If in doubt use WPA2/WPA Mixed which should work on most networks.

##### Scoppy Access Code

Use this used to restrict who can access the Pico W when in station/client mode. See [Wi-Fi Connection Settings](../app-help/WiFi-Connection-Settings) for more information about connecting using an access code.

You will most probably want to leave this field blank.

## <sup>1</sup>Wi-Fi Connection Methods

See [Wi-Fi Connection Settings](../app-help/WiFi-Connection-Settings)

#### See also
{% include wifi-links.md %}
<br>
{% include scoppy-links.md %}
