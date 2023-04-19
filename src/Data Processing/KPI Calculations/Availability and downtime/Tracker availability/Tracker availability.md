# Tracker availability
Following calculation applies:

1.	Tracker availability daylight (TAd) = (Sum daylight time trackers  - Sum downtime trackers) / Sum daylight time trackers
2.	Tracker availability full day (TAt) = (Sum time full day - Sum downtime trackers) / Sum time full day
3.	Tracker availability production loss = E_meas_gross / (E_meas_gross + Production Loss Tracker)
4.	Tracker availability for production loss calculation (TAprodloss) = (Sum time full day – (Sum downtime trackers * Power availability on tracker)) / Sum time full day

Definition of factors:
- Sum downtime trackers
    - Total down time. Down time is calculated as sum of periods when tracker state is in state classes “Idle time” or “Failure time”. Will only happen during day time.
- Sum daylight time trackers:
    - Calculated based on all states not having class “Not scheduled”
    - E.g. “No power production”
- Sum time full day
    - Total time for period.
- E_meas_gross = E_meas + Production Loss Grid + Production Loss Inverters + Production Loss String + Production Loss Curtailment + Production Loss Clippping + Production Loss Soiling + Production Loss Snow + Production Loss Tracker
-	E_meas: measured actual production for plant
    - Production Loss Grid
    - Production Loss Inverters
    - Production Loss Tracker
    - Production Loss String
    - Production Loss Soiling
    - Production Loss Curtailment
    - Production Loss Clipping
    - Production Loss Snow
- Power availability on tracker
    - Factor from 0-1. Removing unavailable power due to string and inverter downtime

