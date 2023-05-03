# Forecast data

[Forecast data](../data_collection/forecast_data.md) is loaded into data warehouse from 3. party suppliers and used for multiple purposes.

The production forecast from the forecast supplier is processed in PowerView before sent out to supplier.

## Combining power forecast with availability forecast
Power forecast is scaled with registered and stored power availability.
Reduced availability can be registered based on known outages like maintenance or curtailment.

## Weighted power forecast
Weighted power forecast can be configured in [Weighted Forecast](../../User%20Interfaces/Forecasting/Setup%20and%20Administration/Setup%20and%20Administration.md).
This solution can combine multiple forecast sources into one.

