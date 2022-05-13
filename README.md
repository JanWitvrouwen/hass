#Home assistant all around the house
In this git repo you will find my approach to a smart house. The aim is to have the highest level of comfort with the least amount of classic switches. 
No switches, only touch screens and voice

## Server

deConz USB zigbee stick


## Light


## Motion
### Xiaomi Aqara Human Motion 
In most places, a xiaomi wireless motion sensor works perfect. With the build in light sensor it is possible to only switch lights on when it is dark.

```
[{"id":"e5fe8cdccbfbe162","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Gang 2","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.motion_sensor_2_gang_2","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"on","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":0,"forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":180,"y":360,"wires":[["8d900cb261d30e7f","ad44b72f6a95127d"],[]]},{"id":"8d900cb261d30e7f","type":"api-current-state","z":"39800f24f17d753b","name":"Lux","server":"a9ab8e32.aa7d","version":3,"outputs":1,"halt_if":"","halt_if_type":"num","halt_if_compare":"is","entity_id":"sensor.motion_sensor_2_gang_2","state_type":"num","blockInputOverrides":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"for":0,"forType":"num","forUnits":"minutes","override_topic":false,"state_location":"payload","override_payload":"msg","entity_location":"data","override_data":"msg","x":410,"y":360,"wires":[["38a045c153ab4241"]]},{"id":"38af93a4d1f45669","type":"api-call-service","z":"39800f24f17d753b","name":"Gang 2 Aan","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_on","areaId":[],"deviceId":[],"entityId":["light.shelly_gang2"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":770,"y":360,"wires":[[]]},{"id":"7a3f2574f29be2f4","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Gang 2","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.motion_sensor_2_gang_2","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"off","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":"0","forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":180,"y":420,"wires":[["9b5e1be6c057e0fd"],[]]},{"id":"9b5e1be6c057e0fd","type":"api-call-service","z":"39800f24f17d753b","name":"Gang 2 Uit","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_off","areaId":[],"deviceId":[],"entityId":["light.shelly_gang2"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":620,"y":420,"wires":[[]]},{"id":"38a045c153ab4241","type":"switch","z":"39800f24f17d753b","name":"","property":"payload","propertyType":"msg","rules":[{"t":"lt","v":"10","vt":"num"}],"checkall":"true","repair":false,"outputs":1,"x":590,"y":360,"wires":[["38af93a4d1f45669"]]},{"id":"a9ab8e32.aa7d","type":"server","name":"HASS","version":2,"addon":true,"rejectUnauthorizedCerts":true,"ha_boolean":"y|yes|true|on|home|open","connectionDelay":true,"cacheJson":true,"heartbeat":false,"heartbeatInterval":"30"}]
```

### 24V PIR motion sensor wired
For the places with limit zigbee coverage, i use wired pir motion sensors attached to the input of a Shelly 1 module.
https://www.amazon.nl/dp/B09LZ635P8/ref=pe_28126711_487805961_TE_item_image

```
[{"id":"52326e14f0414152","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Wasplaats","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.shelly_wasplaats_switch","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"on","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":0,"forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":190,"y":840,"wires":[["88bf5d889fe566e3"],[]]},{"id":"88bf5d889fe566e3","type":"api-call-service","z":"39800f24f17d753b","name":"Wasplaats Aan","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_on","areaId":[],"deviceId":[],"entityId":["light.shelly_wasplaats"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":640,"y":840,"wires":[[]]},{"id":"d01b408be29669cd","type":"server-state-changed","z":"39800f24f17d753b","name":"Motion Wasplaats","server":"a9ab8e32.aa7d","version":4,"exposeToHomeAssistant":false,"haConfig":[{"property":"name","value":""},{"property":"icon","value":""}],"entityidfilter":"binary_sensor.shelly_wasplaats_switch","entityidfiltertype":"exact","outputinitially":false,"state_type":"str","haltifstate":"off","halt_if_type":"str","halt_if_compare":"is","outputs":2,"output_only_on_state_change":true,"for":"0","forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":190,"y":900,"wires":[["887ca40d64ce276d"],[]]},{"id":"887ca40d64ce276d","type":"api-call-service","z":"39800f24f17d753b","name":"Waskot Uit","server":"a9ab8e32.aa7d","version":5,"debugenabled":false,"domain":"light","service":"turn_off","areaId":[],"deviceId":[],"entityId":["light.shelly_wasplaats"],"data":"","dataType":"jsonata","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","x":620,"y":900,"wires":[[]]},{"id":"a9ab8e32.aa7d","type":"server","name":"HASS","version":2,"addon":true,"rejectUnauthorizedCerts":true,"ha_boolean":"y|yes|true|on|home|open","connectionDelay":true,"cacheJson":true,"heartbeat":false,"heartbeatInterval":"30"}]
```

## Heating


## Alarm


## Location



