# Clipping production losses

Clipping is detected based on detection of output power close to maximum nominal output power. Detecting is done based on measured power on PPC vs. nominal dc power on plant and a per plant adjustment limit. If measured value is above nominal and no curtailment is active, clipping is detected.  
Losses are calculated for each 10 minute period the same way as for curtailment:

Clipping losses = (E_est * AdjustmentFactor) - E_meas 
- E_meas: 
    - measured plant energy production for period of curtailment
- E_est: 
    - Estimated production based on standard plant model
- AdjustmentFactor
    - Adjustment factor is calculated based on estimated production and measured production last 60 minutes before clipping starts
        - AdjustmentFactor = E_meas / E_est
- E_meas and E_est as above

Clipping losses are also detected for period of curtailment, when estimated production is above nominal output on plant. The energy estimated above nominal max output is classified as clipping losses.
