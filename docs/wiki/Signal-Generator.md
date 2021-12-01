---
title: Signal Generator
---

### Square Wave
Generates a square wave on GPIO 22. The frequency defaults to 1kHz.

### Sine Wave (PWM)
Generates a square wave on GPIO 22 where the duty cycle changes according to the sine function. The frequency
of the sine wave is 1kHz.   

This PWM signal can be converted to a sine wave by the addition of a low pass filter.
A filter using a 1k resistor and 0.1uF capacitor should work.

See this [All About Circuits](https://www.allaboutcircuits.com/technical-articles/low-pass-filter-a-pwm-signal-into-an-analog-voltage/) article for more information.
