# Home assistant all around the house

In this git repo you will find my approach to a smart house. The aim is to have the highest level of comfort with the least amount of classic switches. 
No switches, only touch screens and voice

## Server

- Lenovo M700 tiny i3 128Gb 8Gb
- deConz USB zigbee stick https://phoscon.de/en/conbee2
- p1 cable
- 500W UPS



## Network
- Unifi Switch
- Unifi Router
- Unifi AP
For better visibility, all IOT wifi devices are connected to a dedicated hidden SSID.
To ease network integration, i've come back from a seperate network for IOT and now everyting is in 1 flat vlan.

## Light
All shelly modules are powered by 12 or 24V to ease the wiring and open the possibility for external switches on UTP.


### Shelly 1
For the 230V lights, i use shelly 1. 
The 10A dry contact is perfect for all general loads.

Intergration in hass is done via Shelly4Hass


### Shelly RGBW2
For all 12V spots and 24V led strips
on a single color, 4 different circuits can be connected to a single RGBW2 resulting in lower costs and less used space in the cabinet.

Intergration in hass is done via Shelly4Hass

## Motion
### Xiaomi Aqara Human Motion 
In most places, a xiaomi wireless motion sensor works perfect. With the build in light sensor it is possible to only switch lights on when it is dark.

```
[{"id":"e5fe8cdccbfbe162","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Gang 2","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.motion_sensor_2_gang_2","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"on","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":0,"forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":180,"y":360,"wires":[["8d900cb261d30e7f","ad44b72f6a95127d"],[]]},{"id":"8d900cb261d30e7f","type":"api-current-state","z":"39800f24f17d753b","name":"Lux","server":"a9ab8e32.aa7d","version":3,"outputs":1,"halt_if":"","halt_if_type":"num","halt_if_compare":"is","entity_id":"sensor.motion_sensor_2_gang_2","state_type":"num","blockInputOverrides":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"for":0,"forType":"num","forUnits":"minutes","override_topic":false,"state_location":"payload","override_payload":"msg","entity_location":"data","override_data":"msg","x":410,"y":360,"wires":[["38a045c153ab4241"]]},{"id":"38af93a4d1f45669","type":"api-call-service","z":"39800f24f17d753b","name":"Gang 2 Aan","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_on","areaId":[],"deviceId":[],"entityId":["light.shelly_gang2"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":770,"y":360,"wires":[[]]},{"id":"7a3f2574f29be2f4","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Gang 2","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.motion_sensor_2_gang_2","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"off","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":"0","forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":180,"y":420,"wires":[["9b5e1be6c057e0fd"],[]]},{"id":"9b5e1be6c057e0fd","type":"api-call-service","z":"39800f24f17d753b","name":"Gang 2 Uit","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_off","areaId":[],"deviceId":[],"entityId":["light.shelly_gang2"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":620,"y":420,"wires":[[]]},{"id":"38a045c153ab4241","type":"switch","z":"39800f24f17d753b","name":"","property":"payload","propertyType":"msg","rules":[{"t":"lt","v":"10","vt":"num"}],"checkall":"true","repair":false,"outputs":1,"x":590,"y":360,"wires":[["38af93a4d1f45669"]]},{"id":"a9ab8e32.aa7d","type":"server","name":"HASS","version":2,"addon":true,"rejectUnauthorizedCerts":true,"ha_boolean":"y|yes|true|on|home|open","connectionDelay":true,"cacheJson":true,"heartbeat":false,"heartbeatInterval":"30"}]
```

Intergration in hass is done wireless via deConz

### 24V PIR motion sensor wired
For the places with limit zigbee coverage, i use wired pir motion sensors attached to the input of a Shelly 1 module.
https://www.amazon.nl/dp/B09LZ635P8/ref=pe_28126711_487805961_TE_item_image

```
[{"id":"52326e14f0414152","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Wasplaats","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.shelly_wasplaats_switch","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"on","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":0,"forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":190,"y":840,"wires":[["88bf5d889fe566e3"],[]]},{"id":"88bf5d889fe566e3","type":"api-call-service","z":"39800f24f17d753b","name":"Wasplaats Aan","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_on","areaId":[],"deviceId":[],"entityId":["light.shelly_wasplaats"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":640,"y":840,"wires":[[]]},{"id":"d01b408be29669cd","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Wasplaats","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.shelly_wasplaats_switch","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"off","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":"0","forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":190,"y":900,"wires":[["887ca40d64ce276d"],[]]},{"id":"887ca40d64ce276d","type":"api-call-service","z":"39800f24f17d753b","name":"Waskot Uit","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_off","areaId":[],"deviceId":[],"entityId":["light.shelly_wasplaats"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":620,"y":900,"wires":[[]]},{"id":"a9ab8e32.aa7d","type":"server","name":"HASS","version":2,"addon":true,"rejectUnauthorizedCerts":true,"ha_boolean":"y|yes|true|on|home|open","connectionDelay":true,"cacheJson":true,"heartbeat":false,"heartbeatInterval":"30"}]
```
Intergration in hass is done by connecting the PIR to the switch input on a Shelly 1 and settings the switch type to deconnected.

## Switches
### NSPanel
https://sonoff.tech/product/smart-wall-swtich/nspanel/

### Tablet

### shelly i3


## Door and Gate
https://www.banggood.com/5V-or-7-28V-Power-Supply-8-Channel-ESP8266-WIFI-8-way-Relay-Module-ESP-12F-Development-Board-Secondary-Development-Board-p-1833055.html?cur_warehouse=CN&rmmds=buy

## Heating
https://www.banggood.com/5V-or-7-28V-Power-Supply-8-Channel-ESP8266-WIFI-8-way-Relay-Module-ESP-12F-Development-Board-Secondary-Development-Board-p-1833055.html?cur_warehouse=CN&rmmds=buy

https://www.xiaomiproducts.nl/nl/xiaomi-aqara-temperatuur-en-vochtigheidssensor.html


## Alarm
- Door sensor: https://www.xiaomiproducts.nl/nl/xiaomi-aqara-deur-en-raam-sensor-104834619.html
- 

## Energy metering
### Smart meter
P1 port
Activate the port at your energy provider!!
https://www.sossolutions.nl/slimme-meter-kabel-p1-kabel-10-meter

### Shelly EM

### Shelly Plug 

### Shelly Plug S

## Velux Windows
INTEGRA velux window which was delivered with a KLI311 remote.

KLF 050 WW remote connected to 2 relays on a ESPHOme 8 relay module.

Check velux-esphome.yaml [velux-cover.yaml](esphome/velux-cover.yaml)

## Location


## Voice
https://www.lenovo.com/gb/en/smart-clock/?orgRef=https%253A%252F%252Fwww.google.com%252F




## Various Electrical hardware
- https://www.dmlights.be/meanwell_ledvoeding_constante_spanning_led_driver_24vdc_100w~1AI65
- https://www.automation24.be/nl/distributieblok-phoenix-3273374-ptfix-6-18x2-5-gy
- https://www.netwerkkabel.eu/nl/8u-wand-server-rack-494x400x360mm-bxdxh.html
- https://www.dmlights.be/abb__vynckier__fix_o_rail_36mod_2x18_~19QT3


