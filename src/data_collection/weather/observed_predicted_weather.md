# Observed vs. predicted weather

The weather data we collect can be divided into two categories: observed and predicted. Observed weather data is the logged actual weather conditions at the production facility. Predicted weather data is the weather forecast for the production facility.

## Observed weather

Depending on the [source of the data](sources_of_weather_data.md), observed weather data can be a considered a live feed of the weather, and as it is logged it becomes a historical record of the weather. Combining both local weather sensors/stations and external services satellite observations is considered best practice and gives a very good picture of the weather at the production site.

#### Manually corrected observed weather data

As described in [Manual Weather Correction](../../user_interfaces/manual/weather_data_correction.md) and [Manual Snow Correction](../../user_interfaces/manual/snow_loss_correction.md), all weather data can be manually corrected. This allows the correction of any faulty or missing data.

## Predicted weather (forecasts)

Weather, and thus production, forecast data is collected from [external weather services](sources_of_weather_data.md#external-weather-services) and stored in PowerView databases. Update rates down to 5 minutes can be achieved, but the typical setup for day ahead forecasts is every day, and for intra day forecasts every 15 minutes. Typical resolution is 15 minutes.

Availability forecast is added manually by user in PowerView web portal in [Planned Power Reduction](../user_interfaces/forecasting/planned_power_reduction.md) screen.

See also [Forecasting](../../user_interfaces/forecasting/)

## Filtering weather data

As described in [Weather sensor filtering](../data_processing/data_filtering/weather_sensor_filtering.md), all weather is filtered before added to the database. This is done to avoid obviously faulty data.
