# Production

## What is the production?
In photo-voltaic power plants, production is the amount of energy produced by the plant. Production is measured in Wh. We operate with three different sets of numbers on production: **[actual production](#actual-production), [estimated production](#estimate-production) and [budgeted production](#budgeted-production)**.

## Actual production
A plant's production is calculated from counters on energy meters. Energy counter is split in 10 minutes intervals, and production as difference in counter at start and end of interval is calculated and stored in data warehouse. Plant production can be corrected in manual correction page [Production Correction](../../../user_interfaces/manual/production_correction.md).

## Estimated production
To calculate the estmated production, you first need to calculate the estimated DC Power which will allow you to estimate the AC Power, which again can lead you to the estimate total production. Nominal values are used for some of the factors, while others are measured or calculated. Estimated production is calculated for each 10 minute interval and stored in data warehouse. it is, amongst other things, used for loss calculations.

##### Estimated DC Power
Estimated DC power from pv plant

> EstimatedDCPower = `NominalDCPower` * ([Incline Irradiation](irradiation.md) / 1000) * (1 - `TemperatureLosses`) * (1 - `InverterDCLosses`) * `ModuleEfficiency`

###### Variables

- `NominalDCPower`: nominal DC power for plant as defined per plant in plant setup (for E/W using inverters with same orientation)
- `InclineIrradiation`: Incline Irradiation measurements (SolarGIS data if not present) (for E/W using inverters with same orientation)
- `TemperatureLosses`: Module temperature loss factor as calculated (see below)
- `InverterDCLosses`: loss factor on inverter DC side as defined in plant setup
- `ModuleEfficiency`: Efficiency of module at irradiation level. Taken from module type efficiency curve with irradiation vs. efficiency steps

> `TemperatureLosses` = ([Estimated cell temperature](module_temperature.md) - 25) * (`ModuleTempCoeff` / 100)
- `ModuleTempCoeff`: module temperature coefficient as defined in plant setup

##### Estimated AC Power
Estimated AC power delivered to grid

> EstimatedACPower = [EstimatedDCPower](#estimated-dc-power) * `InverterEfficiency` * (1- `InverterMiscLosses`) * (1 – `PlantMiscLosses`)

###### Variables
- `InverterEfficiency`: Efficiency of inverter at power level. Taken from inverter type efficiency curve with DC power vs. efficiency steps
- `InverterMiscLosses`: misc losses factor as defined per plant in plant setup
- `PlantMiscLosses`: loss factor from inverter to grid as defined per plant in plant setup 

##### Estimate Production
Estimated production per 10 minute periods used for loss calculations are calculated based on following algorithm:

> Estimated Production = time integration (EstimatedACPower)


## Budgeted production
Budgeted production is manually set on a [per plant level and in kWh](../../../data_collection/budget_data.md).
