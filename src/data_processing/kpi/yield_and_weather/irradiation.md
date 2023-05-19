# Irradiation

## What is irradiation?
Irradiation is the amount of solar energy that hits a surface. In photo-voltaic power plants, irradiation is measured in kWh/m2. We operate with three different sets of numbers on irradiation: **[actual irradiation](#actual-irradiation), [estimated irradiation](#estimate-irradiation) and [budgeted irradiation](#)**.

## Actual irradiation
Irradiation is measured by irradiation sensors. Irradiation is measured in 10 minutes intervals, and irradiation as measured value is stored in data warehouse. Irradiation can be corrected in manual correction page [Irradiation Correction](../../../user_interfaces/manual/irradiation_correction.md).


# Incline Irradiation

Incline irradiation is calculated from incline irradiation pyranometer sensors as first source. Sensors are filtered according to rules in [Weather sensor filtering](../../data_filtering/weather_sensor_filtering.md)

If data is missing for a period, data is backfilled from external data source. 

Incline irradiation for east/west oriented plants are calculated as the weighted average of east and west oriented irradiation (Weighted by nominal power in east and west direction)


## Horizontal Irradiation

Horizontal irradiation is calculated from horizontal irradiation pyranometer sensors as first source. 
Sensors are filtered according to rules in [Weather sensor filtering](../../data_filtering/weather_sensor_filtering.md).

If data is missing for a period, data is backfilled from external data source. 

## Budget Irradiation

Budgeted incline irradiation for a plant. Internal budget is default used.

See [Budget data](../../../data_collection/budget_data.md)