---
title: Analog Front-End Design 3
---

> If you have suggestions for improvements or would like to share your own designs for a Scoppy analog front end then please head to the [Scoppy forum](https://github.com/fhdm-dev/scoppy/discussions).

This design builds on Design 2 and adds over and under voltage protection to the analog front end. After all, we won’t have a cheap oscilloscope if we keep frying our components!

I’m assuming here that the minimum and maximum voltages that will be applied to the input of the scope will be -18V and +18V respectively.  It has been tested from -18.5V to 18.5V (two of my 9V batteries in series) but of course If you decide to use this design you are doing so at your own risk. I personally wouldn’t use Scoppy with an expensive phone/tablet just in case something unexpected goes wrong (better to use an old, obsolete phone that is no longer used for anything else) - especially when dealing with higher voltages - but of course you can do what you like.

### Protecting the Op-Amp input(s)

First of all we need to protect the op-amp. In this design we’ll be using an LM324 op-amp, which is very similar to the LM358 but contains four individual op-amps rather than two. We’ll be using three of these op-amps. The reason for this will be explained later.

According to the datasheet for the LM324 the allowed input voltage range goes from -0.3V to 32V. Of course 32V is above the maximum expected voltage (18V) and so we don’t need to worry about over-voltage protection. However we do need to ensure that the voltage at the input pins don’t go below -0.3V. A schottky diode can be used to clamp the voltage to something above -0.3V (D1 in the schematic). 

One thing that needs to be considered when selecting the diode is its reverse current. The 1N5817 has a very low forward voltage but high reverse current and this results in a voltage drop at the input of the op-amp (in the order of 100mV). Presumably this is because it draws current through the high value input resistor (Rg1). The 1N5711 has a much lower reverse current specification and I couldn’t discern any voltage drop when this was inserted into the circuit. However, its forward voltage (at the current expected in this part of the circuit) is very close to the minimum allowed voltage of -0.3V. To be safer I prefer to use something like a BAT46. It does result in a voltage drop of a few millivolts but the clamped voltage is more like -0.23V.

### Protecting the Pico/RP2040

The Pico datasheet states that:

`the ADC capable GPIO26-29 have an internal reverse diode to the VDDIO (3V3) rail and so the input voltage must not exceed VDDIO plus about 300mV`

The obvious way to protect the ADC inputs (GPIO26-29) then is to simply insert a schottky diode between the ADC input and VDDIO. However, the RP2040 datasheet says that:

`the voltage on the ADC analogue inputs must not exceed IOVDD ...<snip>... Voltages greater than IOVDD will result in leakage currents through the ESD protection diodes`

That suggests to me that we shouldn’t be allowing current to pass (leak) through our clamping diode and into IOVDD. I could be completely wrong here - if you think so then please share your thoughts in the forum ([Discussions](https://github.com/fhdm-dev/scoppy/discussions)).

Anyway, to be safe we’re going to avoid that situation by sending the current to the output of one of our op-amps (LM324-sink on the schematic). The LM324 is able to sink up to ~10mA so this should work fine if we limit the current from the main op-amp (LM324-amp in the schematic). Given that the maximum voltage expected at the output of LM324-amp is around 4.5V (Vcc - 1V) then we need a resistor of at least 120R to limit the current to 10mA (4.5-3.3 / 0.010 = 120). A 220R resistor should do fine (Rout).

And of course the reason we are using an LM324 rather than the LM358 of the previous designs is that three op-amps are required.

A 1N5817 diode (D2) is used here (rather than a BAT46 - used on the input of LM354-amp) because at the expected maximum current of 10mA the forward voltage drop of the BAT46 is higher than 300mV. The high reverse current of the 1N5817 is not such an issue here because Rout has a low value and so there will only be a small voltage drop across Rout when D2 is reverse biased.

### Construction

![Schematic](https://github.com/fhdm-dev/scoppy/raw/main/images/frontend3/schematic.png)   
![Breadboard](https://github.com/fhdm-dev/scoppy/raw/main/images/frontend3/bb.png)   

Here are some instructions for assembling this front end on a breadboard. The pin numbers refer to the LM324 PDIP package. Refer to the schematic and breadboard image above. NB. The rail labelled 5V on the schematic is actually VSYS which of course is not necessarily 5V because it depends on how charged the battery is on your Android device.

Connect 3V3 of the Pico to the top red power rail of the breadboard. Connect VSYS to the bottom red power rail. Connect both ground rails of the breadboard to one of the GND pins of the Pico. The fuse as shown in the breadboard image is optional.

Connect the Vcc pin of the LM324 to the VSYS rail. Connect the GND pin of the LM324 to the GND rail. Don’t connect anything to the ADC pin(s) of the Pico yet.

Now we’ll configure each of the 4 op-amps of the LM324 in turn.

**Op-amp 2 - Unused**   
Op-amp 2 (pins 5, 6 and 7 of the PDIP package) is not used so we’ll wire it up as recommended in the TI tech note - [How to Properly Configure Unused Operational Amplifiers](https://www.ti.com/lit/an/sboa204a/sboa204a.pdf?ts=1624953615530&ref_url=https%253A%252F%252Fwww.google.com%252F).

The voltage at the non-inverting input should be approximately VSYS/2 and the output should be the same.

**Op-amp 4 - Vref**   
Wire up this op-amp as shown in the schematic. The voltage at the output should be approximately 1.65V.

**Op-amp 3 - sink**   
Wire up this op-amp as shown in the schematic. The voltage at the output should be 3.3V.

**Op-amp 1 - amp**   
Wire up this op-amp as shown in the schematic, including the under-voltage protection diode on the input (D1) and the current limiting resistor (Rout) and over-voltage protection diode (D2) on the output. Don’t connect the output to the Pico yet.

You should now be able to safely apply any voltage at Vin1/Vin2 of between -18V and +18V. Test that the voltage at the input of the LM324 (Vampin) doesn’t go below -.3V and the voltage at the output of op-amp 2 after Rout (Vadc) doesn’t go above 3.6V.

Once you’ve confirmed that all of the op-amps have been wired correctly you can connect the output of Rout to the ADC pin of the Pico.

<br>    
<br>    
<br>    
    
> The author makes no warranty, representation or guarantees regarding the suitability of this design for any particular purpose. Nor does the author assume any liability arising out its use and specifically disclaims any and all liability, including without limitation special, consequential or incidental damages.








