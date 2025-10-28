# Cultivation sensors  
Code for all cultivation sensors that are used in experiment.

## Requirements

Any SBC with 2 USBs and 2 I2C interfaces. Install script covers Raspbian compatible devices and Armbian on sun50i-h616 SoC/dt

## Install

Run `./install.sh IP_ADDR P_HOSTNAME` where IP_ADDR is address of main server (with MongoDB database and clinostate_images docker container) and P_HOSTNAME is parent hostname (hostname of clinostat controller f.e if your controller hostname is clinostat, then you use "clinostat")

Script covers everything and can detect if your device is running Raspbian or Armbian with sun50i-h616. In case of other devices you will be ask if you want to continue. You will need to enable two I2C devices later.

## Configure

In config.py you can configure I2C addresses to which sensors are connected. `to_kill_at_exception` is switch if you want to stop execution of all threads when exception occures in any thread. `False` is disabled.

## Libraries

Those libraries are hard linked.

`./modules/sensors/ADS1x15` is forked from: https://github.com/chandrawi/ADS1x15-ADC MIT Licensed

`./modules/sensors/apds9960` is forked from https://github.com/liske/python-apds9960 GPL-3.0 Licensed

In both cases new device IDs where added.

## Misc
In misc folder you will find three systemd services. Most important one is `sensors.service` which you can install to automaticly run software at startup. Put it into `/etc/systemd/system/` dir and then enable it with `sudo systemctl enable sensors.service`. To start run `sudo systemctl start controller.service`.
