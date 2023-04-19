# Weather report

Report showing weather data for plant.

Graphs and table.

Input parameter:

* Start and End period: used if not period is used. Un-check both boxes before use.
* Period type and period: select report period if not start and end time is used
* Report description: used in the heading of the report
* Interval: the time interval used within the report period, used for data aggregation

Report elements:

* Temperature data: environment and module temperature as line graph 
* Irradiation data: all irradiation measurement types as average values in line graph
* Accumulated irradiation: accumulated incline irradiation values for facility based on average incline irradiation values from pyranometers
    * Missing and estimated values shown below graph
* Wind direction: average wind direction per interval shown in line graph
* Wind speed: average, min and max wind speed per interval shown in line graph
* Rain amount: accumulated rain amount per interval shown in bar graph
* Humidity: average, min and max humidity per interval shown in line graph
* Air pressure: average, min and max air pressure per interval shown in line graph
* Environment temperature: average, min and max environment temperature per interval shown in line graph
* Measured weather data for all meters: aggregated data per interval for each weather station
