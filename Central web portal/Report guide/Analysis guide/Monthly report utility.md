# Monthly report utility

The monthly report utility contains data aggregated for a month for a specific plant adapted to utility needs.

Input parameter:

* Month

Report elements:

* Production table
    * Feed in active energy (MWh): shows data for each main energy meter and total for plant
    * Feed in re-active energy (MVArh): shows data for each main energy meter and total for plant
    * Total production manually adjusted: production number adjusted manually (default same as meter values)
* Production per day graph
    * Active feed-in energy production. The adjusted production value is shown. Bar graph per day.
* Production per day table
* Accumulated incline irradiation per day
    * kWh/m2 values, aggregated based on the average incline irradiation measurement from the incline pyranometers
* Temperature per day 
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
        * Grid availability measured (%):  calculated based on Grid state.
    * Grid availability calculation per day in graph calculated based on Grid state
* Inverter non-operation
    * Table with summarized non-operational time per inverter
    * Shown as minutes, time span and percentage
* Grid/facility non-operation
    * Table with all non-operational time periods for grid
    * Period duration shown as minutes, time span and percentage
* Tracker non-operation (only for plants with trackers)        
    * Table with summarized non-operational time for period per tracker
    * Shown as minutes, time span and percentage
          