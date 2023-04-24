# Grid down time production loss

Grid state is classified into following [Equipment States](../../../../Data%20Collection%20&%20Data%20Flow/Equipment%20States/Equipment%20States.md) classes:
- Production time
- Failure time
- Idle time
- Line restraint time
- Unscheduled

“Failure time”, “Idle time” and “Line restraint time” is counted as down time resulting in reduced plant availability and thus production loss due to down time.

Following algorithm is implemented to estimate production loss:
- Grid down time production loss = [Estimated Production](../../Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md) * AdjustmentFactor

Factors calculated as follows:
- Adjustment factor is calculated based on estimated production and measured production last 10 minutes before grid downtime starts and first 10 minutes after grid downtime ends and formula is:
    - AdjustmentFactor = [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) / [Estimated Production](../../Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md)
    - Clipped [-0.95 , 1.05], meaning max +/- 5% adjustment

 For E/W installations, losses for east and west are calculated separately with incline irradiation and module temperature for each orientation and add together
