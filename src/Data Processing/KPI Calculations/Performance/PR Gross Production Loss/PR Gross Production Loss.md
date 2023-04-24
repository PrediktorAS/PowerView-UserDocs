# PR Gross Production Loss

Uses PR net as basis, but production is using measured production + production losses due to downtime for grid/inverter + curtailment losses.

- PR Gross Prod Loss = E_Meas_Loss * Is / Pnom / Iacc
    - E_Meas_Loss: Measured energy production, manually adjusted if necessary + production loss due to inverters and grid downtime
        - E_Meas_Loss = [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) + [Grid Downtime production Loss](../../Production%20Losses/Grid%20down%20time%20production%20losses/Grid%20down%20time%20production%20losses.md) + [Plant Downtime Production Loss](../../Production%20Losses/Plant%20down%20time%20production%20losses/Plant%20down%20time%20production%20losses.md) + [Curtailment Production Loss](../../Production%20Losses/Curtailment%20production%20losses/Curtailment%20production%20losses.md) 
    - Is: Irradiance at standard test conditions, constant 1000 W/m2
    - Pnom: nominal DC power of plant
    - Iacc: [Incline Irradiation](../../Yield%20and%20Weather/Incline%20Irradiation/Incline%20Irradiation.md)
      

