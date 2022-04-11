# ArduinoIDEcustomLauncher
In some linux systems ArduinoIDE has some problem accessing Arduino devices because of permission problems. This custom launcher helps with not having to re-establish device permissions every time you connect your Arduino to your computer.

There are a couple components to this. If you are using something like GNOME, you need to edit your ArduinoIDE's .desktop file like this: EXEC=gnome-terminal -e "bash -c 'xhost +;sudo bash /where_your_file_is/arduino-1.8.10/arduino;xhost -'"
This will make sure even though the Arduino IDE is running from the ROOT user (because our script runs it.) It will stil work. You can find your .desktop file in /usr/share/applications folder. If you don't know what a .desktop file is. Google it.

The way this script is designed, you need to copy the code in your "arduino" script and copy it to a new script you will create  named "arduino_start" in the same directory. arduino_start should contain the orginal code in the aruino script and the orginal script called "arduino" should be changed with this script. 

In the new arduino script you need to change the SCRIPT_PATH="/opt/arduino-1.8.10/arduino_start" part to wherever your arduino script directory is. This change needs to be made in lines 26 and 41. After that it should be ready to go.

Since this script runs the ArduinoIDE as root, some may consider it a security risk. But since you are probably using this on your personal computer, not on some big company's servers, it shouldn't be a problem. And if you don't close the software with the little x icon like you should, you should probably run the "xhost -" command just to be safe. Use at your own discretion
