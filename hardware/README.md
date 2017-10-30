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

[I2S howto on the Raspberry Pi](https://github.com/nejohnson2/rpi-i2s) gives a good writeup for how to do this as well as provides a very comprehensive RPi GPIO breakout highlighting the PCM (PCM == I2S??) pins.  This came from [pinout.xyz](https://pinout.xyz/pinout/pcm) which is a very good resource: <img src="https://github.com/nejohnson2/rpi-i2s/blob/master/rpi-pins.png" align="right" width="334" height="446">

Here is the general GIO header
<img src="https://pinout.xyz/resources/raspberry-pi-pinout.png">

---

[Eagle PCB CAD software](https://www.autodesk.com/products/eagle)
