# PR Gross Production Loss

Uses PR net as basis, but production is using measured production + production losses due to downtime for grid/inverter + curtailment losses.

- PR Gross Prod Loss = E_Meas_Loss * Is / Pnom / Iacc
    - E_Meas_Loss: Measured energy production, manually adjusted if necessary + production loss due to inverters and grid downtime
        - E_Meas_Loss = [Actual Production](../yield_and_weather/actual_production.md) + [Grid Downtime production Loss](../production_losses/grid_down_time_production_losses.md) + [Plant Downtime Production Loss](../production_losses/plant_down_time_production_losses.md) + [Curtailment Production Loss](../production_losses/curtailment_production_losses.md) 
    - Is: Irradiance at standard test conditions, constant 1000 W/m2
    - Pnom: nominal DC power of plant
    - Iacc: [Incline Irradiation](../yield_and_weather/incline_irradiation.md)
      

