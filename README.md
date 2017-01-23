Raspberry PI Smart Home
==========
Home automation with Raspberry PI 3, Node JS, Raspbian OS & ms-gpio.js

## Setup

### Hardware
1. Raspberry Pi 3 model B, with at least 16gb memory card which must be preloaded with Raspbian OS. For installing Raspbian OS on memory card, you can refer to website https://github.com/raspberrypi/noobs/blob/master/README.md
2. 5V 10A 2 Channel Relay Module <br/>
<img title="5v 2 Channel Relay Switch" width="250" alt="Screenshot 5v 2 Channel Relay Switch" src="https://github.com/mayankmania/smarthome/raw/master/UIPics/relayswitch.jpg"/> <br/>
Relay switch shown in the above picture is a two channel relay module, only two eletrical devices can be controlled with this. For controlling more devices, you can go for 4,6 or 8 channel relay switch<br/>
3. Circuit creation, each device is controlled by set of GPIO pins & relay switch channel. Depending upon the number of eletrical devices we want to control, those many number of GPIO pin must be connected to a **channel/input** on a relay switch. Next step is to create a circuit between relay switch and eletrical device, this can be done by keeping the live current passing as in input, with output coming from relay switch to the eletrical device. <br/> Below circuit diagram, shows a connection between Raspberry PI 3, Relay Switch and an Electrical Appliance 
<br/>
<img title="Cicuit Diagram" alt="Cicuit Diagram" src="https://github.com/mayankmania/smarthome/blob/master/UIPics/circuit.png"/> <br/><img title="5v 2 Channel Relay Switch" alt="Screenshot 5v 2 Channel Relay Switch" src="https://github.com/mayankmania/smarthome/blob/master/UIPics/rs_2.jpg"/> <br/>
Please note, how we have created circuit between **relay switch** and an **electrical appliance**. You need to ensure that the **live current wire** from the plug goes directly into the relay switch **Common/Middle** electrical contact; and it comes out **either** from **Normally Connected** or **Normally Open** electrical contact, but not both at the same time. Also **neutral wire** from the plug must be directly connected to the electrical appliance.<br/>

##### Default GPIO Pin & device Mapping
1. <b>Note</b>: While interacting with the GPIO pin, Raspberry Pi(BOARD/physical) pin number must be passed. Please see [this page](http://elinux.org/RPi_Low-level_peripherals) for more details. On Raspberry PI 3 device, physical pin differs from BCM numbering which is internally used
2. Each device is controlled by a specific GPIO pin, hence configuration of the eletrical device and pin mapping must be done in advance
3. Current application shows a demo which can work with 4 devices, but it can be extended to more appliances
4. GPIO pin mapping of 4 devices are given as follows:
 * Physical Pin 15 maps to GPIO22 => fan
 * Physical Pin 16 maps to GPIO23 => bulb
 * Physical Pin 18 maps to GPIO24 => washer
 * Physical Pin 19 maps to GPIO10 => tv
 <br/><img title="GPIO Numbering" alt="GPIO Numbering" src="https://github.com/mayankmania/smarthome/blob/master/UIPics/pin_numbering.png"/> <br/>
As shown in the above picture, we are always going to control the GPIO by using it physical number highlighted in the middle using circle

### Software
1. Node.js 
2. MS-GPIO node module
3. HTML5/Bootstrap
4. Linux/Rasbian
5. Putty, can be used for remotely connecting terminal session with Raspberry PI
6. Raspberry PI Static IP : To access the node application hosted in Raspberry PI device, we need to provide a local static IP to it. This will allow us to access the smarthome application by providing the IP from mobile/PC or any other device which are part of LAN(I had used **192.168.0.7** as my static IP for accessing the application, you can choose any other available IP)
 
### Access Rights
1. Super/root user privileges

## Running the project
1. Start your Raspberry PI device
2. To work with Raspberry PI , you need to have a super user access, **sudo -i** command can be used for the same
3. Navigate to the **Desktop** folder, clone/download this project in your Raspberry PI device
 ```
 sudo -i
   
 cd /home/pi/Desktop
   
 git clone https://github.com/mayankmania/smarthome.git
 ```
4. Now navigate to the path /home/pi/Desktop/smarthome run the node server.
   
 ```
 cd /home/pi/Desktop/smarthome
   
 node index.js
 ```
 If everything works well, your application must be hosted locally on 9000 port
5. From any device(mobile/PC) which is connected to same LAN as Raspberry device, enter http://192.168.0.7:9000 in the browser. It should present a HTML based UI, which will provide you a list of devices along with their current status(running/stopped). You can now control each device by clicking on the play and stop button provided in front of each device 
<br/>
**Mobile View**
</br>
<img title="GPIO Numbering" alt="GPIO Numbering" src="https://github.com/mayankmania/smarthome/blob/master/UIPics/mobile.png"/> <br/>
**Desktop View**
<br/>
<img title="GPIO Numbering" alt="GPIO Numbering" src="https://github.com/mayankmania/smarthome/blob/master/UIPics/Desktop.png"/> <br/>
