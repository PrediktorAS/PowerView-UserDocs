# Estimated Production

Estimated production per 10 minute periods used for loss calculations are calculated based on following algorithm:
- Estimated Production = time integration (EstimatedACPower)

- EstimatedACPower = EstimatedDCPower * InverterEfficiency * (1- InverterMiscLosses) * (1 – PlantMiscLosses)

- EstimatedDCPower = NominalDCPower * ([Incline Irradiation](../Incline%20Irradiation/Incline%20Irradiation.md) / 1000) * (1 - TemperatureLosses) * (1 - InverterDCLosses) * ModuleEfficiency
    - TemperatureLosses = ([Estimated cell temperature](../Module%20Temperature/Module%20Temperature.md) - 25) * (ModuleTempCoeff / 100)

Parameters and measures:
- EstimatedACPower: estimated AC power to grid
- EstimatedDCPower: estimated DC power from pv plant
- InverterEfficiency: Efficiency of inverter at power level
    - Taken from inverter type efficiency curve with DC power vs. efficiency steps
- InverterMiscLosses: misc losses factor as defined per plant in plant setup
- PlantMiscLosses: loss factor from inverter to grid as defined per plant in plant setup  
- NominalDCPower: nominal DC power for plant as defined per plant in plant setup  
    - for E/W using inverters with same orientation
- InclineIrradiation: Incline Irradiation measurements (SolarGIS data if not present) 
    - for E/W using inverters with same orientation
- TemperatureLosses: Module temperature loss factor as calculated 
- InverterDCLosses: loss factor on inverter DC side as defined in plant setup
- ModuleEfficiency: Efficiency of module at irradiation level
    - Taken from module type efficiency curve with irradiation vs. efficiency steps
- CellTemperature: estimated cell temperature based on measured module temperature and irradiation
- ModuleTemperatureMeasured: Module temperature measured
    - for E/W using inverters with same orientation
- ModuleTempCoeff: module temperature coefficient as defined in plant setup
