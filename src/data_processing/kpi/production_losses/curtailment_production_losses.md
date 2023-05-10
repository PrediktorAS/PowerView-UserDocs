# Production Losses due to Curtailment

Curtailment is a reduction in the production of electricity implemented by the plant operator. Curtailment can be due to grid constraints, plant constraints or other reasons.

Curtailment losses are calculated for each 10 minute period based on registered curtailment periods. Curtailment is registered as state 6006 on [grid state](../../../data_collection/equipment_states/grid.md).

For each period, estimated production is calculated based on measured irradiation and available nominal power. The difference between estimated and measured value is defined as the losses.

## Calculations
> Curtailment losses = ([Estimated Production](../yield_and_weather/estimated_production.md) * [AdjustmentFactor](./#adjustment-factor)) - [Actual Production](../yield_and_weather/actual_production.md) 


If measured power is not close to the curtailment limit, the losses are set to 0. Detection limit is 95%, meaning measured power on PPC (or PPC power analyser) must be more than 95% of PPC active power setpoint value to calculate losses. If PPC active power setpoint value is 0, curtailment losses also calculated.

