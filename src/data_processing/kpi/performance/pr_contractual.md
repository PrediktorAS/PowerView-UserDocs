# Performance Ratio Contractual Bonus and LD

The Contractual PR formula is in general customer and project specific, so the formula below is a generic formula included where no specific formula is present.

## Formula

> PR Contractual = ( E_Meas * Is ) / ( Pnom * Xd * Iacc * Kd * A )

### Variables
- `E_Meas`: [Actual Production](../yield_and_weather/actual_production.md)
- `Is`: Irradiance at standard test conditions, constant 1000 W/m2
- `Xd`: Module degradation factor, see formula below <!--- TODO: Where is the "formula below?" -->
- `Pnom`: Nominal DC power of plant (sum of installed panels)
- `Kd`: Plant loss factor for losses outside operator control - grid outages, curtailment and manual corrected losses. See formula below
- Manual correction factor: factor from 0-1 edited in screen [Production Correction Factor](../../../user_interfaces/manual/production_correction_factor.md) <!--- What is this related to the formula above? -->
    - `IAcc`: Accumulated [Incline Irradiation](../../../user_interfaces/manual/irradiation_correction.md) (plant value from sensors or backfilled from external weather source)
    - `A`: Implied warranted plant availability as per contract

### Plant Loss Factor (`Kd`) formula
> Kd = `E_Meas` / ( `E_Meas` + `Curtailment Production Loss` + `Grid Downtime Production Loss` + `Other excluded losses` )
- `E_Meas`: [Actual Production](../yield_and_weather/actual_production.md)
- `Curtailment Production Loss`: [Curtailment Production Loss](../production_losses/curtailment_production_losses.md)
- `Grid Downtime Production Loss`: [Grid Downtime Production Loss](../production_losses/grid_down_time_production_losses.md)
- `Other excluded losses`: E_meas * (1 – Manual correction factor)  / Manual correction factor
