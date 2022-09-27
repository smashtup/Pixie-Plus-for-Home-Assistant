# Pixie Plus for Home Assistant 

First, a warning. Please only use this code if you know what you are doing. Installation of this integration requires knowledge and is not straight forward. The integration was only tested on my system and is not sure to work on other systems without modifications. It is not supported in any way. 
==========================

This is a Pixie Plus integration for Home Assistant. Pixie Plus is a line of smart light products made by an Australian company called SAL. The
integration only supports light switches' on and off functionality. There is no support for color or brightness settings (I don't have any lights with
dimmers or colors). It also doesn't support built in groups, scenes, schedules or timers but I assume that you would use Home Assistant for those
functions any way. It only works if you have a Pixie Plus Hub and doesn't support Bluetooth capabilities. It requires the cloud because of the way they implemented their system (no direct access to the local hub IP, only through their servers. 

I am not a programmer, and my code is messy and inefficient. I only wrote this because I didn’t like the idea that I needed SmartThings as a mediator between HA and the lights.  


Installation: 

The easy part – just copy the files into the custom_components folder in HA and restart HA. You can then add the integration from the UI by clicking on the 'add integration' button under Settings / Devices and Services / Integration and look for Pixie Plus. It will then ask you for your Pixie Plus credentials (username and password) and 3 other numbers (see below). 

The difficult part – to use the integration you will need 3 parameters that are quite difficult to get. They are called ApplicationID, InstallationID and JavaScriptKey. I assume they are generated by the Pixie Plus client (i.e. mobile app) and are needed for communication with the server. I came across them when I was analyzing the data between the app and the hub for writing of this integration. I was also able to find the first two in a file called “ALL_SHARE_DATA.xml” using a rooted virtual android phone in the data/data/pixie_plus direcotry, but this doesn’t provide you with the JavaScriptKey.  

To find all the numbers you will need to use a mitmproxy and a rooted virtual android phone (I used Android SDK). You will need to upload to the phone the mitmproxy CA certificate as a system (not user) certificate. This link is very helpful: https://docs.mitmproxy.org/stable/howto-install-system-trusted-ca-android/. Once all this is done you will be able to see the communication between the client and the server and easily located the needed parameters (I suggest using mitmweb). There may be an easier way to find those parameters so let me know if you discover it.  


Usage: 

Once you provide all the needed credentials, the integration should work, and you should see new light entities. However, I can’t guarantee it will work. Feel free to use, modify and add to the code as needed. I may be able to answer occasional question (if I know the answer) but generally won’t have much time to spend on that. 
