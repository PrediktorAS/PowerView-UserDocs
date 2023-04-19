# Incline Irradiation

Incline irradiation is calculated from incline irradiation pyranometer sensors as first source. Sensors are filtered according to rules in [Weather sensor filtering](../../../Data%20Filtering/Weather%20Sensor%20Filtering/Weather%20Sensor%20Filtering.md)

If data is missing for a period, data is backfilled from external data source. 

Incline irradiation for east/west oriented plants are calculated as the weighted average of east and west oriented irradiation (Weighted by nominal power in east and west direction)
