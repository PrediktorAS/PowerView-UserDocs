# Tracker report

The tracker report contains data for trackers for a specific plant. This report exist only for plants with trackers.

Input parameter:   

* Start and End period: used if not period is used. Un-check both boxes before use.
* Period type and period: select report period if not start and end time is used
* Report description: used in the heading of the report

Report elements:

* Tracker availability
    * Availability table for whole period
        * Non-operational time (minutes): total non operation time for trackers, summed up for month based on Tracker state. Failure time and idle time are counted as non-operational time. See also Tracker availability calculation
        * Non-operational time (dd hh:mm:ss): Same as above but presented as days, hours, minutes and seconds
        * Grid availability measured (%):  calculated based on Tracker state. See also Tracker availability calculation
    * Tracker availability calculation per day in graph calculated based on Tracker state
* Tracker non-operation per tracker   
    * Table with summarized non-operational time for period per tracker
    * Shown as minutes, time span and percentage
* Tracker non-operation details
    * table showing each non-operational time period
    * Shows start time, end time, duration and comment (if added manually
