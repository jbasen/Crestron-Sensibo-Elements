# Crestron-Sensibo-Elements

Note - There is currently a bug in the API for the Sensibo Elements.  The AQI
value that is retrieved through the API doesn't match the value that you will
see in the Sensibo App.  Sensibo is aware of this issue and it should be addressed
shortly.

This module obtains measurements from a Sensibo Elements on a Crestron 3-Series or 
4-Series Processor.  

The first step in using this module is to obtain an API Key.  To accomplish 
this you will need to use your username/password and login to the Sensibo 
web site.  There is a login link in the menu at the bottom of the main 
page of the web site.  You will then be presented with a screen that shows 
you your Sensibo devices.  In the upper left hand corner of the screen is 
a menu icon and selecting it will present you with an option to create an 
API Key.

Next you will need to obtain the ID of your Sensibo Elements.  Currently you
must enter the following https string in a browser:

https://home.sensibo.com/api/v2/users/me/pods/?fields=*&apiKey=XXXXX

where XXXXX is your API key obtained above. Next copy the returned json and
paste it into a json formatter such as

https://jsonformatter.curiousconcept.com/

Once you have formatted the json so it is more readable you will have to
locate the device ID of your Sensibo Elements.

Once Sensibo catches up you will be able to retrieve the device ID from the
Sensibo web site. First you will need to login to the Sensibo web site. Then,
in the lower right corner of the square that represents you Sensibo Elements
 is a 3 dot menu icon.  Pressing this displays a drop down
menu.  Press the "Advanced" option on the menu and then choose "Advanced Info".
The UID is the device ID of your Sensibo Elements.

Copy the API Key and the UID into the API_Key and Device_ID paramters of this
module. 

Inputs
Initialize                 - Must be pulsed to initilize communications
Refresh                    - Will referesh the status of feedback signals.
                             by the Sensibo Elements

Outputs
Temperature_FB             - Current Temperature
Feels_Like_FB              - Current Feels Like Temperature
Humidity_FB                - Current Humidity
TVOC_FB                    - Current Total Volatile Organic Compounds Level
CO2_FB                     - Current CO2 Feeback
PM25_FB                    - Current PM25 Particulate Level
ETOH_FB                    - Current Ethanol Level
IAQ_FB                     - Current Indoor Elements Quality
Temperature_Unit_FB        - Either C or F depending on whether the Temperature_FB
                             and Target_Temperature_FB are in Celsius or Fahrenheit


Parameters
Device_ID                  - UID of device to be controlled obtained
                             from the Sensibo web site
API_Key                    - API Key from Sensibo web site
Temperature_Unit           - C or F.  
Debug_Msg_Output           - Where to send debug messages
                             0=None, 1=Console, 2=Error Log, 3=Both 
