# Availability Details

Result and sub parameters of availability calculations, based on plant formula.

Data is caclulated for a time period and presented as numbers.

Input parameter:

* Start and End period: used if not period is used. Un-check both boxes before use.
* Period type and period: select report period if not start and end time is used
* Report description: used in the heading of the report

Report elements:

* Plant availability: 
    * Total inverter down time (minutes): total down time for all inverters in sum (Failure and idle time) from state registration
    * Total inverter time (minutes): total inverter time as sum 
    * Plant availability (%): plant availability, as Total inverter down time as percent of total inverter time
    * Plant availability nominal (%): Nominal availability set in plant parameters
* Grid/facility availability:
    * Total down time grid (minutes) : total grid down time from state registration
    * Total grid time (minutes): total time
    * Grid availability (%): grid availability calculated as total down time as percentage of total time
* Inverter non-operation per inverter: Sum of non-operational time per inverter
* Inverter non-operation details: each non-operational time period for each inverter
* Grid/facility non-operation details: each grid non-operational state
