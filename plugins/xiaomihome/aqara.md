# The Xiaomi Aqara zigbee protocol

### Adding the Xiaomi Aqara gateway to Jeedom

A full presentation of the range is available here: [Presentation article] (https://lunarok-domotique.com/plugins-jeedom/xiaomi-home-jeedom/aqara-lumi-xiaomi-smart-home-security/).

The Xiaomi gateway is necessary to activate the local API, so that Jeedom can communicate with its various devices.

Attention, you need the Xiaomi Mi Home Security version, not the Aqara Homekit version which does not have an API and does not allow all existing sensors to be linked.

** You need the Chinese version of the gateway, the European version does not allow activation of developer mode. **

** First do the developer mode activation manipulations before the firmware updates that Mi Home would offer. Do them only if it didn't work from the beginning or if it is already activated. **

For that you need to:
* add the gateway in the ** Mi Home ** application,
* be on the server ** China Mainland **,
* use the language ** Chinese ** (yes, suddenly screens can contain many illegible characters unless you are fluent in Mandarin ...),
* click on the gateway to select it,
* click on the "...",
* click on ** about **,
* you then have a ** version number **, click on it repeatedly until the message (yes in Chinese it doesn't help :)) and two new options appear,
* choose the first option (newly appeared),
* activate the switch button so that it turns green,
* local mode is active and your gateway is accessible on your local network.

* Attention *: On ** iOS ** (iPhone), in the ** about ** page, there is no ** version number **. You must click 5 times in the white part to continue.

* Attention *: To be able to send commands to the gateway, you must enter its password on its equipment page, in Jeedom (** Plugins-> Home automation protocol-> Xiaomi Home **, then click on the gateway you have previously created). This password is visible on the page where you activate the ** developer mode **, in the Mi Home application.

### Creation of equipment in Jeedom

The ** Xiaomi gateway ** will automatically appear in Jeedom, Aqara equipment will be created automatically. If that seems long, two things to know:
* For ** Aqara sensors **, the communication triggers the creation of the equipment in Jeedom. The frequency therefore varies depending on the model and its characteristics. (for example: blow on a temperature sensor will change the temperature value and will therefore bring up the information)
* For the ** switches ** and ** buttons ** Aqara, it may be necessary to activate them to have the creation of commands. (for example: press one of the buttons)

### Inclusion / Exclusion of sensors from Jeedom

It is possible to manage from Jeedom the additions or deletion of sensors of your gateways.

** Inclusion **: for each gateway, an inclusion button is available on the plugin's equipment page. By clicking on it, the gateway goes into inclusion mode and waits for a sensor to appear. It will be necessary to follow the appropriate manipulations for the sensor to be included. The module will then be added (and visible in Jeedom but also Mi Home)

** Exclusion **: to exclude a sensor, go to the health page of the plugin. A button is available for each sensor. Note that the exclusion does not remove the equipment in Jeedom for security reasons. It should then be deleted.

### Commands for compatible equipment

Currently compatible equipment provides the following information:

* ** Gateway **: RGB ring (with color and intensity), light sensor, play recorded sounds (0 to 8, 10 to 13, 20+ correspond to the default sounds in Mi Home, 10000 to turn off, 10001 and more for custom sounds). [See presentation in French] (https://lunarok-domotique.com/2017/03/mi-smart-gateway-domotique-jeedom/).
* ** Motion detector **: Binary status command for detected motion, no motion time, brightness sensor.
* ** Opening detector **: Binary status command for opening, no closing time length.
* ** Temperature / humidity sensor **: Information on temperature, humidity (and pressure for v2).
* ** Switch button **: Click command with click, double_click, long_click_press, long_click_release values.
* ** Socket ** and ** wall socket **: Binary status command with on and off, usage and consumption status.
* ** Wall switch **: Status command for each switch (click, double_click) and if dual, a command that gives simultaneous press.
* ** Flush-mounted switch ** (including the one with neutral): Binary status control with on and off for each switch.
* ** Cube **: Motion status command with the value move, tap_twice, shake_air, alert, flip90, flip180, free_fall, rotate_right, rotate_left and a Rotation command with the value in degrees of movement. [Presentation in French] (https://lunarok-domotique.com/2017/03/aqara-xiaomi-magic-controller-emploi-dans-jeedom/)
* ** Smoke detector **: Alarm (binary), Density smoke (digital), Optical Sensor Visibility (digital%) command.
* ** Gas ​​detector **: Alarm (binary), Density (digital) command.
* ** Water detector **: Status command (binary).
* ** Motor for curtain **: Status command (string), position (string) and associated action commands.

### Other common commands

For all this equipment, a ** Refresh ** command allows you to force the refresh of its information in Jeedom.

The API also provides the ** battery status ** of the equipment. The battery voltage is returned. With an API technical sheet indicating that it will be at most 3.2V and logically at 2.8V the battery is no longer usable. In fact, these are 3V batteries, so here is the information provided in Jeedom:

* ** Voltage **: on command not visible on the dashboard by default,
* ** Battery **: in standard status, but also on command not visible. Its value is considered to be 100% if greater than or equal to 3V, then decreases to 0% for 2.8V.
* ** Battery type **: The battery type is indicated for each item of equipment on the summary.
