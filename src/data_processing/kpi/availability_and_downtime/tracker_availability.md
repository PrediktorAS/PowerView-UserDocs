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
- E_meas_gross = [Actual Production](../yield_and_weather/production.md) + [Grid Downtime production Loss](../production_losses/grid_down_time_production_losses.md) + [Plant Downtime Production Loss](../production_losses/plant_down_time_production_losses.md) + [String Downtime Production Loss](../production_losses/string_down_time_production_losses.md) + [Curtailment Production Loss](../production_losses/curtailment_production_losses.md) + [Clipping Production Loss](../production_losses/clipping_production_losses.md) + [Soiling Production Loss](../production_losses/soiling_production_losses.md) + [Snow Production Loss](../production_losses/snow_production_losses.md) + [Tracker Downtime Production Loss](../production_losses/tracker_down_time_production_losses.md)
    
- Power availability on tracker
    - Factor from 0-1. Removing unavailable power due to string and inverter downtime

For states and classes see [Equipment States](../../../data_collection/equipment_states/) and [Tracker States](../../../data_collection/equipment_states/tracker.md)
