# Weather sensor filtering

All weather data read with bad quality from sensor (e.g. due to comm problems) will be rejected. In addition, below filtering applies.

##	Filtering with out-of-order status (O)
Sensors can be configured as out of order in manual input screen shown in [Weather Data Correction](../../../User%20Interfaces/Manual%20Data%20Registration/Weather%20Data%20Correction/Weather%20Data%20Correction.md). These values are set to bad and not used in plant data calculations.

Values filtered are labelled as “O” in sensor report

## Statistics filtering (L,M)
Remove points when the absolute value of the median is within interval X and point is more than Y% away from median. The median value calculated is the “continuous” median, that is not necessary one of the sample values if it is an even number of sensors. Removed points labelled “M” in sensor report.

Remove points outside interval Z, labelled “L” in sensor report.
- Ambient Temperature (°C)
    - X={2;~} °C , Y=50%
    - Z={-100 ; 100}
- Module Temperature  (°C)
    - X={2;~} °C , Y=50%
    - Z={-100 ; 100}
- Wind Speed (m/s)
    - X={1;~}  m/s, Y=50%
    - Z={0 ; 100}
- Horizontal Irradiation Pyranometer (W/m2)
    - Remove points < 5 W/m2 when power is above 5% of nominal power
    - Remove points > 10 W/m2 when median is below 5 W/m2
    - X={5;~}  W/m2, Y=50%
    - Z={0 ; 1500}
- InCline Irradiation Pyranometer (W/m2)
    - Remove points < 5 W/m2 when power is above 5% of nominal power
    - Remove points > 10 W/m2 when median is below 5 W/m2
    - X={5;~}  W/m2, Y=50%
    - Z={0 ; 1500}
- Reference cells  (W/m2)
    - Z={0 ; 1500}
- Soiling index (%)
    - Z={0 ; 20}
- WindDirection (°)
    - Z={0 ; 360}
- Humidity (%)
    - Z={0 ; 200}
- Rain intensity (mm/h)
    - Z={0 ; 500}

##	Incline irradiaiton tracker filtering (T)
Incline irradiation values from pyranometer are removed based on status of connected tracker. If state is Idle or Failure (down time) on tracker pyranometer values is marked with bad quality and not included in plant average value. 

Connected tracker is configured in screen as shown below. Tracker filtering can be disabled using checkbox in screen. This can be done if status signal of tracker is not reliable.

Removed points labelled “T0” in sensor report.

##	Weather data filtering reporting 
Data quality is stored in data warehouse and can be reported using “Weather data details” report.
Calculated average and what sensors are used/rejected is shown:

Status Letters:
- "FilterStatus"
    - Blank=no filter
    - L=Limit filter
    - M=Median filter
    - O=sensor out of Order filter
    - T=Tracker malfunction filter

Mail can be sent to stakeholders, summarizing rejected irradiation values.

##	Backfilling data from external weather source
If weather sensor data is missing, it is backfilled from external weather data if that is present in the soluion. This is true for the following parameters:

- Incline Irradiation
    - If horizontal irradiation data exists, TF is calculated from the external data and incline irradiation calculated based on measured horizontal irradiation and TF from external data: incline irradiation = horizontal irradiation * TF
    - If both incline and horizontal irradiation is missing, value is filled directly
- Horizontal Irradiation
    - If incline irradiation data exists, TF is calculated from the external data and horizontal irradiation calculated based on measured incline irradiation and TF from external data: horizontal irradiation = incline irradiation / TF
    - If both incline and horizontal irradiation is missing, value is filled directly
- Wind Speed
- Wind Direction
- Ambient Temperature
- Module Temperature
    - Calculated from ambient temperature and horizontal irradiation using formula: 
        - Module temperature = Ambient Temperature + (Incline Irradiation / 800) * 25
- Air Pressure
- Humidity
- Rain Amount

PS: External weather data is interpolated to 10 minute levels to match the reporting interval.

A correction factor used to align the external weather data. The correction factor is calculated as the relation between the external weather data and measurement for the last 10 days. Only 10 minute periods having both external and actual data is used.
A correction factor is also calculated for transposition factor.
- Cor_XX = Measured / External

The factor is used in the following way for the different parameters:
- Incline irradiation:
    - If horizontal irradiation measurement exists, the correction factor for the transposition factor (Cor_TF) is multiplied with the incline irradiation value derived from the measured horizontal value.
    - If horizontal irradiation measurement does not exist, the correction factor for the incline irradiation measurements (Cor_Inc) are multiplied with the external value. 
- Horizontal irradiation:
    - If incline irradiation measurement exists, the horizontal irradiation value derived from the measured incline irradiation value is divided by the correction factor for the transposition factor (Cor_TF)
    - If incline irradiation measurement does not exist, the external value is divided by the correction factor for the horizontal irradiation measurements (Cor_Hor)
- Other parameters (Wind Speed, Ambient Temperature, Module Temperature, Air Pressure, Humidity, Rain Amount):
    - The external value is multiplied with the correction factor for the measurement type (Cor_XX). 
        - E.g. Temp = External Temp * Cor_Temp

##	Backfilling irradiation data with data interpolation
If irradiation data is missing for shorter periods for a site and external data is missing, the data missing is backfilled with interpolated data. This goes for both incline and horizontal irradiation.

This can be the result of e.g. all values being removed from the median filtering.
Periods of 90 minutes or less with missing data is backfilled.
Algorithm uses is a linear interpolation of the irradiation values from start to end of the interval.
