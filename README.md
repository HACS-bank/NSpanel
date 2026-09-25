# Development of addons which can be used to extend NSpanel-Easy

once these are ready and I learn how, these will be submitted to the real project. this is my testing ground, nothing here is recommended to use in production 

## local Climate control if API down

concept: local climate control always running, but controlling relay0. if API goes down, change onto local control of relay1
needs generalisation: should use a substitution to pick relay 1 or 2

## Hardware button press wakes the screen

not yet useable

## Bluetooth BLE proxy

working as proxy, needs more work for iBeacon to use with BPS 

## ESPectre on NSpanel-Easy

working. waiting for ESPectre v3 to be released 

As well as including this package, you will need
1. Home Assistant _ESPectre Traffic Generator_ app
2. NSPanel-Easy blueprint settings for the Relay 2 icon _motion sensor_

Don't try to use with Bluetooth Proxy or BLE as they interfere with one another and will not both fit in the image

## how to deploy

add the following to esphome .yaml, build and deploy to panel
```
packages:
  remote_package_nspanel_easy:
    url: https://github.com/edwardtfn/NSPanel-Easy
    ref: latest
    refresh: 300s
    files:
      - nspanel_esphome.yaml # Base package
      - esphome/nspanel_esphome_addon_climate_heat.yaml
      - esphome/nspanel_esphome_addon_display_light.yaml

  remote_package_hacsbank_nspanel:
    url: https://github.com/HACS-bank/NSpanel
    ref: main
    refresh: 300s
    files:
# wake panel on hardware button press
      - nspanel-buttonwake.yaml
# ESPectre Motion Detection
      - nspanel-espectre.yaml
# or
      - nspanel-bluetooth.yaml # dont use with ESPectre due to interference
```
