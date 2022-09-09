---
title: The Oscilloscope Screen
---


![](https://github.com/fhdm-dev/scoppy/raw/main/images/ui-with-labels.png)

### Top Status Bar
**Sample Rate**   
The sample rate used to capture the displayed waveform. Tap this to set a fixed sample rate.

**Sample Count**   
The number of samples captured and stored by the app

**Sample Record View**   
High-level view of the overall waveform record. The gray rectangle represents the part of the record that is displayed on the screen. The vertical line is the position of the trigger point in the record.

**Horizontal Time/Div**   
The currently selected Horizontal time/div setting. Tap here to display a popup from which you can quickly change the horizontal time/div. The horizontal time/div can also be adjusted using the Horizontal TIME/DIV controls on the RHS control panel.

**Horizontal Position**   
The horizontal position in relation to the trigger point - measured in divs. This can be adjusted using the Horizontal POSITION controls on the RHS control panel.


### Right-hand side Control Panel
**Run Mode Button**  
Toggles between Run and Stopped modes
 
**Single Shot Capture Button**   
Captures a single waveform record. The sample count and rate will generally be higher than waveforms captured in Run mode.

**Navigation Button**   
Tapping this button will hide the control panel and show the function menu. From the function menu tap CONTROLS to show the control panel.

**Horizontal Controls**   
Use these to adjust the Horizontal time/div and position settings. 
Single tap or long-press the +/- buttons. Tap the TIME/DIV button to enter an exact value. Long-press TIME/DIV to reset to the default value. Tap the POSITION button to enter an exact value for the position. Long-press POSITION to reset the position to 0.

**Vertical Controls**   
Use these to adjust the Vertical volts/div and position settings for each channel. First select the channel you wish to adjust by tapping the appropriate CH button. Single tap or long-press the +/- buttons to adjust the selected channel. Tap the VOLTS/DIV button to enter an exact value for volts/div. Long-press VOLTS/DIV to reset to the default value. Tap the POSITION button to enter an exact value for the vertical position of the waveform on the screen. Long-press POSITION to reset the position to 0.

**Trigger Controls**
Use these to adjust the selected trigger channel, level and triggering mode. Single tap the LEVEL button to enter an exact value for the trigger level. Long press the LEVEL button to set the trigger level to the midpoint of the current waveform (ie. 50%). 

### Bottom Status Bar
**Signal Source**   
The source from which to obtain measurements. If USB is selected you will need to connect your Android device to a Raspberry PI Pico using an On-the-go (OTG) cable or adapter. The Pico will also need to have the scoppy-pico firmware installed (see the installation page in this wiki). Tapping this badge will open a menu from which you can change the signal source as well as view information about the currently connected device.

**Channel Badges**  
These display the status and settings of the two channels. Tap the badge to display a menu from which you can turn on/off the channel and modify channel settings.
   
- **Channel Volts/Div**    
Currently selected Volts/Div for the channel  
- **Channel Position**    
Vertical position of the channel waveform on the screen
- **Channel Voltage Range**   
If you have configured multiple voltage ranges in the channel settings then the currently selected range will be shown here. See the [Analog Front-End](./Analog-Front-End) documentation for more information.

**Trigger Badge**    
This displays the current trigger settings. Tap the badge to open the trigger menu.   
- **Trigger Channel**  
The currently selected trigger channel 
- **Trigger Level**   
The trigger level for the selected channel

### Waveform View (Grid/Gradicule)
**Channel Ground Levels**  
The vertical position on the screen which corresponds to 0V for the channel.

**Waveform Measurements**   


**Run Status**   
Indicated if the scope is in Run mode, Stopped or performing a single capture.

**Grid Lines and Waveform Traces**   
The width of these can be configured via Settings (Tap the Menu button to get to Settings).
    
<br>
{% include see-also.md %}
