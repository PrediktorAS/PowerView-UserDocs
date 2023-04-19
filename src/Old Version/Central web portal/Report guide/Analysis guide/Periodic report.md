# Periodic report

The periodc report contains data aggregated for a period for a specific plant. Report is found in menu for each plant.

The report has a common template adapted to each plant.

Input parameter:

* Period type and period: select report period if not start and end time is used
* Report description: used in the heading of the report
* Continent: filter continent
* Country: filter country
* Facility: select plant
* Report description: title for report

Report elements:

* Production table
    * Feed in active energy (MWh): shows data for each main energy meter and total for plant
    * Feed in re-active energy (MVArh): shows data for each main energy meter and total for plant
    * Total production manually adjusted: production number adjusted manually (default same as meter values)
* Production per day graph
    * Active feed-in energy production. The adjusted production value is shown. Bar graph per day.
* Performance ratio
    * Performance ratio value for whole month
    * Performance ratio per day in graph
* Accumulated incline irradiation per day
    * kWh/m2 values, aggregated based on the average incline irradiation measurement from the incline pyranometers
* Environment temperature per day
    * Min, max and average environment temperature for each day, based on average 10 minute measurements from weather stations 
* Rain amount per day
    * Accumulated rain amount based on rain intensity. Sum of 10 minute values.
* Plant availability
    * Availability table for whole month
        * Non-operational time (minutes): total non operation time for inverters, summed up for month based on Inverter state. Failure time and idle time are counted as non-operational time. See also Plant availability calculation
        * Non-operational time (dd hh:mm:ss): Same as above but presented as days, hours, minutes and seconds
        * Plant availability measured (%): plant availability calculated based on Inverter state
        * Contractual availability (%): contractual availability for plant set in Plant parameters general
    * Plant availability per day in graph calculated based on Inverter state
* Grid availability
    * Availability table for whole month
        * Non-operational time (minutes): total non operation time for grid, summed up for month based on Grid state. Failure time and idle time are counted as non-operational time. See also Grid availability calculation
        * Non-operational time (dd hh:mm:ss): Same as above but presented as days, hours, minutes and seconds
        * Grid availability measured (%):  calculated based on Grid state.
    * Grid availability calculation per day in graph calculated based on Grid state
* Tracker availability (only for plants with trackers)
    * Availability table for whole month
        * Non-operational time (minutes): total non operation time for trackers, summed up for month based on Tracker state. Failure time and idle time are counted as non-operational time. See also Tracker availability calculation
        * Non-operational time (dd hh:mm:ss): Same as above but presented as days, hours, minutes and seconds
        * Grid availability measured (%):  calculated based on Tracker state. See also Tracker availability calculation
    * Tracker availability calculation per day in graph calculated based on Tracker state
* Inverter non-operation
    * Table with summarized non-operational time per inverter
    * Shown as minutes, time span and percentage
* Grid/facility non-operation
    * Table with all non-operational time periods for grid
    * Period duration shown as minutes, time span and percentage
* Tracker non-operation (only for plants with trackers)        
    * Table with summarized non-operational time for period per tracker
    * Shown as minutes, time span and percentage
