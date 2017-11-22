make sure everything is wired up as outlined in the hardware section

Flash a micro SD with [RASPBIAN STRETCH LITE](https://www.raspberrypi.org/downloads/raspbian/) using [Etcher](https://etcher.io/)

Default login U/P:  pi/raspberry

---

[Attach to WiFi](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md):

`wpa_passphrase "MySSID" "SomePasswordForTheSSID" | sudo tee -a /etc/wpa_supplicant/wpa_supplicant.conf > /dev/null`


[Enable sshd](https://www.raspberrypi.org/documentation/remote-access/ssh/):
```shell
sudo systemctl enable ssh
sudo systemctl start ssh
```

Now `sudo reboot` and make sure it connects to WiFi.  You make want to login to the console and run `ifconfig -a` to find out what IP address was assigned

---

Adafruit has [instructions](https://learn.adafruit.com/adafruit-i2s-mems-microphone-breakout/raspberry-pi-wiring-and-test) on how to install I2S support on the Raspberry Pi

install the updated 
* `/boot/config.txt`
* `/etc/modules`

`sudo reboot`

make sure the drivers loaded: `lsmod | grep snd`

Update the system (this will take a while)
``` shell
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install rpi-update
sudo rpi-update
sudo reboot
```

Install the compilation dependencies:
`sudo apt-get install git bc libncurses5-dev`

Download kernel source & compile (slow!):
```shell
sudo wget https://raw.githubusercontent.com/notro/rpi-source/master/rpi-source -O /usr/bin/rpi-source
sudo chmod +x /usr/bin/rpi-source
/usr/bin/rpi-source -q --tag-update
rpi-source --skip-gcc
```

---

continue testing from here

---


Prepare to Compile the i2s module

Compile I2S support: `sudo mount -t debugfs debugs /sys/kernel/debug`

'sudo cat /sys/kernel/debug/asoc/platforms'

NOTE: If you are using Pi Zero - the module name is 20203000.i2s

Download the module, written by [Paul Creaser](https://github.com/PaulCreaser/rpi-i2s-audio)
```shell
git clone https://github.com/PaulCreaser/rpi-i2s-audio
cd rpi-i2s-audio
vi my_loader.c
```

NOTE:  If using the Raspberry Pi Zero, look for the following lines:
```
.platform = "3f203000.i2s",
.name = "3f203000.i2s",
```
and change them to:
```
platform = "20203000.i2s",
.name = "20203000.i2s",
```

Compile the module
```
make -C /lib/modules/$(uname -r )/build M=$(pwd) modules
sudo insmod my_loader.ko
```

Verify it loaded
``` shell
lsmod | grep my_loader
dmesg | tail
```
Note that on the Pi 2/3 you'll see `asoc-simple-card asoc-simple-card.0: snd-soc-dummy-dai <-> 3F203000.i2s mapping ok` on the last line and on Pi Zero you'll see `asoc-simple-card asoc-simple-card.0: snd-soc-dummy-dai <-> 20203000.i2s mapping ok`

set the module to automatically load upon boot
``` shell
sudo cp my_loader.ko /lib/modules/$(uname -r)
echo 'my_loader' | sudo tee --append /etc/modules > /dev/null
sudo depmod -a
sudo modprobe my_loader
```

And then `sudo reboot`




---

===

---

install software for I2S following these instructions: [rpi-i2s](https://github.com/nejohnson2/rpi-i2s)
