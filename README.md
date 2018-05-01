Installation and use of iTPMS based on CANBus messages for wheel speed in T7 cars with ESP/TCS

Installation of Arduino IDE and the extra libraries

1.	Download Arduino and install the stable version of Arduino IDE for your operation system:
https://www.arduino.cc/en/Main/Software
Accept all standard setting and install all of the required add-ons
2.	Start Arduino 
3.	Open the attached sketch (.ino)
4.	In File>Preferences find the empty field called “Additional Boards Manager URL” and paste this link there: http://arduino.esp8266.com/stable/package_esp8266com_index.json
5.	Open board manager from Tools>Board:Arduino/Genunino Uno>Boards Manager
6.	Search for esp8266, it will find only one result, click install
7.	Go to https://github.com/Seeed-Studio/CAN_BUS_Shield, click download or clone and download the zip file. Then extract it here: C:\Users\YourUserNmae\Documents\Arduino\libraries
10.	Replace the mcp_can.h and mcp_can_dfs.h files in C:\Program Files (x86)\Arduino\libraries\CAN_BUS_Shield-master with the ones provided in this project
11.	Go to Tool>Board and select NodeMCU 1.0
12.	Go to Tool>Board and select the appropriate com port
13.	Go to Tool>Board and select the highest upload speed
14.	Restart Arduino IDE
15.	Open the Sketch and click the upload button (right arrow). If everything went well it will start to flash the logger.

If you have a normal Arduino board instead of ESP8266, you can skip steps 4-7

Usage:
The main idea is that the bluetooth dongle has prev/next buttons as well as play/pause/answer phone buttons. The buttons work by grounding the other connection, so we can use a microcontroller to ground them instead. I used my favorite esp8266+mcp2515 combo from this topic:
http://www.trionictuning.com/forum/viewtopic.php?f=46&t=6831
We need microcontroller and canbus, since the steering wheel buttons work by providing different resistance, the SID measures it and trasforms it to CAN messages on the I-Bus. 
Hardware connections:
- Connect the ESP and the MCP as in the logger topic
- Connect D0 on the ESP to the active lead of the Play button on the bluetooth
- Connect D1 on the ESP to the active lead of the Next button on the bluetooth
- Connect D2 on the ESP to the active lead of the Prev button on the bluetooth
- Connect CAN H and CAN L from the MCP to the back board of the headunit (they are clearly marked)
- Connect the power lined of the ESP, MCP and Bluetooth together and put some kind of filter cap on the bluetooth device (optional)

Handsfree specific:
Unsolder the wires of the microphone and solder longer leads on it. Then stick it in on of the holes of the face plate like so:
![Microphone](https://preview.ibb.co/kB1D2c/IMG_20180224_152904.jpg)

Video demo: https://www.youtube.com/watch?v=of_FWERjKOs
[![Video demo](https://img.youtube.com/vi/of_FWERjKOs/0.jpg)](https://www.youtube.com/of_FWERjKOs)
