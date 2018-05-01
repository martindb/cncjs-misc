# cncjs-misc

Miscellaneous scripts/configs/notes for my CNC machine (raspberry pi)

----

# Startups all with root's cron (sudo crontab -e)

#Starteo CNCjs, streamer de la camara y pendant para el DS3

@reboot cnc -m /pendant:/home/pi/cncjs-pendant-tinyweb-1.2.4/src -m /tablet:/home/pi/cncjs-shopfloor-tablet-1.0.4/src -w /home/pi/gcode

@reboot /home/pi/mjpg-streamer.sh start

@reboot /home/pi/cncjs-pendant-ps3.sh

#Starteo el servicio de chilipeppr

@reboot /home/pi/chilipeppr/serial-port-json-server

---------

# Samba gcode share files (CNCjs watch dir)

#Install samba
sudo apt-get install samba samba-common-bin

#Copy smb.conf to /etc/samba dir
/etc/samba/smb.conf

#Restart samba service
sudo /etc/init.d/samba restart

-----

# Dualshock 3 (PS3) Shanwan clone pendant

Guide for connecting to RPI 3 internal BT:
https://raspberryblog.de/?p=1870

Patched bluez from here:
https://github.com/luetzel/bluez

---------

# BT errors (Bluetooth: hci0: Frame reassembly failed)

#Change in
/usr/bin/btuart

921600 with 460800 and reboot



