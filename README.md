# 1. esp_Odom
## Install Arduino IDE in Jetson Nano
```
git clone https://github.com/JetsonHacksNano/installArduinoIDE.git
cd installArduinoIDE
./installArduinoIDE.sh
sudo reboot
sudo shutdown -h now
```
Plug the ESP into the USB port of your Jetson Nano.

https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

## Dependency for arduino
  ```
  sudo apt-get update
  sudo apt-get install ros-melodic-rosserial-arduino
  sudo apt-get install ros-melodic-rosserial
 ```
create a libraries folder inside arduino folder and then
  ```
  cd ~/Arduino/libraries
  rm -rf ros_lib
  rosrun rosserial_arduino make_libraries.py <path of arduino libraries>
  ```

## Install

Use the following commands to download and compile the package.

```
cd ~/catkin_ws/src
git clone https://github.com/Saifali4604/ros_robo_jetson
```
Open your <work_space>/src/ros_mpu6050_arduino/ and copy "ros.h" and "Arduinohardware.h" and paste it in Arduino/libraries/ros_lib/

[delete the previous file in that location]
now open new terminal 
```
cd catkin_ws
catkin_make
gedit ~/.bashrc
```
and paste ```source ~/catkin_ws/devel/setup.bash``` at the last line
## Arduino code
Connect Your Arduino with mpu6050 board to your PC And upload the code given in this repository.
**Download Mpu6050 lib by Electronicscat**(https://github.com/ElectronicCats/mpu6050)
```
sudo ls -l /dev/ttyACM* 
sudo chmod 777 /dev/ttyACM0
```
or
```
ls -l /dev |grep ttyUSB
sudo chmod 777 /dev/ttyUSB0
```
**Note:** Always use Serial.begin(500000) in the code

## Run the package
1. Start the ROS master
```
roscore
```
2. Run the launch file:
```
roslaunch jetson_nanobot.launch
```
