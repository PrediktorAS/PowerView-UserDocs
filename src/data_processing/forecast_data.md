# Forecast data

[Forecast data](../data_collection/weather/observed_predicted_weather.md) is loaded into data warehouse from [external services](../data_collection/weather/sources_of_weather_data.md#external-weather-services) and used for multiple purposes.

The production forecast from the forecast supplier is processed in PowerView before sent out to supplier.

## Combining power forecast with availability forecast

Power forecast is scaled with registered and stored power availability.
Reduced availability can be registered based on known outages like maintenance or curtailment.

## Weighted power forecast

Weighted power forecast can be configured in [Weighted Forecast](../user_interfaces/forecasting/setup_and_administration.md).
This solution can combine multiple forecast sources into one.
