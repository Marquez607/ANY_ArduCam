# ANY_ArduCam
Hardware Agnostic Driver for using the OV2640 based ArduCam. This library is currently friendly to low level embedded platforms. This is currently not a full featured as the original ArduCam arduino library supports many camera platforms as well as has other image format. Currently the only support image format for this platform is 
JPEG. Other functionality should be easy to add. This code was adpated from their ESP32 example. 

## Why?
Currently, all of the available libraries for this camera are all platform specific (arduino, ESP32, raspberry pi) so there would be a significant amount of dev effort involved to port over to another platform. With this repo, I've partially made it usable on any system via funtion pointers so that the end user only needs to provide hardware specific functions in order to get it working on their MCU.

## Original Library
My code was adapated from the below repo
https://github.com/ArduCAM/ArduCAM_ESP8266_UNO

## Demonstrated Embedded Platforms 
* TI CC3235 ( Wifi SoC) 

## How to Use 
