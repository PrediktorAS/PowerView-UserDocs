# Clipping production losses

Clipping is detected based on detection of output power close to maximum nominal output power. Detecting is done based on measured power on PPC vs. nominal dc power on plant and a per plant adjustment limit. If measured value is above nominal and no curtailment is active, clipping is detected.  
Losses are calculated for each 10 minute period the same way as for curtailment:

Clipping losses = ([Estimated Production](../../Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md) * AdjustmentFactor) - [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) 

- AdjustmentFactor
    - Adjustment factor is calculated based on estimated production and measured production last 10 minutes before clipping starts and first 10 minutes after clipping ends and formula is:
        - AdjustmentFactor = [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) / [Estimated Production](../../Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md)
        - Clipped [-0.95 , 1.05], meaning max +/- 5% adjustment

Clipping losses are also detected for period of curtailment, when estimated production is above nominal output on plant. The energy estimated above nominal max output is classified as clipping losses.
