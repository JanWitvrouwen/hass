# Home assistant all around the house

In this git repo you will find my approach to a smart house. The aim is to have the highest level of comfort with the least amount of classic switches. 
No switches, only touch screens and voice

## Server

- Lenovo M700 tiny i3 128Gb 8Gb
- [deConz USB zigbee stick](https://phoscon.de/en/conbee2)
- [P1 port cable](https://www.sossolutions.nl/slimme-meter-kabel-p1-kabel-10-meter)
- 500W UPS

## Network
- Unifi Switch
- Unifi Router
- Unifi AP
For better visibility, all IOT wifi devices are connected to a dedicated hidden SSID.
To ease network integration, i've come back from a seperate network for IOT and now everyting is in 1 flat vlan.

## Light
All [shelly](https://shelly.cloud) modules are powered by 12 or 24V to ease the wiring and open the possibility for external switches on UTP.


### Shelly 1
For the 230V lights, i use [Shelly 1 module](https://shelly.cloud/shelly-plus-1/)a. 
The 10A dry contact is perfect for all general loads.

Intergration in hass is done via [Shelly4Hass](https://github.com/StyraHem/ShellyForHASS)


### Shelly RGBW2
For all 12V spots and 24V led strips on a single color, 4 different circuits can be connected to a single [Shelly RGBW2](https://shelly.cloud/products/shelly-rgbw2-smart-home-automation-led-controller/) resulting in lower costs and less used space in the cabinet.

Intergration in hass is done via [Shelly4Hass](https://github.com/StyraHem/ShellyForHASS)

## Motion
### Xiaomi Aqara Human Motion 
In most places, a xiaomi wireless motion sensor works perfect. With the build in light sensor it is possible to only switch lights on when it is dark.
Intergration in hass is done wireless via deConz
[Code](Node-Red/aqara-motion.json)

### 24V PIR motion sensor wired
For the places with limit zigbee coverage, i use wired [pir motion sensors](https://www.amazon.nl/dp/B09LZ635P8/ref=pe_28126711_487805961_TE_item_image) attached to the input of a [Shelly 1 module](https://shelly.cloud/shelly-plus-1/).
Intergration in hass is done by connecting the PIR to the switch input on a Shelly 1 and settings the switch type to deconnected.

[Code](Node-Red/pir.json)
## Switches
### NSPanel
- [NSPanel](https://sonoff.tech/product/smart-wall-swtich/nspanel/)
- [Custom gui with ESPHome](https://github.com/marcfager/nspanel-mf)
- My own esphome [code](esphome/nspanel.yaml)
- My Node-Red [code](Node-Red/nspanel.json)

### Tablet

### shelly i3
- Shelly i3
- [Code](Node-Red/i3.json)

## Heating
- [ESPHome 8 relay module](https://www.banggood.com/5V-or-7-28V-Power-Supply-8-Channel-ESP8266-WIFI-8-way-Relay-Module-ESP-12F-Development-Board-Secondary-Development-Board-p-1833055.html?cur_warehouse=CN&rmmds=buy)
- [Temperature sensor](https://www.xiaomiproducts.nl/nl/xiaomi-aqara-temperatuur-en-vochtigheidssensor.html)
- [Actuator] (https://www.vloerverwarmingstore.be/p/watts-230v-actuator-watts-actuator-22c-normaal-gesloten?gclid=Cj0KCQiAmL-ABhDFARIsAKywVaewXcgfjG1puQjNqt-2RWaMK8zt9UdgicWADp7w8jSVKL7FB5139mQaAjzWEALw_wcB)
- [Code](Node-Red/heating.json)

## Alarm
- Door sensor - [Xiaomi Aqara Door and Window Sensor ](https://www.techpunt.nl/nl/xiaomi-aqara-deur-en-raam-sensor-104834619.html)
- Motion sensor: [Xiaomi Aqara Temperature and Humidity Sensor](https://www.techpunt.nl/en/xiaomi-aqara-temperature-and-humidity-sensor.html)
- Motion alert on camera

## Energy metering
### Smart meter
- [P1 port cable](https://www.sossolutions.nl/slimme-meter-kabel-p1-kabel-10-meter)
- Activate the port at your energy provider!!

### Shelly EM
- [Shelly EM](https://shelly.cloud/products/shelly-em-smart-home-automation-device/) - Single phase monitoring. 2 monitoring connections per shelly EM. Perfect non-intrusive monitoring for Washer and Dryer. 

### Shelly Plug 
- [Shelly Plug](https://shelly.cloud/products/shelly-plug-smart-home-automation-device/) - Power outlet monitoring and switching. Up to 3500W

### Shelly Plug S
- [Shelly Plug S](https://shelly.cloud/products/shelly-plug-s-smart-home-automation-device/) - Power outlet monitoring and switching. Up to 2500W. Smaller than the Plug version

## Velux Windows
INTEGRA velux window which was delivered with a KLI311 remote.

KLF 050 WW remote connected to 2 relays on a ESPHOme 8 relay module.

- [Code](esphome/velux-cover.yaml)

## Location
- Location based on HASS android app.


## Voice
- https://www.lenovo.com/gb/en/smart-clock/?orgRef=https%253A%252F%252Fwww.google.com%252F
- Google Home Mini
- Google Home Speaker

## Doorbel
- Ring doorbell without Chime. Instead the integration triggers a mp3 on all google speakers, send a toast to the nspanels and send a picture to the phone.
- [Code](Node-Reg/ring.json)


## Various Electrical hardware
- https://www.dmlights.be/meanwell_ledvoeding_constante_spanning_led_driver_24vdc_100w~1AI65
- https://www.automation24.be/nl/distributieblok-phoenix-3273374-ptfix-6-18x2-5-gy
- https://www.netwerkkabel.eu/nl/8u-wand-server-rack-494x400x360mm-bxdxh.html
- https://www.dmlights.be/abb__vynckier__fix_o_rail_36mod_2x18_~19QT3


