# PR Contractual Bonus and LD

Contractual PR formula is in general curstomer and project specific.

General formula included is as below.

- PR Contractual = ( E_Meas * Is ) / ( Pnom * Xd * Iacc * Kd * A )
    - E_Meas: Measured energy production
    - Is: Irradiance at standard test conditions, constant 1000 W/m2
    - Xd: module degradation factor, see formula below
    - Pnom: nominal DC power of plant (sum of installed panels)
    - Kd: plant loss factor for losses outside Scatec control - grid outages, curtailment and manual corrected losses
        - Kd = E_Meas / ( E_Meas + Production Loss Curtailment + Production Loss Grid + Other excluded losses )
            - Production Loss Grid
            - Production Loss Curtailment
            - Other excluded losses = E_meas * (1 – Manual correction factor)  / Manual correction factor
    - Manual correction factor: factor from 0-1 edited in screen “Production adjustment factor” per plant and day
        - IAcc: accumulated incline irradiation (plant value from sensors or backfilled from external weather source)
        - A: Implied warranted plant availability as per contract
