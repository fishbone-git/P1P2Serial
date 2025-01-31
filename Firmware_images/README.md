# Firmware images for P1P2-ESP-Interface

## P1P2Monitor firmware for ATmega328 on P1P2-ESP-Interface

(this image does not work on Arduino Uno)

P1P2Monitor auxiliary control is currently only usable for Daikin E-series. Monitoring is also available for certain F-series models.

[P1P2Monitor v0.9.22](P1P2Monitor-0.9.22.ino.hex)

To install (Linux CLI):

```
avrdude -c avrisp -p atmega328p  -P net:<IPv4>:328 -e -Uflash:w:P1P2Monitor-0.9.22.ino.hex:i
```

To install (Windows CLI, using avrdude 7.0 for Windows):

```
avrdude.exe -c avrisp -p m328p  -P net:<IPv4>:328 -e -Uflash:w:P1P2Monitor-0.9.22.ino.hex:i
```

## P1P2-bridge-esp8266 firmware for 4MB ESP8266 on P1P2-ESP-Interface

[P1P2-bridge-esp8266 0.9.22 (4MB version) for Daikin E-series](P1P2-bridge-esp8266-0.9.22-Eseries-4MB.ino.bin)

[P1P2-bridge-esp8266 0.9.22 (4MB version) for Daikin F-series](P1P2-bridge-esp8266-0.9.22-Fseries-4MB.ino.bin)

To install OTA (Linux CLI):

```
~/.arduino15/packages/esp8266/tools/python3/3.7.2-post1/python3 -I ~/.arduino15/packages/esp8266/hardware/esp8266/3.0.2/tools/espota.py -i <IPv4> -p 8266 --auth=P1P2MQTT -f P1P2-bridge-esp8266-0.9.22-Eseries-4MB.ino.bin
```
or
```
~/.arduino15/packages/esp8266/tools/python3/3.7.2-post1/python3 -I ~/.arduino15/packages/esp8266/hardware/esp8266/3.0.2/tools/espota.py -i <IPv4> -p 8266 --auth=P1P2MQTT -f P1P2-bridge-esp8266-0.9.22-Fseries-4MB.ino.bin
```

To install over USB with ESP01 programmer (Linux CLI):

```
~/.arduino15/packages/esp8266/tools/python3/3.7.2-post1/python3 -I ~/.arduino15/packages/esp8266/hardware/esp8266/3.0.2/tools/upload.py --chip esp8266 --port /dev/ttyUSB0 --baud 115200 --before default_reset --after hard_reset write_flash 0x0 P1P2-bridge-esp8266-0.9.22-Eseries-4MB.ino.bin
```
or
```
~/.arduino15/packages/esp8266/tools/python3/3.7.2-post1/python3 -I ~/.arduino15/packages/esp8266/hardware/esp8266/3.0.2/tools/upload.py --chip esp8266 --port /dev/ttyUSB0 --baud 115200 --before default_reset --after hard_reset write_flash 0x0 P1P2-bridge-esp8266-0.9.22-Eseries-4MB.ino.bin
```

To install OTA from Windows with espota.py from [here](https://github.com/esp8266/Arduino.git):

```
yourpath\Arduino-master\tools\espota.py -i <IPv4> -p 8266 --auth=P1P2MQTT -f P1P2-bridge-esp8266-0.9.22-Eseries-4MB.ino.bin
```

```
yourpath\Arduino-master\tools\espota.py -i <IPv4> -p 8266 --auth=P1P2MQTT -f P1P2-bridge-esp8266-0.9.22-Fseries-4MB.ino.bin
```

## P1P2-bridge-esp8266 firmware for 1MB ESP01s

Uses MQTT_INPUT_HEXDATA (topic P1P2/R/#) instead of serial for P1/P2 data input, and provides debugging output over 115.2kBaud serial.

[P1P2-bridge-esp8266 0.9.22 (1MB version) for Daikin E-series](P1P2-bridge-esp8266-0.9.22-Eseries-ESP01s.ino.bin)

[P1P2-bridge-esp8266 0.9.22 (1MB version) for Daikin F-series](P1P2-bridge-esp8266-0.9.22-Fseries-ESP01s.ino.bin)

## FOSS notice

These images are built with Arduino BSPs and libraries, for which source code and license information is made available [here](../OSS-dependencies/README.md).
