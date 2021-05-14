

.. _irremote:


IR REMOTE LIRC
**************

Using lirc to remotely control devices with IR (infrared).

PocketVJ Exhibition Image 4.0.7 or older do following steps:

First uninstall the out of date  lirc version with::

 sudo apt-get purge lirc
 sudo apt-get autoclean


Then install the special patched version (needs CP 4.0.6 or newer) with::

 sudo apt-get install -y /var/www/sync/debs/liblirc-client0_0.9.4c-9_armhf.deb
 sudo apt-get install -y /var/www/sync/debs/liblirc0_0.9.4c-9_armhf.deb
 sudo apt-get install -y /var/www/sync/debs/lirc_0.9.4c-9_armhf.deb``


This will take a few minutes.


After comnpletion, edit the .conf file to enable sending::

 sudo nano /etc/lirc/lirc_options.conf

 driver          = default
 device          = /dev/lirc0


From here on the software is installed.
Now we need to enable the IR sender::

 sudo nano /boot/config.txt 
 
 dtoverlay=gpio-ir-tx,gpio_pin=4


Finally we copy the IR protocol file to the lirc config, I always store mine in::

 /var/www/sync/remotes/
 
 


In this example, the IR file made for U400 Livia Ultra Short Throw Laser Beamer::


 sudo cp /var/www/sync/remotes/laserbeamer.lircd.conf /etc/lirc/lircd.conf 
 


Connect the IR sender as documented in :ref:`expansion`.



Test it with (use a digicam to check if diode is flashing)::


 irsend SEND_ONCE laserbeamer KEY_POWER



Recording your own IR is way more complicated and will not be described here in detail, only some hints::

 sudo nano /etc/lirc/lirc_options.conf =>
 driver          = default
 device          = /dev/lirc1

 nano /boot/config.txt =>
 dtoverlay=gpio-ir,gpio_pin=18 #pin of receiver
 dtoverlay=gpio-ir-tx,gpio_pin=4 #pin of sender


 stop lircd.service =>
 sudo /etc/init.d/lircd stop

 test =>
 mode2 -d /dev/lirc1


 record =>
 irrecord -f -d /dev/lirc1 ~/lircd.conf

 nice tool to check =>
 sudo ir-keytable -c -p all -t

 Most important keys:
 KEY_POWER
 KEY_OK
 KEY_HOME
 KEY_MENU
 KEY_MEDIA (source select)
 
 KEY_VOLUMEUP
 KEY_VOLUMEDOWN
 KEY_MUTE
 
 KEY_UP
 KEY_LEFT
 KEY_DOWN
 KEY_RIGHT
 
 KEY_PLAY
 KEY_PAUSE
 
 KEY_F1 (focus+)
 KEY_F2 (focus-)
 
 KEY_F3 (keystone+)
 KEY_F4 (keystone-)
 

I ended up in listing the raw ir commands in terminal with::


 mode2 -d /dev/lirc1
 

 


and then writing my own config file like this::

    # Device(s) controlled by this remote:

    begin remote

  name  laserbeamer
  flags RAW_CODES|CONST_LENGTH
  eps            30
  aeps          100

  gap          108203

      begin raw_codes

          name KEY_POWER
             9059    4475     594     539     582     553
              569     541     597     535     590     545
              569     539     595     538     589    1655
              595    1675     570    1655     608    1655
              595    1675     569    1674     590    1655
              599    1671     570     539     595     538
              566     547     591     540     595    1651
              568     568     591     539     589     545
              569     540     595    1674     570    1674
              590    1658     593     518     609    1637
              614    1675     570    1653     610    1660


          name KEY_OK
             9063    2205     591

          name KEY_HOME
             9072    2205     589

          name KEY_VOLUMEUP
             9097    2174     585

          name KEY_VOLUMEDOWN
             9043    2233     582

          name KEY_F1
             9075    2221     566

          name KEY_F2
             9065    2206     590

          name KEY_LEFT
             9050    2229     591

          name KEY_UP
             9119    2159     585

          name KEY_DOWN
             9049    2228     562

          name KEY_RIGHT
             9057    2207     587

          name KEY_MEDIA
             9039    4485     586     545     560     575
              564     567     567     545     560     595
              543     567     568     564     541    1706
              564    1702     543    1699     539    1707
              568    1679     568    1697     540    1707
              567    1701     542     568     567     565
              563     551     565     567     567     565
              539    1707     568     565     539     595
              542     568     566    1702     551    1695
              561    1682     568    1701     543     567
              567    1685     558    1702     539    1707
      
          name KEY_PLAY
             9067    2227     568

      end raw_codes

    end remote

Which is extremely time consuming and frustrating work.