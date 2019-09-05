# SensorPush Integration for Home Assistant

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=WREP29UDAMB6G)

Home Assistant integration for [SensorPush temperature and humidity/hygrometer sensors](https://www.amazon.com/SensorPush-Wireless-Thermometer-Hygrometer-Android/dp/B01AEQ9X9I?tag=rynoshark-20).

NOTE:

* If you register a new physical sensor with SensorPush, you must restart Home Assistant to discover the new device(s).

*  Ideally SensorPush sensors would be located within range of a [SensorPush G1 WiFi Gateway](https://www.amazon.com/SensorPush-G1-WiFi-Gateway-Anywhere/dp/B01N17RWWV?tag=rynoshark-20) for continously collecting and publishing data from the sensors to the SensorPush cloud. However, SensorPush sensors can also synchronize historical data over Bluetooth when nearby to an iOS or Android device with the SensorPush app).

## Installation

If you have trouble with installation and configuration, visit the [SensorPush Home Assistant community discussion](https://community.home-assistant.io/t/sensorpush-humidity-and-temperature-sensors/105711).

### Step 1: Install Custom Components

Easiest is by setting up [Home Assistant Community Store (HACS)](https://github.com/custom-components/hacs) and then adding the "Integration" repository: *rsnodgrass/hass-sensorpush*. However you can also manually copy all the files in [custom_components/sensorpush/](https://github.com/rsnodgrass/hass-sensorpush/custom_components/sensorpush) directory to `/config/custom_components/sensorpush` on your Home Assistant installation.

### Step 2: Configure SensorPush

Example configuration.yaml entry:

```yaml
sensorpush:
  username: your@email.com
  password: your_password

sensors:
  - platform: sensorpush
```

#### Lovelace

```yaml
entities:
  - entity: sensor.warehouse_humidity
  - entity: sensor.warehouse_temperature
show_header_toggle: false
title: SensorPush
type: entities
```

## Hardware Requirements

* [SensorPush Wireless Thermometer/Hygrometer - Humidity & Temperature Smart Sensor](https://www.amazon.com/SensorPush-Wireless-Thermometer-Hygrometer-Android/dp/B01AEQ9X9I?tag=rynoshark-20)
* [SensorPush G1 WiFi Gateway](https://www.amazon.com/SensorPush-G1-WiFi-Gateway-Anywhere/dp/B01N17RWWV?tag=rynoshark-20)

## See Also

* [Community support for Home Assistant SensorPush integration](https://community.home-assistant.io/t/sensorpush-humidity-and-temperature-sensors/105711)
* [pysensorpush](https://github.com/rsnodgrass/pysensorpush) - Python interface to SensorPush cloud API
* [SensorPush](https://sensorpush.com) (official product page)
* [ReviewGeek's review of SensorPush](https://www.reviewgeek.com/3291/sensor-push-review-the-best-smart-hygrometer-and-thermometer-around/)

## Known Issues

## Future Enhancements

* support Celsius (in addition to Fahrenheit) when SensorPush exposes units via its APIs

No plans to implement the following at this time:

* determine if the following devices work with SensorPush (all were tested/approved the same day, with same internal designs):

- Oasis OH-31 HT Tracker (FCC Grantee [2AL92](https://fccid.io/2AL92-OH31/Test-Report/Test-Report-3428874), ID: 2AL92-OH31) like the SensorPush (FCC Grantee 2AL9W and [2AL9X HT1](https://fccid.io/2AL9X-HT1/Test-Report/Test-Report-3433404))
- [iBeTag Beacon IB004NPLUSSHT](https://fccid.io/2AB4P-IB004NPLUSSHT/External-Photos/External-photos-3446863) (FCC Grantee [2AB4P](https://fccid.io/2AB4P))
- [Jaalee Beacon IB004NPLUSSHT](https://fccid.io/2ABRO-IB004NPLUSSHT/Test-Report/Test-Report-3431944) (FCC Grantee 2ABRO)
- [Saalee iB004N-Plus-SHT](https://www.dhgate.com/product/wireless-digital-bluetooth-sensor-beacon/451751881.html?skuid=568611302727536642)
- [AnkhMaway iB004N-Plus-SHT LT](https://ankhmaway.en.alibaba.com/product/60602605562-806002398/Ble_Beacon_With_Temperature_and_Humidity_Sensor_Bluetooth_Programmable_iBeacon.html) / (https://www.beaconzone.co.uk/iB004NPLUSLight)

* allow fetching data directly from the sensor via Bluetooth (no cloud dependency required); may be required to integrate with above sensors
