
NETWORK SETTINGS
================


.. image:: _images/13_CP_networksettings.png


INFO
******

CHANGE IP
*********

**192.168.2.** => sets the ip range to 192.168.2.***

**10.0.0.0.** => set the ip range to 10.0.0.0.***

**RJ45 DHCP** => sets the rj45 connection to dhcp to get the ip adress from a router


REMOTE ACCESS
*************

see video tutorial: 
https://video.pocketvj.com/AVideo/video/3/pocketvj-exhibition-access-from-everywhere-over-the-internet



CP PASSWORD
***********



.. image:: _images/13_CP_connectwifi.png



CONNECTING TO WIFI
*******************

Used to connect to an in house wifi with internet so you can accesss from anywhere.

see video tutorial: https://video.pocketvj.com/AVideo/video/11/pocketvj-exhibition-wifi-connecting


.. image:: _images/13_CP_wifiantenna.png






UDP Control
***********

You can control the PocketVJ with UDP commands. On port ``5000``

**Uppercase and lowercase matters!**


When using Packetsender or similar, make sure to send a "Newline" after every command, 

e.g:   ``stop\n``

see here: https://docs.allthingstalk.com/developers/api/udp-messaging/


.. image:: _images/13_udp_packetsender.png


The commands are defined in: https://github.com/magdesign/PocketVJ-CP-exh/blob/master/sync/commandmapping.sh


Ask if you need more control commands and I will add them or edit the file by yourself.



TCP Control
***********

You can control the PocketVJ with TCP commands.

Standard port for http:// commands is port ``80``

Its your decision which tool you use to send the commands,
here is an example using curl via terminal to control a PocketVJ with the IP: 2.0.0.100

``curl -s http://2.0.0.100/backend.php/?action=stop``

IP://X.X.X:X/backend.php/?action=..............

For more commands check backend.php
Every function is controllable via TCP!


