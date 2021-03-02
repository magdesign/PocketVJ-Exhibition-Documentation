
DISPLAY
********




.. image:: _images/12_CP_display.png


INFO
******

**Actual Resolution** => See what resoultion we are currently displaying

**Possible** => Ask the attached device which resolution it is capable of

RESOLUTION
************

**Default** => Everytime we boot, we ask the attached device for the resolution


**1920 x 1080** => Force the PocketVJ to always output in this resolution (needs reboot)

.. note::
    - Mapper will only work up to 1920 x 1080 resolution and default flip setting
    - If forced to 1920 x 1200 you may encounter glitch issues!



ROTATE & FLIP
**************

Rotate or flip the output => Needs reboot


SLEEP
******

Set the display to sleep or wakeup




PROJECTOR
**********

.. note::  
    - Make sure to connect a PJlink compatible projector via rj45 cable
    - Default ip is: 192.168.2.254
    - For custom ip's make sure to stay in the same range as the PocketVJ's rj45 ip
    - Disable password and powersettings on projector
    - When coming from a CP older than 4.0.3, make sure to hit "Factory Reset" to change to the new projector control system

.. image:: _images/12_CP_projector.png

see video tutorial: https://video.pocketvj.com/AVideo/video/25/pocketvj-pjlink-a-projector



If you need a pjlink password, edit:
``/home/pvj/.local/share/pjlink/pjlink.config`` and add a new line containing:
``password = yourpassword``

(Password input field coming in next CP release)