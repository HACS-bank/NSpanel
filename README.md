# ESPectre on NSpanel-Easy

As well as including this package, you will need
1. Home Assistant _ESPectre Traffic Generator_ app
2. NSPanel-Easy blueprint settings for the Relay 2 icon _motion sensor_

Don't try to use with Bluetooth Proxy or BLE as they interfere with one another and will not both fit in the image

```
packages:
  remote_package_nspanel_easy:
    url: https://github.com/edwardtfn/NSPanel-Easy
    ref: latest
    refresh: 300s
    files:
      - nspanel_esphome.yaml # Base package
      - esphome/nspanel_esphome_addon_display_light.yaml
  remote_package_hacsbank_nspanel:
    url: https://github.com/HACS-bank/NSpanel
    ref: main
    refresh: 300s
    files:
      - nspanel-espectre.yaml
```
