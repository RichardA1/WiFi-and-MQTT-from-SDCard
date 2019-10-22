# Get WiFi and MQTT credentials from SD Card while using a VS1053

This code can be used for projects that use an Feather Hazzuh ESP8266 with a Music Maker Feather Wing to pass the network credentials to the Arduino code so that it can connect to WiFi and an MQTT server. This is done via a configuration file saved onto the SD Card with the relevant information.

This will make it easy for an end user to update network information, but this code dose save critical network credentials in plain text format onto a removable SD Card. This is a security risk and this should not be used as is for anything other than a demo or testing.

To make this method secure the following changes should be made:
 - Alter code so that the config.txt file is read once, the info is saved to EEPROM and the config.txt file contents are reset to have blank values. If the device sees new values in the config.txt file, the new setting are saved in EEPROM otherwise it connects with the setting last saved.

- When opened if the contents of config.txt is not encrypted, load the setting, encrypt the credentials and re save the encrypted information onto the SD Card. From that point on only the Arduino code can decrypt the information for use in connecting to the network.

On the SD Card you will want to create a file names config.txt.

This file needs to contain the following text.

```
SSID: "YourSSID"
PASS: "YourPassword"
MQTT: "YourMQTT URL"
MQTTuser: "MQTTuser"
MQTTpass: "MQTTpassword"
```
