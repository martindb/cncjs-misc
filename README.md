# cncjs-misc

Miscellaneous scripts/configs/notes guide for my CNC machine (raspberry pi)

----
# Install NOOBS / Config Raspbian

https://www.raspberrypi.org/downloads/noobs/
https://www.sdcard.org/downloads/formatter_4/eula_mac/


Tips:
- Disable GUI
- Set hostname, wifi, ssh, serial, tz, wifi country, locale
- Change passwords
- Add keys
- Free space
https://lifehacker.com/instantly-free-up-almost-1gb-on-your-raspberry-pi-by-di-1773831271
- Set LC_ALL=en_US.UTF-8 in /etc/environment
- Update/Upgrade
https://www.raspberrypi.org/documentation/raspbian/updating.md


----
# Power button and LED

https://howchoo.com/g/mwnlytk3zmm/how-to-add-a-power-button-to-your-raspberry-pi
https://howchoo.com/g/ytzjyzy4m2e/build-a-simple-raspberry-pi-led-power-status-indicator

TEST!

----

# Samba gcode share files (CNCjs watch dir)

mkdir -p /home/pi/cncjs/gcode

chmod 777 /home/pi/cncjs/gcode

#Install samba

sudo apt-get install samba samba-common-bin

#Copy smb.conf to /etc/samba dir

/etc/samba/smb.conf

#Restart samba service

sudo /etc/init.d/samba restart

----
# Install Chilipeppr

http://chilipeppr.com/jpadie
https://github.com/chilipeppr/serial-port-json-server/releases

Install in /home/pi/chilipeppr

Use chilipeppr.sh to exetue it (infinite loop)

-----
# Install CNCJS

https://github.com/cncjs/cncjs/wiki/Setup-Guide:-Raspberry-Pi-%7C-System-Setup-&-Preparation

Not use PM2 (will use cron)

----

# Install tablet pendant

mkdir -p /home/pi/cncjs/

cd /home/pi/cncjs/

wget https://github.com/cncjs/cncjs-shopfloor-tablet/archive/v1.0.4.tar.gz

tar zxf v1.0.4.tar.gz

----


# Startups all with root's cron (sudo crontab -e)


#Start chilipeppr

@reboot /home/pi/chilipeppr/chilipeppr.sh

#Start CNCjs and pendants

@reboot cnc -m /tablet:/home/pi/cncjs-shopfloor-tablet-1.0.4/src -w /home/pi/cncjs/gcode

@reboot /home/pi/cncjs/cncjs-pendant-ps3.sh

###@reboot cnc -m /pendant:/home/pi/cncjs-pendant-tinyweb-1.2.4/src -m /tablet:/home/pi/cncjs-shopfloor-tablet-1.0.4/src -w /home/pi/gcode

#Start video streamer

###@reboot /home/pi/mjpg-streamer.sh start

---------
# Dualshock 3 (PS3) Shanwan clone pendant

Guide for connecting to RPI 3 internal BT:
https://raspberryblog.de/?p=1870

Patched bluez from here:
https://github.com/luetzel/bluez

---------
---------

# Falta esta parte - NO ANDA parece

Estoy probando con el bluez 5.48

https://scribles.net/updating-bluez-on-raspberry-pi-5-43-to-5-48/

Veremos si anda con este, o tengo que usar el patcheado.... pero necresito conectar el ds3 al usb y ya lo tengo todo cerrado.... cuando lo abra ponerle el soporte a la SD!!!!

---------

# BT errors (Bluetooth: hci0: Frame reassembly failed)

Change in /usr/bin/btuart 921600 with 460800 and reboot




