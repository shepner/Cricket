Prototype Hardware v1

Base computer
* $10 [Raspberry Pi Zero W](https://www.adafruit.com/product/3400)

Voice
* $6 [Adafruit I2S 3W Class D Amplifier Breakout - MAX98357A](https://www.adafruit.com/product/3006) (I2S)
* $3 [Mono Enclosed Speaker - 3W 4 Ohm](https://www.adafruit.com/product/3351)

Hearing
* $7 [Adafruit I2S MEMS Microphone Breakout - SPH0645LM4H](https://www.adafruit.com/product/3421) (I2S)

Touch
* $5 [Adafruit LIS3DH Triple-Axis Accelerometer (+-2g/4g/8g/16g)](https://www.adafruit.com/product/2809) (I2C or SPI)

Vision
* $8 [Adafruit APDS9960 Proximity, Light, RGB, and Gesture Sensor](https://www.adafruit.com/product/3595)

Power
* $20 [PowerBoost 1000 Charger - Rechargeable 5V Lipo USB Boost @ 1A - 1000C](https://www.adafruit.com/product/2465)
* $15 [Lithium Ion Polymer Battery - 3.7v 2500mAh](https://www.adafruit.com/product/328)

---

[I2S howto on the Raspberry Pi](https://github.com/nejohnson2/rpi-i2s) gives a good writeup for how to do this.

Here is a Raspberry Pi GIO pinout from [pinout.xyz](https://pinout.xyz/pinout/pcm) highlighting the PCM (I2S??) pins: <img src="https://github.com/shepner/Cricket/blob/master/hardware/RPi_PCM.png?raw=true" align="right" width="300" height="400">

Wiring for [Adafruit I2S MEMS Microphone Breakout - SPH0645LM4H](https://www.adafruit.com/product/3421)
* 3v   -> RPi pin 1  (3.3v Power)
* GND  -> RPi pin 6  (Ground)
* BCLK -> RPi pin 12 (BCM 18 (CLK))
* DOUT -> RPi pin 38 (BCM 20 (DIN))
* LRCL -> RPi pin 35 (BCM 19 (FS))
* SEL  -> RPi pin 9  (Ground)

The documentation can be found [here](https://learn.adafruit.com/adafruit-i2s-mems-microphone-breakout/) with information about how to wire 2 of them together [here](https://learn.adafruit.com/adafruit-i2s-mems-microphone-breakout/raspberry-pi-wiring-and-test)


Wiring for [Adafruit I2S 3W Class D Amplifier Breakout - MAX98357A](https://www.adafruit.com/product/3006)
* VIN  -> RPi pin 2  (5v Power)
* GND  -> RPi pin 20 (Ground)
* SD   -> RPi pin NA
* GAIN -> RPi pin NA
* DIN  -> RPi pin 40 (BCM 21 (DOUT))
* BCLK -> RPi pin 12 (BCM 18 (CLK))
* LRC  -> RPi pin 35 (BCM 19 (FS))
* \+    -> SPEAKER RED
* \-    -> SPEAKER BLACK

The documentation can be found [here](https://learn.adafruit.com/adafruit-max98357-i2s-class-d-mono-amp/downloads)

Note that running this from 5v will signal to output in "stereo" due to the 1Mohm resistor rom SD to Vin.  That is, both L and R channel signals will be sent through the single output.


---

Here is the general GIO header
<img src="https://pinout.xyz/resources/raspberry-pi-pinout.png">

---

[Eagle PCB CAD software](https://www.autodesk.com/products/eagle)
