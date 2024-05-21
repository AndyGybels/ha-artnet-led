
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)

# Home Assistant integration modbus pulse

Provides the same functionality as the build in "modbus" integration but extends it with a  *pulse* parameter which allows u to send a pulse to the modbus adress.
Usefull for controlling for example relay switches.

## Prerequisites

* [Home Assistant (hass)](https://www.home-assistant.io/) >= 2022.0.
* [pymodbus](https://github.com/pymodbus-dev/pymodbus) == 3.6.8 will load automatically.

## Installation

> **Note**
> 
> This integration requires [HACS](https://hacs.xyz/docs/setup/download/) to be installed


1. Open HACS
2. Open the options in the top right and select _Custom repositories_
3. Enter this repository's URL (`https://github.com/AndyGybels/modbus-pulse`) under the Category _Integration_.
4. Press _Add_
5. _+ EXPLORE & DOWNLOAD REPOSITORIES_
6. Find _Modbus Pulse_ in this list
7. _DOWNLOAD THIS REPOSITORY WITH HACS_
8. _DOWNLOAD_
9. Restart Home Assistant (_Settings_ > _System_ >  _RESTART_)

## Configuration

modbus_pulse is configured in the `configuration.yaml` file under the *modbus_pulse* domain.
Configuration is the same as the integrated modbus integration so see the modbus integration documentation for more information:
https://www.home-assistant.io/integrations/modbus/


Example switch configuration:

```yaml
modbus_pulse:
  - type: tcp
    host: IP_ADDRESS
    port: 502
    switches:
      - name: Switch
        slave: 2
        address: 15
        write_type: coil
        pulse: true
        pulse_delay: 100
        verify:
            input_type: coil
            adress: 8192
            state_on: 1
            state_off: 0
```

Example light configuration:

```yaml
modbus_pulse:
  - type: tcp
    host: IP_ADDRESS
    port: 502
    lights:
      - name: Studio
        slave: 2
        address: 15
        write_type: coil
        pulse: true
        pulse_delay: 100
        verify:
            input_type: coil
            adress: 8192
            state_on: 1
            state_off: 0
```



# Legal

Modbus pulse is developed under the Apache2 licence
