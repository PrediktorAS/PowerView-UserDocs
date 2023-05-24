# What is weather data?

Listening to a weather forecast you'll hear things like "it will be 20 degrees and mainly sunny with a light breeze from the south". This is a very simplified version of what weather data is. Weather data is a collection of parameters that describe the weather at a given location at a given time. If you step outside and look at the sky, you can see the weather. You can see if it is sunny or cloudy, if it is raining or snowing, and you can feel the temperature and wind. However, you cannot see the air pressure, humidity or the amount of rain that has fallen. This is what we call weather data. Also, you'll be able to predict the weather pretty accurately for the next few hours, but you cannot predict the weather for the next few days.

Depending on your source of information, the level of detail and accuracy of the weather data will vary.

## Typical parameters collected

* Irradiation (horizontal, incline, diffuse)
* Temperature (environment, module)
* Wind (speed, direction)
* Humidity
* Rain Amount
* Air Pressure
* Snow Depth

## All weather data is filtered

To normalize incoming data, all weather data is filtered before added to the database. This is done to avoid obviously faulty data. This is described in detail [here](../../data_processing/data_filtering/weather_sensor_filtering.md) 
