# cncjs-misc

Miscellaneous scripts for my CNC machine (raspberry pi)



# Startups all with root's cron (sudo crontab -e)

#Starteo CNCjs, streamer de la camara y pendant para el DS3
@reboot cnc -m /pendant:/home/pi/cncjs-pendant-tinyweb-1.2.4/src -m /tablet:/home/pi/cncjs-shopfloor-tablet-1.0.4/src -w /home/pi/gcode
@reboot /home/pi/mjpg-streamer.sh start
@reboot /home/pi/cncjs-pendant-ps3.sh

#Starteo el servicio de chilipeppr
@reboot /home/pi/chilipeppr/serial-port-json-server

---------


