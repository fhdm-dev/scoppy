---
title: Wi-Fi Connection Settings
---

## How to access the Wi-Fi connection settings

Tap the connection badge at the the lower left of the screen and then tap _Connection settings_. This menu item will only be visible when Wi-Fi is selected as the connection type. To change the connection type, tap the connection badge and then tap _Change connection type_.


## Connection Methods

The following connection methods apply when the Pico W is in _client/station mode_. If the Pico W is in _access point mode_ then the app will connect automatically.

### Auto
The app will try and connect to the first Pico W (with the Scoppy firmware installed) that it finds on the network. If another phone/tablet has already established a connection with the Pico W then the connection will fail.

Use this setting if there is only one Pico W (with the Scoppy firmware) that is on the network.

### Scoppy device name
Using this option you can select which Pico W to connect to. Tap the Search button to find Pico Ws on the network.

### IP address
If you know the IP address of the Pico W (eg. if you have setup a fixed MAC/IP mapping on your router) then you can enter it here. 

Note 1. The Pico W only obtains its IP address via DHCP - you cannot set a fixed address in the firmware.

Note 2. The MAC address of a connected Pico W can be found via the connection menu in the app and tapping _Connected device_ and _About device_. The MAC address is also written to the serial output when the Pico W starts up.

### Access Code
Use this option if you have multiple Pico Ws on the network and want to control who can access each one. The access code must also be entered in the
firmware settings. Once a Pico W is assigned an access code (and has been restarted) then it can't be connected to via the _Auto_ and _Scoppy device name_ connection methods (but the IP address method will still work - as will connecting via USB).

The same access code should not be used on different Pico Ws on the network.

Note: it can take a while for this option to take effect because the previous connection information is cached by Android for a period of time.

## See also
{% include wifi-links.md %}
<br>
{% include scoppy-links.md %}
