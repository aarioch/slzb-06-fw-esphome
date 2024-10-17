# SLZB-06x ESPHome Bluetooth proxy/Zigbee/Thread configs and binaries  

This repository includes YAML config files and compiled binaries of ESPHome-based firmware for SLZB-06x series coordinators.

These firmware allow users to use ESPHome Bluetooth proxy functionalities, as well as a combination of ESPHome Bluetooth proxy together with Zigbee (via Zigbee2MQTT or ZHA) and Thread/Matter-over-Thread (together with the Thread add-on/integration for Home Assistant).

## 1. Supported models

Firmware fits a series of SLZB-06x coordinators:  
| Model | [SLZB-06](https://smlight.tech/product/slzb-06/) | [SLZB-06M](https://smlight.tech/product/slzb-06m/) | [SLZB-06p7](https://smlight.tech/product/slzb-06p7/) | [SLZB-06p10](https://smlight.tech/product/slzb-06p10/)   | [SLZB-06p10](https://smlight.tech/product/slzb-06p10/) | [SLZB-06Mg24](https://smlight.tech/product/slzb-06mg24/) |
|---|:---:|:---:|:---:|:---:|:---:|:---:|  
|BT Proxy only|Yes|Yes|Yes|Yes|Yes|Yes|  
|Zigbee+BT Proxy|Yes|Yes|Yes|Yes|Yes|Yes|  
|Thread+BT Proxy|Yes|Yes|Yes|Yes|Yes|Yes|  

## 2. Firmware types and basic settings
There are 3 ESPHome yaml configs in 'configs' directory:  
1. **bt**: Bluetooth proxy only (in case you do not need a Zigbee or Thread connections).   
2. **zb-bt**: Zigbee+Bluetooth proxy. Settings for Zigbee (Zigbee2MQTT or ZHA):  
   - baudrate: 115200  
   - port: 6638  
3. **th-bt**: Thread+Bluetooth proxy. Settings for Thread (Thread integration/add-on):  
   - baudrate: 460800  
   - port: 6638  


## 3. Integration with Home Assistant  

![](https://github.com/smlight-dev/slzb-06-fw-esphome/blob/main/assets/img/zigbee-bluetooth-ha-exposed-config.png)

By default, Home Assistant should automatically discover SLZB-06x flashed with ESPHome, just like any other ESPHome device, and prompt the user to add it to Home Assistant.

If Home Assistant doesn't autodiscover the ESPHome device on your network, please follow these steps: 
- Go to "Settings".
- Go to "Devices & Services".
- Click the button "Add Integration" in the bottom right corner.  
- Search for the "ESPHome" integration and add it, using the IP address of your device and the port specified above (default is '6638').



## Please Note
Because of the [ESPHome recommendation](https://esphome.io/components/bluetooth_proxy.html), the Web Server component (ESPHome web interface) is disabled by default.

However, all controls and functionalities are available through the Home Assistant ESPHome integration, as shown in the screenshot above.  

If the user wants to enable the web interface at their own risk, this can be done simply by uncommenting those two lines in the ESPHome config and recompiling the firmware:  
*web_server:  
  port: 80  
  local: True*  
We do not recommend doing that based on the aforementioned notice from ESPHome
