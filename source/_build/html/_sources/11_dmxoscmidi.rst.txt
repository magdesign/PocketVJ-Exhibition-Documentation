
DMX OSC MIDI
=========================

This section is for recording and playback DMX, ArtNet, sACN and remote controlling via OSC, Midi, UDP or DMX

see video tutorial for recording/playback: https://video.pocketvj.com/AVideo/video/37/pocketvj-exhibition_dmx_in_out_recording

see video tutorial for remote controlling: https://video.pocketvj.com/AVideo/video/14/pocketvj-exhibition-artnet-dmx-remote-control



OLA
*****

.. image:: _images/11_CP_dmx_osc_midi_ola.png


**Start** => Start OLA, this is necessary to activate DMX, ArtNet, sACN


**Open Panel** => Opens the seperate control panel to create Universes

**Daemon on** => Enables ola always when PocketVJ boots, (turn off when not used!)

**Daemon off** => Turns off ola and the olad daemon

DMX Remote
**********

.. note::
    - Create the remote listener on universe 15. 
    - If you send control commands via ArtNet over RJ45 make sure not to be connected via Wifi and having a DMX Monitor in the browser open, since this would give you a loop and will end in weird behavior.


**DMX Remote ON** => enables the DMX remote control on Universe 15

**DMX Remote OFF** => disables the DMX remote control on Universe 15

find the remote commands here: https://raw.githubusercontent.com/magdesign/PocketVJ-CP-exh/master/sync/artnet.conf




OLA PANEL
*********

Add a Universe:

.. image:: _images/11_ola_panel1.png

Select Universe ID and device:

.. image:: _images/11_ola_panel2.png

Save:

.. image:: _images/11_ola_panel3.png


Open Monitor:

.. image:: _images/11_ola_panel4.png

  
..




DMX RECORDER
************

.. image:: _images/11_CP_dmx_osc_midi_recorder.png

**Stop Recording** => Stop Recording

**REC Show** => Record Show

.. note::
    REC Show01 will record on Universe 1-30, the others on Universe 1-20


Universe
*********

**Change to 1** => change the recorded track to Universe 1


DMX PLAYER
***********


**1.0 Entry field** => Here you enter the delay time in seconds.milliseconds until the audio/video starts

**Set Delay** =>  Set the entered delay time

.. note::
    The delay will be used for all recorded shows the same, if you need them seperate, write me an email

    ArtNet playback is limited to 4 Universes by firmware


**Show01** => Plays DMX Show01

**Show01/01_Audio** => Plays DMX Show01 together with 01_audio.mp3

**Show01/01_Video** => Plays DMX Show01 together with 01_video.mp4


ArtNet/DMX Remote Control
***************************

``1    128-255 `/var/www/sync/stopall```

See all commands here: https://github.com/magdesign/PocketVJ-CP-exh/blob/master/sync/artnet.conf


Autostart to OSC/ArtNet/UDP


OSC
*****

.. image:: _images/11_CP_dmx_osc_midi_ola_oscmidi.png


**Start Listen** => Starts to listen for OSC commands on port ``9876``

List of OSC commands: https://github.com/magdesign/PocketVJ-CP-exh/blob/master/sync/osc_control.js 


**Download TouchOSC** => Download the TouchOSC layout contributed by Cornelius Henke:
https://github.com/magdesign/PocketVJ-CP-v3/raw/master/sync/PocketVJ_OSC.touchosc 


.. image:: _images/11_osc_app.png
      :width: 300




To send OSC commands under Debian Linux 
(sudo apt install liblo-tools):

``oscsend 192.168.2.100 9876 /pause``

or sendosc for all platformas: https://github.com/yoggy/sendosc

``sendosc 2.0.10.102 9876 /testscreen``


MIDI
*****

see video tutorial: https://video.pocketvj.com/AVideo/video/9/pocketvj-exhibition-midi-control

List of Midi commands: https://github.com/magdesign/PocketVJ-CP-exh/blob/master/sync/midicontrol.cfg

You can add more Midi commands yourself in /var/www/sync/midicontrol.cfg
or kindly ask me to add the features you need.


MIDI RECORDER
***************
This is new function, not very tested yet, but should work as expected.

When hitting Record it will record all incoming midi signals and on play it should playback them. Currently only working when your usb-midi device is on number:20 , should be on default if no other usb thing is plugged in.



