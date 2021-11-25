# MAC Challenge LIDAR-Lite Raspberry Pi Setup

Installation guide for the LDIAR sensor in the MAC Challenge. Please follow the instrucitons below from Garmin first for enabling the I2C peripheral and wiring the LIDAR-Lite sensor before installing the script.

1. Clone the repositoty: `git clone https://github.com/greenfrogs/LIDARLite_RaspberryPi_Library.git`
2. Cd into the directory and build the code `cd LIDARLite_RaspberryPi_Library` and `make`
3. Edit permissions on run.sh file so it can run `chmod +x run.sh`
4. Run the application with `./run.sh` and try connecting in a webbrowser to the IP_ADDRESS:3000 (you can check the ip address on the pi with the command `ip a` and reading out the inet value for the eth0 adaptor)
5. Check current directory name with `pwd` (needed for the next step)
6. Set the application to begin on reboot by running `crontab -e` and then adding `@reboot /home/pi/LIDARLite_RaspberryPi_Library/run.sh` (instead of /home/pi/LIDARLite_RaspberryPi_Library use the output from the pwd command in the preivous step)

## Instructions to enable the I2C peripheral in the ARM core

From a command shell, launch the configuration editor
```
sudo raspi-config
```
From the menu, select
* **Interfacing Options**
* **P5  I2C**
* **Enable** the interface
* Select **Finish**
* Reboot the Raspberry Pi


## Wiring the LIDAR-Lite to the Raspberry Pi

[Raspberry Pi Header](https://www.raspberrypi.org/documentation/usage/gpio/images/GPIO-Pinout-Diagram-2.png)

On the 40-pin header make the following connections -
```
* LLv3 Blue  (SDA) - RPi pin 3 (GPIO 2)
* LLv3 Green (SCL) - RPi pin 5 (GPIO 3)
* LLv3 Red   (5V ) - RPi pin 4
* LLv3 Black (GND) - RPi pin 6

- Wire a 680uF capacitor across pins 4 and 6
```

Additionally, see the following tutorials for other information concerning I2C on Raspberry Pi
* [Adafruit](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup/configuring-i2c) - Configuring I2C
* [Sparkfun](https://learn.sparkfun.com/tutorials/raspberry-pi-spi-and-i2c-tutorial) - SPI and I2C Tutorial


## License
Copyright (c) 2019 Garmin Ltd. or its subsidiaries. Distributed under the Apache 2.0 License.
See [LICENSE](LICENSE) for further details.
