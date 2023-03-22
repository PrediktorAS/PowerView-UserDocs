# Curtailment production losses

Curtailment losses are calculated for each 10 minute period based on registered curtailment periods. Curtailment is registered as state 6006 on grid state.

For each period, estimated production is calculated based on measured irradiation and available nominal power. The difference between estimated and measured value is defined as the losses.

Curtailment losses = (E_est * AdjustmentFactor) - E_meas 
- E_meas: 
    - measured plant energy production for period of curtailment
- E_est: 
    - Estimated production based on standard plant model
    - Cut on max nominal AC power on plant. Estimated production above nominal power is classified as clipping losses
- AdjustmentFactor
    - Adjustment factor is calculated based on estimated production and measured production last 60 minutes before curtailment starts
        - AdjustmentFactor = E_meas / E_est
- E_meas and E_est as above

If measured power is not close to the curtailment limit, the losses are set to 0. Detection limit is 95%, meaning measured power on PPC (or PPC power analyser) must be more than 95% of PPC active power setpoint value to calculate losses. If PPC active power setpoint value is 0, curtailment losses also calculated.

