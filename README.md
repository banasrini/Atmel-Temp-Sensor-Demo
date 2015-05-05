##Blog, How - To

### what are we building
In this blog, I will show you how to build a sophisticated but simple real time temperature sensor. Think of the possibilities; a weather reporter, a smart temperature monitor for your nursery or even,..   

For a while now, every time I think of IoT, I think of the Raspberry Pi and Arduino; nothing more, nothing less. To be honest, when I knew I had to work with an Atmel chip, I was nervous. If only I knew it wont take me more than a couple hours. Yes, its that easy, and I am going to teach you exactly how to build a smart temperature sensor.
 

### what you will need
**hardware**
	
	1. Atmel ATWINC1500 module mounted on ATWINC1500 Xplained Pro Extension
	2. ATSAMD21-XPRO host MCU board for driving the ATWINC1500 Xplained Pro Extension
	3. Atmel I/O1 Xplained Pro for sensor and SD-card input to host MCU
	Insert images.
		
**software**

	1. Windows PC.
	2. Install Atmel Studio 6.2
	3. Install updates to Atmel Studio as suggested during installation 
	4. Install terminal software like putty or teraterm (I have used putty)
	5. Download the files from INSERT LINK TO DROPBOX HERE
	
### Connecting the hardware to make sense

	1. Connect WINC1500 XPRO board to SAMD21 XPRO connector EXT1
	2. Connect IO1 XPRO board to SAMD21 XPRO connector EXT2
	3. Connect OLED1 XPRO board to SAMD21 XPRO connector EXT3
	4. Connect SAMD21 XPRO to a free USB port on your PC (make sure no other USB port on your PC is in use)
	5. Connect the power to the port that says “DEBUG USB”. 
	
### The Software

	1. open main.h and change the following : 
```#define TEST_MODE_SSID	(CHOOSE THE wifi name the computer is connected to)
   #define TEST_MODE_PASSWORD ( enter the password for the same wifi connection)
   #define TEST_MODE_WITHOUT_PROVISION
```

4. how to use PubNub or a UI to stream that data
5. how to scale this
6. practical use cases
7. what do yoiu needa to build tisdfh kfhj


http://www.atmel.com/devices/atwinc1500.aspx?tab=documents - documentation for the hardware