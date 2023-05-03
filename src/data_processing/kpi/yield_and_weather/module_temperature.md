# Module Temperature

Different module temperature KPI’s are present in the system based on measurement and calculations:
1.	Module temperature: average of measured module temperature sensors
2.	Module temperature daylight: average of measured module temperature sensors during daylight, that is when irradiation is above 5 W/m2
3.	Estimated cell temperature:  average of estimated cell temperature calculated from measured module temperature and incline irradiation measurements
4.	Estimated cell temperature daylight: average of estimated cell temperature during daylight
5.	Estimated cell temperature daylight weighted : irradiation weighted average of estimated cell temperature during daylight 

##	Module temperature
Module temperature measured from each sensor is used as basis. It is filtered according to algorithm in [Weather sensor filtering](../../data_filtering/weather_sensor_filtering.md) and stored per 10 minute period in data warehouse. When reported, all values for a day are used.

If all module temperature from sensors are missing, values from external satellite weather source is used. Module temperature is then calculated based on formula:
Module temperature = Ambient Temperature + (Incline Irradiation / 800) * 25

##	Module temperature daylight
Average value calculated base on the “Module Temperature”. Only 10 minute values with incline irradiation above 5 W/m2 is used in average.

##	Estimated cell temperature
This is a calculated value based on measured module temperature and incline irradiation measurements:
Estimated cell temperature = Module Temperature + 3*( Incline Irradiation) / 1000
Value calculated per 10 minute interval and input to the algorithm is 10 minute values for plant filtered as in [Weather sensor filtering](../../data_filtering/weather_sensor_filtering.md).

##	Estimated cell temperature daylight
Average value calculated base on the “Estimated cell temperature” values. Only 10 minute values with incline irradiation above 5 W/m2 is used in average.

##	Estimated cell temperature daylight weighted 
Irradiation weighted average of estimated cell temperature during daylight. Input is the 10 minute "Estimated cell temperature daylight" values. Average value for a period is weighted based on incline irradiation measurements. Used in KPI calculations and labeled “Cell temperature, Daylight” in reports
Estimated cell temperature daylight weighted = (Estimated cell temperature daylight * Incline Irradiation) / sum(Incline Irradiation)
