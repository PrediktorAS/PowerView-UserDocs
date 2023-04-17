# PR Gross Production Loss

Uses PR net as basis, but production is using measured production + production losses due to downtime.

- PR Gross Prod Loss = E_Meas_Loss * Is / Pnom / Iacc
    - E_Meas_Loss: Measured energy production, manually adjusted if necessary + production loss due to inverters and grid downtime
        - E_Meas_Loss = E_Meas + Production Loss Inverters + Production Loss Grid + Production Loss Curtailment
            - E_Meas: measured production
            - Production Loss Inverters
            - Production Loss Grid
            - Production Loss Curtailment
    - Is: Irradiance at standard test conditions, constant 1000 W/m2
    - Pnom: nominal DC power of plant
    - Iacc: accumulated irradiation in the module plan
        - If data missing, irradiation for same time previous day is used. 30 days back is checked and 5 first day with irradiation is used

