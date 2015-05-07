#Blog, How - To
 

The buzzword being IoT, we wanted to build something that everyone can easily understand and build themselves, and of course include both hardware and software. The first thing that came to our mind was the Raspberry Pi and the Arduino, but we wanted to try out something different. Something that is easy to build, that is viable and easily scalable. We decided on combining Atmel MCU and PubNub to build a real time temperature sensor demo. 


 
 
 <insert image/gif of the UI built by Tomomi>
 
 
## What you are building

The Atmel temperature sensor enables monitoring temperature from anywhere in the world at low-latency, and provide updates in realtime whenever the temperature changes. 
The temperature sensor will measure the ambient temperature and publish it as a data stream to a channel in the PubNub network. A web browser that subscribes to this channel displays the data stream. 

### The concept : 

![alt text](images/demofunctionality.png)

1. We are using the Atmel I/O1 Xplained Pro sensor that measures the temperature. 
2. This is connecting to the Wi-Fi using the ATWINC1500 module which can talk to any device on the internet.
3. The PubNub code running on the Atmel chip enables us to publish the temperature information in real time to any one subscribing to the same channel as a real time data stream.
4. Through the [pubnub developer console](http://www.pubnub.com/console/), you can receive this stream of information from as many sensors as you like in real time. 
 

### What do you need

####**Hardware**
	
1. **ATWINC1500** module. This is a Wi-Fi black box that contains the Wi-Fi stack, the TCP stack and the TLS stack.
2. **ATSAMD21-XPRO** host MCU board. 
3. Atmel **I/O1 Xplained Pro** for sensor and SD-card input to host MCU
4. **OLED 1 Xplained pro** to provide the display on the chip. 
	
	

####**Software**

1. Windows PC.
2. Sign up for [PubNub](https://www.pubnub.com), and get a set of publish and subscribe keys. 
3. Install Atmel Studio 6.2
4. Install updates to Atmel Studio as suggested during installation 
5. Install terminal software like putty or teraterm (I have used putty)
6. Download the files from INSERT LINK TO DROPBOX HERE.
7. Open the PubNub example solution file. 

** A prerequisite is that you upgrade the firmware for SAMD21 using the .bat file provided with the PubNub Atmel example before you run this demo. Make sure no other software like putty or teraterm is using the com port). Close atmel  studio and the putty terminal. **


### Connecting the hardware in the right way : 

1. Connect WINC1500 XPRO board to SAMD21 XPRO connector EXT1
2. Connect IO1 XPRO board to SAMD21 XPRO connector EXT2
3. Connect OLED1 XPRO board to SAMD21 XPRO connector EXT3
4. Connect SAMD21 XPRO to a free USB port on your PC (make sure no other USB port on your PC is in use)
5. Connect the power to the port that says “DEBUG USB”. 
	
	
![alt text](images/FullSizeRender.png)	
	
### The Software (need to add images)

1. Open the PubNub example solution on Atmel Studio and open main.h.
2. Include the following lines: 
	
```
#define TEST_MODE_SSID "Enter-your-SSID"	(choose THE Wi-Fi access point you want the chip to connect to)
#define TEST_MODE_PASSWORD "Enter-the password-for-the-SSID" (enter the password for the same Wi-Fi connection)
#define TEST_MODE_WITHOUT_PROVISION
```
3. In main.c, add the channel name and pub, sub keys. 
4. Build (F7 / Build -> build solution), run(continue/ green arrow/ F5/ debug -> continue).
5. Open [PubNub console] (http://www.pubnub.com/console/), use the same channel name and pub,sub keys as in the code and SUBSCRIBE. 
6. If all is well, you should see a constant stream of messages in the following format : 
	<Atmel_Pubnub> {"columns":[["temperature","55"]]}
	
![alt text](images/fullsetup.png)	

### Visualizing the data stream

[](link to TOmomi's UI)

Tomomi (ADD A LINK TO HER BIO), built this extremely pretty visual for the demo. It mocks nursery or greenhouse monitor(a very typical use case of using temperature sensors), instead of just displaying raw data off the sensor. This interface is running on a browser. The technology behind is quite simple, using [PubNub JavaScript APIs](https://www.pubnub.com/docs/javascript/javascript-sdk.html) to subscribe the data sent from the Atmel chip.

This interface is accessible from anywhere in the world with any devices- mobile phones, tablets, and any smart devices, as long as you have a web browser.
The main purpose behind this is to present information in most efficient manner without losing its accuracy.

In this scenario, the UI shows the current temperature, also a simple line graph, updating in **real time** so that you can tell the relative changes of the temperature, raising and dropping.

This particular data is simple, but when you have multiple, more complicated data, data visualization plays more crucial role. 



### Final note 

This demo is read-only, but in reality, you want to develop solid products that lets your users monitor *and* control, i.e, **bidirectional communication** between devices. For instance, if you have a smart A/C, not only monitoring the current room temperature, but you need to make it controllable from a remote devices. With the power of [PubNub APIs](https://www.pubnub.com/developers/), you can achieve this with no hassle. 
I hope I am leaving you guys with enough excitement to try this demo out, and also build cooler ones. Let me know at @bhavana1110. 



