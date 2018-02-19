##Jane Cleland-Huang Drone Class
1. Attach JST connect to UBEC
2. Attach Dupont connectors to serial cable
3. Attach everything to Iris
4. Boot Pi and ssh in
5. Configure Pixhawk

###  6. Test connection
- $ mavproxy.py --master=/dev/ttyS0 --baudrate 57600 --aircraft MyCopter
- Get Iris's current basics 
- Change the flight mode and confim change in QGrounControl
- python -i testconnection.py
- Explore log file:

### 7.(optional) Looking at flight logs:
There are 2 types of log files created by Ardupilot.....
Two ways of trying this:
####Opt1: MAVExplorer is installed on the pi
ssh in forwarding the xserver
$ MAVExplorer.py <*.tlog>
- Check the log at: MyCopter/logs/<DATE>/flight1/flight.tlog

####Opt2: Install MAVExplorer on your local machine
- Copy the log to your own computer and install it locally
- Install instructions are [here](http://ardupilot.org/dev/docs/using-mavexplorer-for-log-analysis.html)

####Tips
$  mavproxy.py --h


### 7. Create default mavproxy setup


### 7. Exercise
- Write a python script that runs on boot up and changes the failsafe settings on the Pixhawk, print results to file to prove it ran on boot.

- Explore more examples at [DroneKit](http://python.dronekit.io/examples/index.html#example-toc)

### 8. Extended exercise
- Install nginx on the Pi and monitor a parameter (pitch/roll/yaw/baromter/GPS/etc from a webpage







































































































































































































































































