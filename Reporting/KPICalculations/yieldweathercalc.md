[//]: # (MBo: Fra KPI Calculations.pdf)

# Yield and Weather Calculations

## Actual Production

Plant production is calculated from counters on energy meters. Energy counter is split in 10 minutes intervals, and production as difference in counter at start and end of interval is calculated and stored in data warehouse.
Plant production can be corrected in manual correction page “Production adjustment”.

## Estimated Production

Estimated production used for loss calculations are calculated based on following algorithm:

* EstimatedProduction = time integration (EstimatedACPower)
* EstimatedACPower = EstimatedDCPower *InverterEfficiency* (1- InverterMiscLosses) *(1 – PlantMiscLosses)
* EstimatedDCPower = NominalDCPower*(InclineIrradiation / 1000)*(1 - TemperatureLosses)*(1 - InverterDCLosses)*ModuleEfficiency
* TemperatureLosses = (CellTemperature - 25)* (ModuleTempCoeff / 100)
* CellTemperature = ModuleTemperatureMeasured + 3 * (InClineIrradiation / 1000)

Parameters and measures:

* EstimatedACPower: estimated ac power to grid
* EstimatedDCPower: estimated dc power from pv plant
* InverterEfficiency: Efficiency of inverter at power level
  * Taken from inverter type efficiency curve with DC power vs. efficiency steps
* InverterMiscLosses: misc losses factor as defined per plant in plant setup
* PlantMiscLosses: loss factor from inverter to grid as defined per plant in plant setup
* NominalDCPower: nominal DC power for plant as defined per plant in plant setup
  * for E/W using inverters with same orientation
* InclineIrradiation: Incline Irradiation measurements (SolarGIS data if not present)
  * for E/W using inverters with same orientation
* TemperatureLosses: Module temperature loss factor as calculated
* InverterDCLosses: loss factor on inverter DC side as defined in plant setup
* ModuleEfficiency: Efficiency of module at irradiation level
  * Taken from module type efficiency curve with irradiation vs. efficiency steps
* CellTemperature: estimated cell temperature based on measured module temperature and irradiation
* ModuleTemperatureMeasured: Module temperature measured
  * for E/W using inverters with same orientation
* ModuleTempCoeff: module temperature coefficient as defined in plant setup

## Incline Irradiation

Incline irradiation is calculated from incline irradiation pyranometer sensors as first source. Sensors are filtered according to rules in chapter 3.2.1.
If data is missing for a period, data is backfilled from external data source. See chapter 3.2.1.5.

### East/West oriented plants

Incline irradiation for east/west oriented plants are calculated as the weighted average of east and west oriented irradiation (Weighted by nominal power in east and west direction)

## Horizontal Irradiation

Horizontal irradiation is calculated from horizontal irradiation pyranometer sensors as first source. Sensors are filtered according to rules in chapter 3.2.1.
If data is missing for a period, data is backfilled from external data source. See chapter 3.2.1.5.

## Transposition Factor

Transposition Factor (TF) is relation between in cline and horizontal irradiation:
• TF = Incline Irradiation / Horizontal Irradiation

## Module Temperature

Different module temperature KPI’s are present in the system based on measurement and calculations:

1. Module temperature: average of measured module temperature sensors
2. Module temperature daylight: average of measured module temperature sensors during daylight, that is when irradiation is above 5 W/m2
3. Estimated cell temperature: average of estimated cell temperature calculated from measured module temperature and incline irradiation measurements
4. Estimated cell temperature daylight: average of estimated cell temperature during daylight
5. Estimated cell temperature daylight weighted : irradiation weighted average of estimated cell temperature during daylight

### Module temperature

Module temperature measured from each sensor is used as basis. It is filtered according to algorithm in 3.2.1 and stored per 10 minute period in data warehouse. When reported, all values for a day are used.
If all module temperature from sensors are missing, values from external satellite weather source is used. Module temperature is then calculated based on formula:
Module temperature = Ambient Temperature + (Incline Irradiation / 800) * 25

### Module temperature daylight

Average value calculated base on the “Module Temperature” values in 2.1.6.1. Only 10 minute values with incline irradiation above 5 W/m2 is used in average.

#### Estimated cell temperature

This is a calculated value based on measured module temperature and incline irradiation measurements:
Estimated cell temperature = Module Temperature + 3*( Incline Irradiation) / 1000
Value calculated per 10 minute interval and input to the algorithm is 10 minute values for plant filtered as in 3.2.1.

#### Estimated cell temperature daylight

Average value calculated base on the “Estimated cell temperature” values in 2.1.6.3. Only 10 minute values with incline irradiation above 5 W/m2 is used in average.

### Estimated cell temperature daylight weighted

Irradiation weighted average of estimated cell temperature during daylight. Input is the 10 minute values from 2.1.6.4. Average value for a period is weighted based on incline irradiation measurements.
Estimated cell temperature daylight weighted = (Estimated cell temperature daylight * Incline Irradiation) / sum(Incline Irradiation)

## Soiling Index

Soiling index for a plant is calculated as average soiling index calculated from soiling stations or reference cells.
If plant is configured to use soiling stations, these measurements are used and reference cells are ignored. (configured in plant parameters)

### Reference cell calculations

All working reference cells are used to calculate the plant average value.
Soiling index for a 10 minute period is calculated as relation between clean and dirty reference cells.
Reference cells are calibrated/normalized with the “cleaning date” as configured in the “Setup weather station” page (Last ref. cell cleaning date (dd.mm.yyyy). Normalization factor is calculated for that day, assuming both reference cells should be equal day after cleaning.
• Soiling Index = 100 * (RefCellIrradiation_Cleaned - RefCellIrradiation_Dirty / RefCellDirtyCleanScale) / RefCellIrradiation_Cleaned
o RefCellIrradiation_Cleaned: measured irradiation on clean reference cell
o RefCellIrradiation_Dirty: measured irradiation on clean reference cell
o RefCellDirtyCleanScale: normalization factor calculated based on cleaned date
o Filter: calculated when RefCellIrradiation_Cleaned > 200 W/m2

### Soiling Index calculations

Plant average soiling index is calculated from all working soiling index measurements. (no filtering on deviation from median etc.)

## Budget Production

Budgeted production for a plant. Internal budget is default used.

## Budget Irradiation

Budgeted incline irradiation for a plant. Internal budget is default used