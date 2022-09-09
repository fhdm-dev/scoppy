---
title: Signal Generator
---

Scoppy includes a very basic (PWM) signal generator. This is accessed by tapping the SIGNAL GENERATOR
button on the menu panel. The signal is ouput on GPIO 22.

When the Pico is powered on the signal defaults to a 1kHz square wave.

### Signal Type

#### Square Wave
Generates a square wave between 100Hz and 1.25MHz with a 50% duty cycle.

#### Sine Wave (PWM)
Generates a square wave where the duty cycle changes according to the sine function. The frequency
of the sine wave is 1kHz.   

This PWM signal can be converted to a sine wave by the addition of a low pass filter.
A filter using a 1k resistor and 0.1uF capacitor should work.

See this [All About Circuits](https://www.allaboutcircuits.com/technical-articles/low-pass-filter-a-pwm-signal-into-an-analog-voltage/) article for more information.

#### None

Turns off signal generation.

<br>
{% include see-also.md %}
