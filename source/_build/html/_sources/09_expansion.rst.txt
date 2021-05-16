.. _expansion:


EXPANSION
=========

This section holds all functions for the expansion board:

.. image:: _images/09_CP_expansion.png




PIR SENSOR
**********

With the PIR Sensor attached, you can create an interactive installation which triggers a random video as soon as the sensor detects motion.

    - This works with *.mp4 videos and/or *.mp3 audios
    - Copy the loop (default, standby) video to the media/internal/pir/loop folder
    - Copy the trigger videos (can by any amount) to the media/internal/pir/trigger folder


see video tutorial: https://video.pocketvj.com/AVideo/video/13/pocketvj-exhibition-pir-sensor


SENSITIVITY
***********

Adjust after how many movements the video will be triggered.

    - low => 30 movements
    - medium => 20 movements
    - high => 12 movements


STILLSHOT
*********

Set the picture which will appear for approx. 1s when the loop file stops and the trigger file starts to play.

CONNECT PIR
***********

.. image:: _images/09_pir_connect.png


If you have trouble with the pir sensor, there is a testscript which you can run from terminal to check what its states::

    python /var/www/sync/startpirtest.py

Factory standard the sensor is set to a distance range of ~5m, if you need another range, you can adjust this directly on
the sensor. Gently unscrew it with a hex key and then change the range with a screwdriver:

.. image:: _images/09_pir_adjust.png


Its also possible to connect Ultrasonic sensors which can be mounted behind materials, ask me for more info.


BUTTONS
*******


see video tutorial: https://video.pocketvj.com/AVideo/video/8/pocketvj-exhibition-button-connecting



CONNECT BUTTONS
****************

.. image:: _images/09_button_connect.png


SENSORS
*******

**Temperature** => see temperature/humidity from temperature sensor.


Attached a DHT11 Temperature/Humidity Sensor as shown in the diagram.

- **+5V** goes to PIN13
- **GND** goes to PIN1
- **S** Signal goes to PIN5


.. image:: _images/09_temperature_connect.png



**IR Sender diode** => See :ref:`irremote`

- **+5V** goes to PIN13
- **GND** goes to PIN1
- **S** Signal goes to PIN6


.. image:: _images/09_ir_connect.png
