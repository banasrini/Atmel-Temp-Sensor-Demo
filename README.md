#Blog, How - To
 

The buzzword being IoT, we wanted to build something that everyone can easily understand and build themselves, and of course include both hardware and software. The first thing that came to our mind was the Raspberry Pi and the Arduino, but we wanted to try out something different. Something that is easy to build, that is viable and easily scalable.


 
 
 <insert image/gif of the UI built by Tomomi>
 
 
## What you are building

The Atmel temperature sensor enables monitoring temperature from anywhere in the world at low-latency, and provide updates in realtime whenever the temperature changes. 
The temperature sensor will measure the ambient temperature and publish it as a data stream to a channel in the PubNub network. A web browser that subscribes to this channel displays the data stream. 

### The concept : 

![alt text](images/demofunctionality.png)

1. We are using the Atmel I/O1 Xplained Pro sensor that measures the temperature. 
2. This is connecting to the wifi using the ATWINC1500 module which can talk to any device on the internet.
4. The PubNub code running on the Atmel chip enables us to publish the temperature and light information in real time to any one subscribing to the same channel.
5. Through the [pubnub developer console](http://www.pubnub.com/console/), you can receive this stream of information from as many sensors as you like in real time. 
 

### what you will need
**hardware**
	
1. Atmel ATWINC1500 module mounted on ATWINC1500 Xplained Pro Extension
2. ATSAMD21-XPRO host MCU board for driving the ATWINC1500 Xplained Pro Extension
3. Atmel I/O1 Xplained Pro for sensor and SD-card input to host MCU
	
	

**software**

1. Windows PC.
2. Sign up for [PubNub](https://www.pubnub.com), and get a set of publish and subscribe keys. 
3. Install Atmel Studio 6.2
4. Install updates to Atmel Studio as suggested during installation 
5. Install terminal software like putty or teraterm (I have used putty)
6. Download the files from INSERT LINK TO DROPBOX HERE.
7. Open the PubNub example solution file. 
	

### Connecting the hardware so it works

1. Connect WINC1500 XPRO board to SAMD21 XPRO connector EXT1
2. Connect IO1 XPRO board to SAMD21 XPRO connector EXT2
3. Connect OLED1 XPRO board to SAMD21 XPRO connector EXT3
4. Connect SAMD21 XPRO to a free USB port on your PC (make sure no other USB port on your PC is in use)
5. Connect the power to the port that says “DEBUG USB”. 
	
	
![alt text](images/FullSizeRender.png)	
	
### The Software (need to add images)

1. First, we will need to do a firmware update - details on firmware update. 
2. open main.h and change the following : 
	
```
#define TEST_MODE_SSID	(choose THE wifi access point you want the chip to connect to)
#define TEST_MODE_PASSWORD (enter the password for the same wifi connection)
#define TEST_MODE_WITHOUT_PROVISION
```
3. In main.c, add the channel name and pub, sub keys. 
4. Build (F7 / Build -> build solution), run(continue/ green arrow/ F5/ debug -> continue).
5. Open [PubNub console] (http://www.pubnub.com/console/), use the same channel name and pub,sub keys as in the code and SUBSCRIBE. 
6. If all is well, you should see a constant stream of messages in the following format : 
	<Atmel_Pubnub> {"columns":[["temperature","55"]]}
	
![alt text](images/fullsetup.png)	


7. Open (link to tomomis demo) to view the data stream on abeautiful real time chart. 
6. practical use cases


http://www.atmel.com/devices/atwinc1500.aspx?tab=documents - documentation for the hardware