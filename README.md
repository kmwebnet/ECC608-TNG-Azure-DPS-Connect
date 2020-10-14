# ECC608-TNG-Azure-DPS-Connect

This communicates ATECC608A-TNGTLS secure chip from ESP32 and connects to Azure IoT Device Provisioning Service.        

for Azure IoT Hub Device Provisioning Service, check the [Azure IoT Hub Device Provisioning Service (DPS) Documentation](https://docs.microsoft.com/en-us/azure/iot-dps/)   

# Requirements

Platformio(PIO Core:5.0.1 PLATFORM: Espressif 32 1.12.4) with VS Code environment.  
install "Espressif 32" platform definition on Platformio  

you need to buy ATECC608A-TNGTLS and prepare downloaded manifest file from Microchip Direct.    
And register them to your Azure IoT Device Provisioning Service prior to use this code.       

# Environment reference
  
  Espressif ESP32-DevkitC  
  this project initialize I2C 1 port   
  pin assined as below:  

      I2C 1 SDA GPIO_NUM_16  
      I2C 1 SCL GPIO_NUM_17  
       
  ATECC608A-TNGTLS(on I2C port 1)   

# Usage  

"git clone --recursive " on your target directory. and you need to change a serial port number which actually connected to ESP32 in platformio.ini.    

move to target directory (where you cloned this project)     

extract device cert from manifest file by using "manifestdecoder.py" python script.
before you use this script, execute pip install python-jose[cryptography] .    
You will find device certificates PEM file in "certs" subdirectory.   

Register device certificates on Azure IoT Device Provisioning Service.     
Manage Connection -> Individual Enrollment    
for detail, check attached .docx file.   

replace definitions to your own in main.c    

#define EXAMPLE_WIFI_SSID ""  
#define EXAMPLE_WIFI_PASS ""  

replace definitions to your own in prov_dev_client_ll_sample.c

static const char* id_scope = "0XXXXXXXXXX";     

# Run this project

just execute "Upload" on Platformio.   

if it's success, you got on terminal as follows:

Provisioning API Version: 1.2.14  
Iothub API Version: 1.2.14  
common name: sn0123XXXXXXXXXXXX01  
Provisioning Status: PROV_DEVICE_REG_STATUS_CONNECTED  
Provisioning Status: PROV_DEVICE_REG_STATUS_ASSIGNING  
Registration Information received from service: XXXXX.azure-devices.net!  
Creating IoTHub Device handle  
common name: sn0123XXXXXXXXXXXX01  
Sending 1 messages to IoTHub every 2 seconds for 2 messages (Send any message to stop)  
IoTHubClient_LL_SendEventAsync accepted message [1] for transmission to IoT Hub.  
IoTHubClient_LL_SendEventAsync accepted message [2] for transmission to IoT Hub.  


# License

This software is released under the MIT License, see LICENSE.  
