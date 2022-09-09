---
title: Vertical Calibration
---

If Scoppy is not displaying the correct voltage levels you may need to adjust the voltage range settings in the app.

Note that this method assumes that you have already entered an approximate voltage range for the channel you are measuring. Reminder: to get to the voltage range settings tap the channel badge at the bottom of the screen and a menu should appear. Tap Settings and then Voltage Range(s).

#### Step 1.
Connect Vin to GND and note the value of Vmax in the Scoppy app. Ideally, the value of Vmax will be 0. If not, enter new values for the voltage range as follows:   
Min. Voltage = Min. Voltage - Vmax   
Max. Voltage = Max. Voltage - Vmax   

(If Vmax is positive, you’ll end up with smaller values for Min and Max. If Vmax is negative you’ll end up with larger values).

The trace should now be at the GND level on the screen.

#### Step 2.
Apply a DC voltage to Vin that is about 80% of the maximum input voltage. If the vertical range is perfectly calibrated then the Vmax displayed in the Scoppy app will be the same as your input voltage and the calibration procedure is complete. If not, then read on!

Calculate the new value for Min. Voltage as follows   
(new) Min. Voltage = (current) Min.Voltage x Vin / Vmax

Likewise, calculate the new value for Max. Voltage as follows   
(new) Max. Voltage = (current) Max. Voltage x Vin / Vmax

Enter the new values and tap OK. Hopefully Vmax will show the correct voltage (ie. Vin).   
Go back to Step 1 to check that the 0 voltage level hasn’t changed. If it has then keep repeating both until you’re happy with the result.


<br>
{% include see-also.md %}
