# PR Contractual Bonus and LD

Contractual PR formula is in general curstomer and project specific.

General formula included is as below.

- PR Contractual = ( E_Meas * Is ) / ( Pnom * Xd * Iacc * Kd * A )
    - E_Meas: [Actual Production](../yield_and_weather/actual_production.md)
    - Is: Irradiance at standard test conditions, constant 1000 W/m2
    - Xd: module degradation factor, see formula below
    - Pnom: nominal DC power of plant (sum of installed panels)
    - Kd: plant loss factor for losses outside operator control - grid outages, curtailment and manual corrected losses
        - Kd = E_Meas / ( E_Meas + [Curtailment Production Loss](../production_losses/curtailment_production_losses.md) + [Grid Downtime Production Loss](../production_losses/grid_down_time_production_losses.md) + Other excluded losses )
            - [Curtailment Production Loss](../production_losses/curtailment_production_losses.md)
            - [Grid Downtime Production Loss](../production_losses/grid_down_time_production_losses.md)
            - Other excluded losses = E_meas * (1 – Manual correction factor)  / Manual correction factor
    - Manual correction factor: factor from 0-1 edited in screen [Production Correction Factor](../../../../User%20Interfaces/Manual%20Data%20Registration/Production%20Correction%20Factor/Production%20Correction%20Factor.md)
        - IAcc: accumulated [Incline Irradiation](../../../../User%20Interfaces/Manual%20Data%20Registration/Irradiation%20Correction/Irradiation%20Correction.md) (plant value from sensors or backfilled from external weather source)
        - A: Implied warranted plant availability as per contract
