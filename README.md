# Home Assistant support for Tuya BLE devices

## Overview

This repo is for testing the Switch Robot from Tuya only, which is a little similar to Fingerbot Plus.
It works to move the arm 
- without errors
- without ESP32 proxy (with a simple ASUS dongle connected to home assistant)
- without polling every 30 seconds (and corresponding warnings).

limitations: If you press the button to move arm on the device it updates only if you are still connected (e.g. 30 seconds after you have send last command). Other than that it will not be propagated to home assistant. Workaround possible via home assistant config.

This integration supports Tuya devices connected via BLE.

_Inspired by code of [@redphx](https://github.com/redphx/poc-tuya-ble-fingerbot)_

_Original HASS component forked from https://github.com/PlusPlus-ua/ha_tuya_ble_

_Merged several changes by @airy10 and @patriot1889, including light support_


## Installation

Place the `custom_components` folder in your configuration directory (or add its contents to an existing `custom_components` folder). Alternatively install via [HACS](https://hacs.xyz/).

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=helgemeyer&repository=ha_tuya_ble&category=integration)

## Usage

After adding to Home Assistant integration should discover all supported Bluetooth devices, or you can add discoverable devices manually.

The integration works locally, but connection to Tuya BLE device requires device ID and encryption key from Tuya IOT cloud. It could be obtained using the same credentials as in official Tuya integration. To obtain the credentials, please refer to *old* official Tuya integration [documentation](https://web.archive.org/web/20240204064157/https://www.home-assistant.io/integrations/tuya/)

## Supported devices list (not up to date)

* Fingerbots (category_id 'szjqr')
  + Fingerbot (product_ids 'ltak7e1p', 'y6kttvd6', 'yrnk7mnn', 'nvr2rocq', 'bnt7wajf', 'rvdceqjh', '5xhbk964'), original device, first in category, powered by CR2 battery.
  + Adaprox Fingerbot (product_id 'y6kttvd6'), built-in battery with USB type C charging.
  + Fingerbot Plus (product_ids 'blliqpsj', 'ndvkgsrm', 'yiihr7zh', 'neq16kgd', 'mknd4lci', 'riecov42'), almost same as original, has sensor button for manual control.
  + CubeTouch 1s (product_id '3yqdo5yt'), built-in battery with USB type C charging.
  + CubeTouch II (product_id 'xhf790if'), built-in battery with USB type C charging.

  All features available in Home Assistant, programming (series of actions) is implemented for Fingerbot Plus.
  For programming exposed entities 'Program' (switch), 'Repeat forever', 'Repeats count', 'Idle position' and 'Program' (text). Format of program text is: 'position\[/time\];...' where position is in percents, optional time is in seconds (zero if missing).

* Temperature and humidity sensors (category_id 'wsdcg')
  + Soil moisture sensor (product_id 'ojzlzzsw').

* Temperature and humidity sensors (category_id 'zwjcy')
  + Smartlife Plant Sensor SGS01 (product_id 'gvygg3m8').

* CO2 sensors (category_id 'co2bj')
  + CO2 Detector (product_id '59s19z5m').

* Smart Locks (category_id 'ms')
  + Smart Lock (product_id 'ludzroix', 'isk2p555', 'gumrixyt').

* Climate (category_id 'wk')
  + Thermostatic Radiator Valve (product_ids 'drlajpqc', 'nhj2j7su').

* Smart water bottle (category_id 'znhsb')
  + Smart water bottle (product_id 'cdlandip')

* Irrigation computer (category_id 'ggq')
  + Irrigation computer (product_id '6pahkcau')
  + 2-outlet irrigation computer SGW02 (product_id 'hfgdqhho'), also known as MOES BWV-YC02-EU-GY

* Lights
  + Most light products should be supported as the Light class tries to get device description from the cloud when there are added but only Strip Lights (category_id 'dd') Magiacous RGB light bar (product_id 'nvfrtxlq') has has been tested

## Support project
_The following is a comment from the original developer which deserves to stay_


I am working on this integration in Ukraine. Our country was subjected to brutal aggression by Russia. The war still continues. The capital of Ukraine - Kyiv, where I live, and many other cities and villages are constantly under threat of rocket attacks. Our air defense forces are doing wonders, but they also need support. So if you want to help the development of this integration, donate some money and I will spend it to support our air defense.
<br><br>
<p align="center">
  <a href="https://www.buymeacoffee.com/3PaK6lXr4l"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy me an air defense"></a>
</p>
