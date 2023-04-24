# Curtailment production losses

Curtailment losses are calculated for each 10 minute period based on registered curtailment periods. Curtailment is registered as state 6006 on [grid state](../../../../Data%20Collection%20&%20Data%20Flow/Equipment%20States/Grid/Grid.md).

For each period, estimated production is calculated based on measured irradiation and available nominal power. The difference between estimated and measured value is defined as the losses.

Curtailment losses = ([Estimated Production](../../Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md) * AdjustmentFactor) - [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) 

- AdjustmentFactor
    - Adjustment factor is calculated based on estimated production and measured production last 10 minutes before curtailment starts and first 10 minutes after curtailment ends and formula is:
        - AdjustmentFactor = [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) / [Estimated Production](../../Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md)
        - Clipped [-0.95 , 1.05], meaning max +/- 5% adjustment

If measured power is not close to the curtailment limit, the losses are set to 0. Detection limit is 95%, meaning measured power on PPC (or PPC power analyser) must be more than 95% of PPC active power setpoint value to calculate losses. If PPC active power setpoint value is 0, curtailment losses also calculated.

