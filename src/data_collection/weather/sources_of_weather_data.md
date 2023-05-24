# Sources of weather data

There are three main sources of weather data, in weighted order:

* Manual input, mainly used to correct any faulty data
* Weather sensors, which are locally installed
* External weather services, often using satellite observations and predictive models, which is used to fill in the gaps between the weather sensors or replace them entirely

## Manual input

As described in [Manual Weather Correction](../../user_interfaces/manual/weather_data_correction.md) and [Manual Snow Correction](../../user_interfaces/manual/snow_loss_correction.md), all weather data can be manually corrected. This allows the correction of any faulty or missing data.

## Weather sensors

Physical weather sensors installed at the production site can be used to collect weather data. This data is considered the most reliable, as it is the closest to the actual production site. The collected data depends on the capabilities of the weather station. We support a number of weather stations through industrial protocols like Modbus and OPC. The resolution of the data collected by a local weather station is better, meaning that we can probe the station often. This makes variations to the weather more visible, and thus makes it easier to detect faulty data.

Having sensors at the site of power production is optional, and often depends on the size of the production at the site. For example, a small solar production site might not have any sensors, while a large solar farm would have many sensors. Data acquired from the sensors are considered the most reliable, as they are the closest to the actual production site. However, the sensors are not always reliable, and can be faulty or missing data. This is why we also use manual observations and satellite data.

## External weather services

Subscribing to an external weather service and adding the data from it are configured manually. The data from these services is used to fill in the gaps between the sensors, or replace them entirely. Sometimes, like in the case of snow, it is a nice supplement to the sensors, if they cannot measure snowfall. However, the satellite data is not always reliable, and can be faulty or missing data. This is why we also use manual observations and sensor data.

Examples of external weather services are:
* [Meteologica](https://www.meteologica.com/)
* [SolarGIS](https://solargis.com/)
* [Enercast](https://www.enercast.de/)