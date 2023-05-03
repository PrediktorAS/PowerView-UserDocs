# Plant availability

Plant availability is calculated in three ways:
1.	Plant availability daylight = Sum daylight time - Sum downtime inverters at daylight / Sum daylight time
2.	Plant availability full day = Sum time full day - Sum downtime inverters full day / Sum time full day
3.	Plant availability production loss = (E_meas_gross - Production Loss Inverters) / E_meas_gross

Definition of factors:
-	Sum daylight time:
    - Calculated based on all states not having class “Not scheduled”, e.g. “No power production”
-	Sum downtime inverters at daylight
    - Total down time inverters, weighted based on inverter nominal DC power.  
    - Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time”
-	Sum time full day
    - Total time for period
-	Sum downtime inverters full day 
    - Total down time 24/7, weighted based on inverter nominal DC power.  
    - Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time” or when state code>10000 (e.g. Stop, no power production)
-	E_meas_gross = [Actual production](../yield_and_weather/actual_production.md) + [Grid Downtime Production Losses](../production_losses/grid_down_time_production_losses.md) + [Plant Downtime Production Losses](../production_losses/plant_down_time_production_losses.md) 


For states see [Inverter States](../../../data_collection/equipment_states/inverter.md)