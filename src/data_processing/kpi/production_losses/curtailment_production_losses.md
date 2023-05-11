# Production Losses due to Curtailment

Curtailment is a reduction in the production of electricity implemented by the plant operator. Curtailment can be due to grid constraints, plant constraints or other reasons.

Curtailment losses can be calculated in two ways (explained below):
- Standard calculation based on [Estimated Production](../yield_and_weather/estimated_production.md)
- Inverter-reference based production estimation

## Standard estimation

Curtailment losses are calculated for each 10 minute period based on registered curtailment periods. Curtailment is registered as state 6006 on [grid state](../../../data_collection/equipment_states/grid.md).

For each period, estimated production is calculated based on measured irradiation and available nominal power. The difference between estimated and measured value is defined as the losses.

#### Calculations
> Curtailment losses = ([Estimated Production](../yield_and_weather/estimated_production.md) * [AdjustmentFactor](./#adjustment-factor)) - [Actual Production](../yield_and_weather/actual_production.md) 

If measured power is not close to the curtailment limit, the losses are set to 0. Detection limit is 95%, meaning measured power on PPC (or PPC power analyser) must be more than 95% of PPC active power setpoint value to calculate losses. If PPC active power setpoint value is 0, curtailment losses also calculated.
 
## Inverter reference based production
<!-- TODO: Where can the reference inverters be specified? -->
A set of reference inverters can be specified for each site. These inverters will produce at full capacity (not curtailed) during plant curtailment and thus used as reference to calculate the theoretical production for the plant.
To get the total plant production, ratio between full production and reference inverter production is calculated for the last 7 days to scale up inverter production.

#### Calculations
> Curtailment Losses = [E_estimatedRefInverters](#calculations-for-e_estimatedrefinverters) - [Actual Production](../yield_and_weather/actual_production.md)

##### Calculations for E_estimatedRefInverters
> E_estimatedRefInverters = E_RefInverters * RollingScalingFactor

- `E_RefInverters`: The measured total energy of the reference inverters 
- `RollingScalingFactor` = [Actual Production](../yield_and_weather/actual_production.md) / `E_RefInverters` for the last 7 days (rolling), during times without curtailment