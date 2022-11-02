# Plant Availability Calculation

The inverter state is used for plant availability calculations. A inverter state in the class Failure Time or Idle Time, reduces the availability and is defined as Non-Operational time. The percentage of state time for these state classes within a period defines the availability value. The availability is calculated as sum of all inverters.

Following is definition of the different plant availability KPI's:

1. Plant availability daylight (PAd) =1 - Sum downtime inverters at daylight / Sum daylight time
2. Plant availability full day (PAt) = 1 - Sum downtime inverters full day / Sum time full day
3. Plant availability production lost = 1- Production Lost Inverters / EAdjGross = 1- Production Lost Inverters / (Production measured + Production Lost Grid +Production Lost Inverters)

Definition of factors:

* Sum daylight time:
    * Calculated based on all states not having class “Not scheduled”
    * E.g. “No power production”
* Sum downtime inverters at daylight
    * Total down time.
    * Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time”
* Sum time full day
    * Total time for period
* Sum downtime inverters full day
    * Total down time 24/7
    * Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time” or when state code>10000 (e.g. Stop, no power production)
* Production measured
    * From energy meters, manually adjusted if necessary
* Production Lost Grid, Production Lost Inverters
    * Production lost due to downtime on the grid and the inverters, see previous chapter
    