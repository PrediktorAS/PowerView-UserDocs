# Data filtering
Data is filtered in reports based on raw measurement data from plant logging.
## Weather sensor filtering
All weather data read with bad quality from sensor (e.g. due to comm problems) will be rejected. In addition, below filtering applies.
### Filtering with out-of-order status
Sensors can be configured as out of order in user interface. These values are set to bad and not used in plant data calculations.
### Statistics filtering
Remove points when the absolute value of the median is within interval X and point is more than Y% away from median. The median value calculated is the “continuous” median, that is not necessary one of the sample values if it is an even number of sensors.
Remove points outside interval Z
• Ambient Temperature (°C)
o X={2;~} °C , Y=50%
o Z={-100 ; 100}
• Module Temperature (°C)
o X={2;~} °C , Y=50%
o Z={-100 ; 100}
• Wind Speed (m/s)
o X={1;~} m/s, Y=50%
o Z={0 ; 100}
• Horizontal Irradiation Pyranometer (W/m2)
o Remove points < 5 W/m2 when power is above 5% of nominal power
o Remove points > 10 W/m2 when median is below 5 W/m2
o X={5;~} W/m2, Y=50%
o Z={0 ; 1500}
• InCline Irradiation Pyranometer (W/m2)
o Remove points < 5 W/m2 when power is above 5% of nominal power
o Remove points > 10 W/m2 when median is below 5 W/m2
o X={5;~} W/m2, Y=50%
o Z={0 ; 1500}
• Reference cells (W/m2)
o Z={0 ; 1500}
• Soiling index (%)
o Z={0 ; 20}
• WindDirection (°)
o Z={0 ; 360}
• Humidity (%)
o Z={0 ; 200}
• Rain intensity (mm/h)
o Z={0 ; 500}
### Incline irradiaiton tracker filtering
Incline irradiation values from pyranometer are removed based on status of connected tracker. If state is Idle or Failure (see chapter 3.1.3) on tracker pyranometer values is marked with bad quality and not included in plant average value.
Connected tracker is configured in screen as shown below. Tracker filtering can be disabled using checkbox in screen. This can be done if status signal of tracker is not reliable.
### Weather data filtering reporting
Data quality is stored in data warehouse and can be reported using “weather data details” report as shown below.
### Backfilling irradiation data with data interpolation
If irradiation data is missing for shorter periods for a site, the data missing is backfilled with interpolated data. This goes for both incline and horizontal irradiation.
This can be the result of e.g. all values being removed from the median filtering.
Periods of 90 minutes or less with missing data is backfilled.
Algorithm uses is a linear interpolation of the irradiation values from start to end of the interval.
### Backfilling data from external weather source
If weather sensor data is missing, it is backfilled from external weather data. This is true for the following parameters:
• Incline Irradiation
o If horizontal irradiation data exists, TF is calculated from the external data and incline irradiation calculated based on measured horizontal irradiation and TF from external data: incline irradiation = horizontal irradiation * TF
o If both incline and horizontal irradiation is missing, value is filled directly
• Horizontal Irradiation
o If incline irradiation data exists, TF is calculated from the external data and horizontal irradiation calculated based on measured incline irradiation and TF from external data: horizontal irradiation = incline irradiation / TF
o If both incline and horizontal irradiation is missing, value is filled directly
• Wind Speed
• Wind Direction
• Ambient Temperature
• Module Temperature
o Calculated from ambient temperature and horizontal irradiation using formula:
▪ Module temperature = Ambient Temperature + (Incline Irradiation / 800) * 25
• Air Pressure
• Humidity
• Rain Amount
## Meter data filtering
Obviously wrong active energy meter readings are filtered out and not added to data warehouse database using following algorithm:
• Calculate max possible production from last 10-minute period production was more than 0
o Use nominal AC power for plant and time since last energy registration on meter
• Add 50 % as safety margin
• If above this limit, reject value.
### Meter data filtering reporting
Weekly mail is sent to stakeholder, summarizing rejected meter values.