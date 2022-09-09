---
title: Release Notes
---

### Android App v1.018 - Pico Firmware v10

#### New Features and changes
__FFT__   
Tap the DISPLAY button to show the FFT window. See the [FFT Help](../app-help/FFT) for more information.

__Probe Settings__   
The probe attenuation can now be set for each channel. Tap the channel badge at the bottom of the screen, then tap Settings and then Probe. When a setting other then 1X is selected, the current probe setting will be displayed in the channel badge.

__Cursor button__   
The cursor button has been moved to the controls panel. This is because there are now separate cursors for the normal waveform display (YT) and
the FFT display.

#### Bugs Fixed
* App would not remember some channel settings after restart
* Horizontal cursors not always visible when first enabled
* Voltage ranges uploaded from firmware not always recognized
* The auto voltage range feature would stop working after app restart
* App would exit when device back button was used to navigate to the home screen

### Android App v1.017 - Pico Firmware v9

#### XY Mode
To enable XY mode, tap Menu and then Display. The XY plot can be displayed on its own or together with the normal YT grid.

#### Other improvements
- In the signal generator screen you can now specify an exact frequency value. Tap the frequency dropdown menu
and then tap Custom. Enter the frequency.
- The app will now show a warning if you've set the Time/Div to a value that would cause the waveform to not be visible
- Voltage ranges can be compiled in the firmware and uploaded to the app automatically. Useful if you use the same Android Device with different front ends.

#### Bugs fixed
- Y cursor info showing incorrect value
- Not enough precision in trigger level dialog
- Tapping Help in the on-screen measurements dialog would actually change the settings
- App would sometimes crash when connecting/disconnecting the Pico
- The disabled channel would be used for the horizontal cursor info

### Android App v1.016 - Pico Firmware v8

#### On-screen measurement configuration
On-screen measurements can now be hidden and/or configured. Tap an on-screen measurement or the channel badge
at the bottom of the screen to access the on-screen measurement configuration window.

In Logic Analyzer mode tapping the far left of the screen will open the on-screen measurement configuration window.

#### Measurements snapshot
There is now a Measurement Snapshot window which will display all available measurements at a single point in time.
The measurement interval can be set to either the entire sample record or just the samples displayed on the screen.
The snapshot window also displays measurements not available as on-screen measurements such as Mean, AC RMS and DC RMS.

To open the Measurement Snapshot window tap the channel badge at the bottom of the screen and select _Measurements_ and then
_Snapshot_. The Measurement Snapshot can also be accessed by tapping and holding an on-screen measurement (or in Logic Analyzer
mode tapping and holding the far left of the screen).

#### Other changes
* Channels can now be quickly switched on/off by tapping and holding the channel badge at the bottom of the screen
* The captured samples can now be exported as a CSV file (tap the Export button on the Menu panel)
* The app now has more sane behaviour when multiple USB devices are attached via a hub. To have Scoppy ignore a device just
tap Deny when Android asks your permission.
* Fixed some bugs that sometimes caused the firmware to stop communicating with the app when the app was re-opened

### Android App v1.014 - Pico Firmware v7
* Falling edge trigger. Available in both Oscilloscope and Logic Analyzer modes
* More signal generator options. From the main menu panel tap the new Signal Generator button
* Run/Stop and Single buttons are now also on the main menu panel
* Tapping the sample record summary at the top of the screen will now move the horz. position
* Tapping the sample rate at the top-left of the screen allows you to choose a fixed sample rate
* It is now possible to select the trigger position within the sample record. Previously it was always in the center

### Android App v1.013 - Pico Firmware v6
* Touch gestures
    *   Swipe to change horz. and vert. position
    *   Pinch open/closed to change horz. and vert. scale
    *   Change selected channel by tapping GND indicator
* Cursors
* Increased logic analyzer max. sample rate to 25MS/s
* Improved logic analyzer triggering at higher sample rates

<br>
### See Also
{% include scoppy-links.md %}
