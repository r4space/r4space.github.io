# Jane Cleland-Huang Drone Class 02/18
## Controling a Pixhwak with a Pi3
### Steps:
1. Add 5V usb supply 
2. Attach dupont connectors to serial cable
3. Test powering up and loging in to the Pi
5. Configure Pixhawk
3. Attach the Pixhawk to the Pi


### Step1: Add 5V usb supply
Use the crimp tool to attach the JST connector to open UBEC input leads making sure to have the correct orientation for the 12V supply coming out ofthe base of the Iris
(red to red and black to black)

![Image of JST Connector](https://r4space.github.io/docs/images/JST.jpeg)


![Image of UBEC](https://r4space.github.io/docs/images/UBEC.jpeg)


### Step2: Add Dupont connector to serial cable
Again strip and crimp the connector to the open end of the cable taking care to get the pin order correct

![Image of Pi3 Pinout](https://r4space.github.io/docs/images/rp3_pinout.png)
![Pixhawk Serial Pinout](https://r4space.github.io/docs/images/PHSerial.png)


### Step3: Power up and connect to the Pi
- i] Insert microSDCard into Pi3 (noting the number on it)
- ii] Connect UBEC to JST connect underneath Iris and the USB to the Pi3
- iii] Connect the Iris battery to power up the Pi
- iv] Connect your computer to the local WLAN:
    -- SSID: NDSUAS
    -- PSWD: NotreDame
- v] ssh pi@Pi<number>.local
    --PSWD: NotreDame
- vi} Shutdown the Pi 
    $ sudo shutdown -h now

### Step4: Configure the Pixhawk Serial Port
- i] Install [QGroundcontrol](http://qgroundcontrol.com/downloads/) on a local machine
- ii] Connect a USB cable between the microusb port on the side of the Iris to a local machine
- iii] QGC should connect to the Iris automatically
- iv] Click on the gears symbol and go to the bottom where the parameters option is
- v] Under parameters, search for:
  -- "SERIAL4_PROTOCOL" and set it to Mavlink2
  -- "SERIAL4_BAUD" and set it to 57600
- vi] Unplug the Iris


### Step5: Connect Pi to Pixhawk
- i] Unscrew the top of the Iris
- ii] Insert DF13 connect (serial cable) into "Serial 4/5" port
- iii] Connect Dupont connect to Pi3 Serial port header
- iv] ssh into pi and run 
    $ mavproxy.py --master=/dev/ttyS0 --baudrate 57600 --aircraft MyCopter
    If it fails to connect go back and check all connections and the setting changes you made
- v] Once successfully connected you should see:
    >> MAV  //Tab to see command options
- vi] Connect to QGC again via the external USB cable and monitor settings as you change them via the ssh and the Pi.  
    -- Eg: Change flight modes:
        >> MAV mode auto    //will change to auto flight mode if not already in it          (See documentation [here](http://ardupilot.org/plane/docs/flight-modes.html) on available flightmodes)

- v] Close Mavproxy and now try interacting via a python script.  Start with the test connection script available in ~/Desktop/
    $ python -i testconnection.py

### Step6: Flight logs:
The pixhawk creats 2 types of log files, dataflash and telemetry logs (.tlogs).  both are in a binary format requiring an injestor to interperest them.
(see the [docs](http://ardupilot.org/copter/docs/common-downloading-and-analyzing-data-logs-in-mission-planner.html) for more details)

When you ran mavproxy.py a t.log file was created, you can either examin this on the Pi (by exporting X) or by copying it to your local machine and doing 1 of a number of things:
     Check for the log at: MyCopter/logs/<DATE>/flight1/flight<number>.tlog

If you have a windows machine, MissionPlanner has good tools for view and exporting the logs to ASCII formats.  However, if you do not run Windows, or wish to create plots for reports/later reference etc MAVExplorer is very useful.  

If you wish to install MAVExplorer on your own local machine, follow the instructions [here](http://ardupilot.org/dev/docs/using-mavexplorer-for-log-analysis.html)

Finally if you do not wish to install MAVExplorer, it is already installed on the Pi, you will just need to forward X over shh as it's a GUI application

Whichever avenue you take, once installed:
$ MAVExplorer.py <*.tlog>


### 7. Exercise
- Write a python script that first checks and then changes one of the [failsafe](http://ardupilot.org/copter/docs/failsafe-landing-page.html) settings on the Pixhawk.

- Explore more examples at [DroneKit](http://python.dronekit.io/examples/index.html#example-toc)
    -- Note: Dronekit repo is already downloaded to the Pi under ~/Desktop/


### 8. Extension exercise (optional)
- Install nginx on the Pi and serve parameters (eg pitch/roll/yaw/baromter/GPS/etc) from a webpage for remote monitoring over wifi







































































































































































































































































