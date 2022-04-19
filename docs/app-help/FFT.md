---
title: FFT Display
---

<br>

### How to enable the FFT display

From the MENU tap the DISPLAY button. Then tap either:
* FFT to show just the FFT screen
* FFT + YT to display the FFT and the normal time-domain (YT) scope output

To hide the FFT display, tap the Display button and then select YT (Default)
   
When the FFT is enabled, the YT window can be shown/hidden by tapping the 'YT Display' checkbox at the bottom of 
the CONTROLS menu.

When both the FFT and YT windows are visible, the controls for both are available in the CONTROLS menu. Just tap either
the YT or FFT tab to select which window you wish to control. 

<br>

### How to configure the FFT for best results

The FFT works best when the resolution bandwidth (RBW) is as low as possible. The RBW is the sample rate divided by the number of sample points that are used
by the FFT algorithm and so we should try to make the the sample rate small and the number of sample points high.
You can't configure the number of sample points in the Scoppy app (yet) so the aim should be to make the sample rate as low as
possible while still displaying the maximum frequency of interest. The FFT can display frequency components up to half the sample rate.

Here's one way of doing it:
* Enable the FFT and YT displays as described above
* Tap the YT tab in the CONTROLS menu and adjust the Time/Div setting so that sample rate (shown at the top-left of the app) is as low as possible while also at least twice the sample rate of the maximum frequency component you are interested in.
* Now tap the FFT tab and tap-and-hold the SPAN button. This will fit the FFT trace in the screen with 0Hz at the left and the maximum displayable frequency on the right.
* Experiment with different Time/Div values.
   
Tip: An alternative method of adjusting the sample rate is to tap the sample rate value at the top-left of the screen and select a sample rate from the drop-down menu. Just remember to change it back to Auto when finished with the FFT!
   
Tip: When doing a single capture, the number of samples used for the FFT will be 16k. This might give better results than RUN mode.

<br>

### Some Definitions
START - The frequency at the left of the FFT screen (even if the trace doesn't go that far to the left)   
   STOP - The frequency at the right of the FFT screen (even if the trace doesn't go that far to the right)   
   CENTER - The frequncy at the horizontal center of the screen   
   SPAN - Stop minus Start

<br>

### Horizontal Controls
#### SPAN
Changes the span while keeping the center unchanged. Touch-and-hold the SPAN button to fit the trace horizontally into the screen

#### CENTER
Changes the frequency component displayed at the horizontal centre of the screen while keeping the span unchanged. Touch-and-hold to move the highest peak to the center.

<br>

### Vertical Controls
#### SCALE
Changes the amplitude per division

#### POSITION
Changes the vertical position of the trace

Tip: First change the POSITION so that the top of the highest peak is near the top of the screen. Then adjust the scale to your liking.

### Vertical Units
#### dBm
RMS Amplitude with respect to 1mW (logarithmic scale). Assumes a load of 50 ohms.

#### dBmV
RMS Amplitude with respect to 1mV (logarithmic scale).

#### V
Peak amplitude (ie. 50% of Vpp) with respect to 1V (linear scale).

### Channels
The FFT can display either CH1, CH2 or both. The selected channel(s) must be switched on. If not switched on, the FFT screen will not display the trace(s).

<br>
[App Help](.)     
[All Documentation](../TOC)         
[Scoppy on GitHub](https://github.com/fhdm-dev/scoppy)
