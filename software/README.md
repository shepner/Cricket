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


Prepare to Compile the i2s module


---

install software for I2S following these instructions: [rpi-i2s](https://github.com/nejohnson2/rpi-i2s)
