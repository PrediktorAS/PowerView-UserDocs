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
- E_meas_gross = [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) + [Grid Downtime production Loss](../../Production%20Losses/Grid%20down%20time%20production%20losses/Grid%20down%20time%20production%20losses.md) + [Plant Downtime Production Loss](../../Production%20Losses/Plant%20down%20time%20production%20losses/Plant%20down%20time%20production%20losses.md) + [String Downtime Production Loss](../../Production%20Losses/String%20down%20time%20production%20losses/String%20down%20time%20production%20losses.md) + [Curtailment Production Loss](../../Production%20Losses/Curtailment%20production%20losses/Curtailment%20production%20losses.md) + [Clippping Production Loss](../../Production%20Losses/Clipping%20production%20losses/Clipping%20production%20losses.md) + [Soiling Production Loss](../../Production%20Losses/Soiling%20production%20losses/Soiling%20production%20losses.md) + [Snow Production Loss](../../Production%20Losses/Snow%20production%20losses/Snow%20production%20losses.md) + [Tracker Downtime Production Loss](../../Production%20Losses/Tracker%20down%20time%20production%20losses/Tracker%20down%20time%20production%20losses.md)
- Power availability on tracker
    - Factor from 0-1. Removing unavailable power due to string and inverter downtime

For states and classes see [Equipment States](../../../../Data%20Collection%20&%20Data%20Flow/Equipment%20States/Equipment%20States.md) and [Tracker States](../../../../Data%20Collection%20&%20Data%20Flow/Equipment%20States/Tracker/Tracker.md)

