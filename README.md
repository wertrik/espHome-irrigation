# espHome-irrigation
Home Assistant - espHome - irrigation system

Irrigation system based on espHome - controlled by HomeAssistant.
I dont use esphome irrigation component - I made this controller before irrigation component was released.
This is not perfect solution for everyone, it just inspiration - how you can create own controller.
Code is not best but I have no time for tweaking maybe in future.

Used parts:
esp32
four relay module
Key&Led module (https://www.aliexpress.com/item/32725359463.html)

espHome main components used:

https://esphome.io/components/display/tm1638.html 

https://esphome.io/guides/automations.html#script-component

I neeed controll 4 zones, so I use four relays. First zone is not used in irrigation program.
So if you have other use case you need change code.

Controller works this way:
User can manually set duration of each zone.
User can manually start and stop each zone.
User can manually start program. Program contains zone 2,3,4.
User can manually stop program/HA program.
There is no option to schedule program - you can start program in actual time.

Im using Scheduler in HomeAssistant.
In HA Im counting duration of each zone - based of rainfall, outdoor tempearature etc.
In HA I set time threshold for each zone, next I count duration for zones, HomeAssistant send time of duration to controller and starts program.
Running program in controller is independent of HomeAssistant.

In controller you can not change thresholds in HA.
HA changes time of duration of each zone in controller.

In yaml files you need to set you credentials, maybe there are some Czech words.
To set time threshold in HA I'm using helpers - "input number" (e.g. input_number.irrigation_zone_3_threshold_time).

![simple](https://user-images.githubusercontent.com/79766288/229622904-3cd84893-b9fc-4526-b818-ed826a37467a.jpg)

