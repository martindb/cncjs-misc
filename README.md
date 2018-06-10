# cncjs-misc

Miscellaneous scripts/configs/notes guide for my CNC machine (raspberry pi)

----
# Install NOOBS / Config Raspbian

https://www.raspberrypi.org/downloads/noobs/
https://www.sdcard.org/downloads/formatter_4/eula_mac/


Tips:
- Disable GUI
- Set wifi, ssh, serial, tz, wifi country, locale
- Change passwords
- Add keys
- Free space
https://lifehacker.com/instantly-free-up-almost-1gb-on-your-raspberry-pi-by-di-1773831271

- As root

export LANGUAGE=en_US.UTF-8

export LANG=en_US.UTF-8

export LC_ALL=en_US.UTF-8

locale-gen en_US.UTF-8

dpkg-reconfigure locales


- Update/Upgrade
https://www.raspberrypi.org/documentation/raspbian/updating.md


----
# Power button and LED

https://howchoo.com/g/mwnlytk3zmm/how-to-add-a-power-button-to-your-raspberry-pi
https://howchoo.com/g/ytzjyzy4m2e/build-a-simple-raspberry-pi-led-power-status-indicator

TEST!

----

# Samba gcode share files (CNCjs watch dir)

#Install samba

sudo apt-get install samba samba-common-bin

#Copy smb.conf to /etc/samba dir

/etc/samba/smb.conf

#Restart samba service

sudo /etc/init.d/samba restart

-----
# Install CNCJS


----
# Install Chilipeppr


----

# Startups all with root's cron (sudo crontab -e)

#Start CNCjs, video streamer and pendants

@reboot cnc -m /pendant:/home/pi/cncjs-pendant-tinyweb-1.2.4/src -m /tablet:/home/pi/cncjs-shopfloor-tablet-1.0.4/src -w /home/pi/gcode

###@reboot /home/pi/mjpg-streamer.sh start

@reboot /home/pi/cncjs-pendant-ps3.sh

#Start chilipeppr

@reboot /home/pi/chilipeppr/serial-port-json-server

---------

# Dualshock 3 (PS3) Shanwan clone pendant

Guide for connecting to RPI 3 internal BT:
https://raspberryblog.de/?p=1870

Patched bluez from here:
https://github.com/luetzel/bluez

---------

# BT errors (Bluetooth: hci0: Frame reassembly failed)

Change in /usr/bin/btuart 921600 with 460800 and reboot

