[//]: # (MBo: Fra KPI Calculations.pdf)

# Availability Calculations

This chapter describes how the availability is calculated in the SCADA application. The following availabilities are calculated:

* Plant availability
* Grid availability
* Tracker availability
* String availability

## Plant Availability

Plant availability is calculated in three ways:

1. Plant availability daylight = Sum daylight time - Sum downtime inverters at daylight / Sum daylight time
2. Plant availability full day = Sum time full day - Sum downtime inverters full day / Sum time full day
3. Plant availability production loss = (E_meas_gross - Production Loss Inverters) / E_meas_gross  

Definition of factors:

* Sum daylight time:
  * Calculated based on all states not having class “Not scheduled”, e.g. “No power production”
  * See chapter 3.1.1.
* Sum downtime inverters at daylight
  * Total down time inverters, weighted based on inverter nominal DC power.
  * Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time”
* Sum time full day
  * Total time for period
* Sum downtime inverters full day  
  * Total down time 24/7, weighted based on inverter nominal DC power.
  * Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time” or when state code>10000 (e.g. Stop, no power production)
* E_meas_gross = E_meas + Production Loss Grid +Production Loss Inverters
  * E_meas: measured actual production for plant (see 2.1.1)
  * Production Loss Grid: see 2.2.1
  * Production Loss Inverters: see 2.2.2

## Grid availability

Grid availability is calculated in three ways:

1. Grid availability daylight (GAd) = (Sum daylight time - Sum downtime grid at daylight) / Sum daylight time
2. Grid availability full day (GAt) = (Sum time full day - Sum downtime grid full day) / Sum time full day
3. Grid availability production loss = (E_meas_gross – Production Loss Grid) / E_meas_gross  

Definition of factors:

* Sum daylight time:
  * Calculated based on all states not having class “Not scheduled” (E.g. “No power production”. See chapter 3.1.2.)
* Sum downtime grid at daylight
  * Total down time  
  * Down time is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint”
* Sum time full day o Total time for period
* Sum downtime grid full day  
  * Total down time 24/7  
  * Down time full day is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint” or when state code>10000 (e.g. No power production, grid down)
* E_meas_gross = E_meas + Production Loss Grid + Production Loss Inverters
  * E_meas: measured actual production for plant, see 2.1.1
  * Production Loss Grid: see 2.2.1
  * Production Loss Inverters: see 2.2.2

For PR Gross calculation, a special formula is used:  
    *“Grid availability daylight gross” (GAdg)*
When grid is down, it might be that there is no irradiation measurement present. This will result in grid down time is already counted for in PR by having a reduced accumulated irradiation value for day and thus a higher PR. For the PR Gross, down time and daylight time is therefore only counted when there exist incline irradiation data and when this is above 5 W/m2 (this is taken from 10 minute average values in data warehouse).

## Tracker availability

Following calculation applies:

1. Tracker availability daylight (TAd) = (Sum daylight time trackers  - Sum downtime trackers) / Sum daylight time trackers
2. Tracker availability full day (TAt) = (Sum time full day - Sum downtime trackers) / Sum time full day
3. Tracker availability for production loss calculation (TAprodloss) = (Sum time full day – (Sum downtime trackers * Power availability on tracker)) / Sum time full day  

Definition of factors:

* Sum downtime trackers
  * Total down time. Down time is calculated as sum of periods when tracker state is in state classes “Idle time” or “Failure time”. Will only happen during day time.
* Sum daylight time trackers:
  * Calculated based on all states not having class “Not scheduled” - E.g. “No power production”. See chapter 3.1.3.
* Sum time full day
  * Total time for period.
* Power availability on tracker
  * Factor from 0-1. Removing unavailable power due to string and inverter downtime

## String availability

String availability is calculated based on specific power on each string relative to plant median of specific power.  

When string has between 20% and 60% relative power, 50% availability is set for string. When relative power is below 20%, 0% availability is set on string.

String availability is calculated for the following aggregated periods (not 10 minute periods):

* Morning: 06:00 to 10:00
* Midday: 10:00 to 14:00
* Afternoon: 14:00 to 18:00  
Exception rules are made to not get string downtime when inverter is not producing or tracker is malfunction:

1. Inverter down:
   * When all strings connected to the inverter is down for the period, string availability is set to 100% for all strings on inverter.
2. Tracker down:
   * Tracker availability is calculated for the tracker connected to a string:
     * TrackerDowntimeFactor (0-1) per string:
       * Calculated as average value for morning, midday and afternoon for each string
     * Limit to detect string availability for a string is adjusted according to following formula:
       * 20% *(1 - 0.5*TrackerDowntimeFactor)
       * 60% *(1 - 0.5*TrackerDowntimeFactor)  

String availability for plant is calculated as the weighted average (weighted by nominal power Wp) of availability for all strings.
