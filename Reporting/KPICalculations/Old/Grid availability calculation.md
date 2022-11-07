# Grid Availability Calculation

The grid state is used for grid availability calculations. A grid state in the class Failure Time, Idle Time or Line Restraint Time, reduces the availability and is defined as Non-Operational time. The percentage of state time for these state classes within a period defines the availability value.

The following formulas apply for grid availability:

1. Grid availability daylight (GAd) = (Sum daylight time - Sum downtime grid at daylight) / Sum daylight time
2. Grid availability full day (GAt) = (Sum time full day - Sum downtime grid full day) / Sum time full day
3. Grid availability production lost = 1 – Production Lost Grid / (Production measured + Production Lost Grid +Production Lost Inverters)

Definition of factors:

* Sum daylight time:
    * Calculated based on all states not having class “Not scheduled”
    * E.g. “No power production”.
* Sum downtime inverters at daylight
    * Total down time.
    * Down time is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint”
* Sum time full day
    * Total time for periodSum downtime inverters full day
    * Total down time 24/7
    * Down time is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint” or when state code>10000 (e No power production, grid down)
* Production measured
    * From energy meters, possible manually adjusted
* Production Lost Grid, Production Lost Inverters
    * Production lost due to downtime on the grid and the inverters, see previous chapter 
 
For PR Gross calculation, a special formula is used (GAdg- Grid availability daylight gross). When grid is down, it might be that there is no irradiation measurement present. This will result in grid down time is already counted for in PR by having a reduced accumulated irradiation value for day and thus a higher PR. For the PR Gross, down time and daylight time is therefore only counted when there exist incline irradiation data and when this is above 1W/m2 (this is taken from 10 minute average values in data warehouse).
