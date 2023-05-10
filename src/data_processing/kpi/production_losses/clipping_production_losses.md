# Production Losses due to Clipping

Clipping is detected based on detection of output power close to maximum nominal output power. Detecting is done based on measured power on PPC vs. nominal dc power on plant and a per plant adjustment limit. If measured value is above nominal and no curtailment is active, clipping is detected. Losses are calculated for each 10 minute period the same way as for curtailment:

## Calculations
> Clipping losses = ([Estimated Production](../yield_and_weather/estimated_production.md) * [AdjustmentFactor](./#adjustment-factor)) - [Actual Production](../yield_and_weather/actual_production.md) 

Clipping losses are also detected for period of curtailment, when estimated production is above nominal output on plant. The energy estimated above nominal max output is classified as clipping losses.
