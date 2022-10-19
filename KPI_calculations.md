![](p105alqw.001.png)

**Product Description ![](p105alqw.002.png)**

**PowerView™  KPI Calculations**

*Confidentiality Notice: This document is confidential and contains proprietary information and intellectual property of Prediktor AS. Neither this document nor any of the information contained herein may be reproduced or disclosed under any circumstances without the express written permission of Prediktor AS. Please be aware that disclosure, copying, distribution or use of this document and the information contained therein is strictly prohibited.* 



||Version |Date |
| :- | - | - |
||2.0 |12/09/2021 |


|Control of Changes |
| - |
|Version |Date |Short Description |
|1.0 |12/01/2020 |First version |
|2.0 |12/09/2021 |Updated  |
||||
||||
CONTENTS ![](p105alqw.002.png)

1  [Introduction ........................................................................................................................................... 5](#_page4_x54.00_y84.04)
1  [KPI Calculations ..................................................................................................................................... 6](#_page5_x54.00_y108.04)
1. [Yield and Weather Calculations......................................................................................................... 9](#_page8_x54.00_y84.04)
1. [Actual Production ...................................................................................................................... 9](#_page8_x54.00_y98.04)
1. [Estimated Production ................................................................................................................ 9](#_page8_x54.00_y194.04)
1. [Incline Irradiation ......................................................................................................................10](#_page9_x54.00_y116.04)
1. [Horizontal Irradiation ................................................................................................................10](#_page9_x54.00_y262.04)
1. [Transposition Factor ................................................................................................................10](#_page9_x54.00_y346.04)
1. [Module Temperature.................................................................................................................10](#_page9_x54.00_y420.04)
1. [Soiling Index ............................................................................................................................. 11](#_page10_x54.00_y311.04)
1. [Budget Production .................................................................................................................... 11](#_page10_x54.00_y675.04)
1. [Budget Irradiation ..................................................................................................................... 11](#_page10_x54.00_y729.04)
2. [Production Loss Calculations .......................................................................................................... 13](#_page12_x54.00_y84.04)
1. [Grid down time production losses ............................................................................................. 13](#_page12_x54.00_y292.04)
1. [Plant down time production losses ........................................................................................... 14](#_page13_x54.00_y258.04)
1. [Tracker down time production losses ....................................................................................... 15](#_page14_x54.00_y473.04)
1. [String down time production losses .......................................................................................... 15](#_page14_x54.00_y652.04)
1. [Soiling production losses .......................................................................................................... 16](#_page15_x54.00_y136.04)
1. [Curtailment production losses .................................................................................................. 16](#_page15_x54.00_y248.04)
1. [Clipping production losses ........................................................................................................ 16](#_page15_x54.00_y640.04)
3. [Availability Calculations ................................................................................................................... 17](#_page16_x54.00_y302.04)
1. [Plant availability ........................................................................................................................ 17](#_page16_x54.00_y453.04)
1. [Grid availability ......................................................................................................................... 18](#_page17_x54.00_y270.04)
1. [Tracker availability ................................................................................................................... 19](#_page18_x54.00_y216.04)
1. [String availability ...................................................................................................................... 19](#_page18_x54.00_y606.04)
4. [Performance Calculations .............................................................................................................. 20](#_page19_x54.00_y434.04)
1. [PR Net ..................................................................................................................................... 20](#_page19_x54.00_y450.04)
1. [PR Gross .................................................................................................................................. 20](#_page19_x54.00_y632.04)
1. [PR Gross Production Loss ......................................................................................................... 21](#_page20_x54.00_y96.04)
1. [PR Net Temp Adjusted .............................................................................................................. 21](#_page20_x54.00_y388.04)
1. [PR Gross Temp Adjusted ........................................................................................................... 21](#_page20_x54.00_y636.04)
1. [PR Gross Production Loss Temp Adjusted ............................................................................... 22](#_page21_x54.00_y84.04)
1. [PR Contractual ......................................................................................................................... 22](#_page21_x54.00_y192.04)
1. [Energy Performance Index....................................................................................................... 22](#_page21_x54.00_y246.04)
1. [Inverter PR ............................................................................................................................... 22](#_page21_x54.00_y434.04)
3  [Data collection ..................................................................................................................................... 23](#_page22_x54.00_y84.04)
1. [Equipment state registration .......................................................................................................... 24](#_page23_x54.00_y84.04)
1. [Inverter state ........................................................................................................................... 24](#_page23_x54.00_y456.04)![](p105alqw.002.png)
1. [Grid state ................................................................................................................................. 25](#_page24_x54.00_y192.04)
1. [Tracker state ........................................................................................................................... 25](#_page24_x54.00_y322.04)
2. [Data filtering................................................................................................................................... 25](#_page24_x54.00_y629.04)
1. [Weather sensor filtering .......................................................................................................... 25](#_page24_x54.00_y663.04)
1. [Meter data filtering .................................................................................................................. 28](#_page27_x54.00_y136.04)
3. [Manual Data Correction .................................................................................................................. 28](#_page27_x54.00_y332.04)
1. [Central Web Portal ................................................................................................................... 28](#_page27_x54.00_y385.04)
1. [Plant web portals ..................................................................................................................... 29](#_page28_x54.00_y118.04)

1  INTRODUCTION ![](p105alqw.002.png)

This  document  describes  the  implementation  of  the  data  collection  structures  and  calculations implemented in SCADA to calculate the different KPI’s. 

2  KPI CALCULATIONS ![](p105alqw.002.png)

Table below summarize KPI’s calculated in the system. 



|**KPI Type** |**KPI name** |**KPI description** |**Default** |
| - | - | - | - |
|Yield and Weather |Actual Production  |Production for plant. Aggregated from energy meters and possibly manually corrected in correction page |X |
|Yield and Weather |Estimated Production  |Estimated production based on weather data measurements |X |
|Yield and Weather |Incline Irradiation |Accumulated incline irradiation energy. Calculated from plant sensors, possibly backfilled from external weather source. Can also be manually corrected in correction page. |X |
|Yield and Weather |Horizontal Irradiation |Accumulated horizontal irradiation energy. Calculated from plant sensors, possibly backfilled from external weather source. Can also be manually corrected in correction page. |X |
|Yield and Weather |Transposition Factor |Relation between incline and horizontal irradiation |X |
|Yield and Weather |Module Temperature |Different calculations based on module temperature measurements and incline irradiation.  |X |
|Yield and Weather |Soiling Index |Plant soiling index, from 0-100. Average value calculated from soiling stations or reference cells |X |
|Yield and Weather |Budget Production |Budget production for a plant.  |X |
|Yield and Weather |Budget Irradiation |Budget incline irradiation for a plant |X |
|Production Loss |Grid down time production losses |Production losses due to down time on grid (reduced grid availability) |X |
|Production Loss |Plant down time production losses |Production losses due to down time on inverters (reduced plant availability) |X |
|Production Loss |Tracker down time production losses |Production losses due to non-working trackers (reduced tracker availability) |X |
|Production Loss |String down time production losses |Production losses due to non-available strings (reduced string availability) |X |
|Production Loss |Curtailment production losses |Production losses due to plant curtailment |X |
|Production Loss |Clipping production losses |Production losses due to plant clipping |X |
|Production Loss |Soiling production losses |Production losses due to panel soiling Price taken from internal original budget |X |
|Revenue Losses |<p>Grid down time revenue loss |Revenue losses due to down time on grid  (reduced grid availability).</p><p> Energy tariff taken from internal original budget</p> |X |
|Revenue Loss |Plant down time revenue loss |<p>Revenue losses due to down time on inverters (reduced plant availability) </p><p>Energy tariff taken from internal original budget </p>|X |
|Revenue Loss |Tracker down time revenue loss |<p>Revenue losses due to non-working trackers (reduced tracker availability) </p><p>Energy tariff taken from internal original budget </p>|X |
|Revenue Loss |String down time revenue losses |<p>Revenue losses due to non-available strings (reduced string availability) </p><p>Energy tariff taken from internal original budget </p>|X |
|Revenue Loss |String down time revenue losses |<p>Revenue losses due to plant curtailment </p><p>Energy tariff taken from internal original budget </p>|X |
|Revenue Loss |Curtailment revenue losses |<p>Revenue losses due to plant clipping </p><p>Energy tariff taken from internal original budget </p>|X |
|Revenue Loss |Clipping revenue losses |<p>Revenue losses due to panel soiling </p><p>Energy tariff taken from internal original budget </p>|X |
|Availability |Plant availability daylight |Plant availability measured as Daylight time – Plant downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) ||
|Availability |Plant availability full day |Plant availability measured as Full day time – Plant downtime (in minutes) / Full day time (24 hours) ||
|Availability |Plant availability production loss |Plant availability measured as Total production including losses – Inverter losses / (Total production including losses) |X |
|Availability |Grid availability daylight |Grid availability measured as Daylight time – Grid downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) ||
|Availability |Grid availability full day |Grid availability measured as Full day time – Grid downtime (in minutes) / Full day time (24 hours) ||
|Availability |Grid availability production loss |Grid availability measured as Total production including losses – Grid losses / (Total production including losses) |X |
|Availability |Tracker availability daylight |Tracker availability measured as Daylight time – tracker downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |X |
|Availability |Tracker availability full day |Tracker availability measured as Full day time – tracker downtime (in minutes) / Full day time (24 hours) ||
|Availability |String availability |Availability of strings calculated based on string production and detection of non producing strings. |X |
|Performance |PR Contractual  |PR from contract for a given plant. Can be adapted to customer requirements from PPA ||
|Performance |PR Net |PR basic calculation. Only looking at irradiance and production. Does not adjust for the module degradation in the nominal power. ||
|Performance |PR Gross |Uses PR net as basis. Divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced.  ||

|Performance |PR Gross Production Loss |Uses PR net as basis, but production is using measured production + estimated production losses due to Plant and Grid downtime. |X |
| - | :- | :- | - |
|Performance |PR Net Temp Adjusted |Temperature adjusted PR calculation. Basis is “PR Net” ||
|Performance |PR Gross Temp Adjusted |Temperature adjusted PR calculation. Basis is “PR Gross” ||
|Performance |PR Gross Production Loss Temp Adjusted |Temperature adjusted PR calculation. Basis is “PR Gross Production Loss” ||
|Performance |Energy Performance Index |Performance of production vs. irradiation, related to budget and actual ||
|Performance  |Inverter PR |PR net per inverter calculated based on above formula and production per inverter. ||
1. Yield and Weather Calculations ![](p105alqw.002.png)
1. Actual Production 

Plant production is calculated from counters on energy meters. Energy counter is split in 10 minutes intervals, and production as difference in counter at start and end of interval is calculated and stored in data warehouse.  

Plant production can be corrected in manual correction page “Production adjustment”.

2. Estimated Production 

Estimated production used for loss calculations are calculated based on following algorithm:

- EstimatedProduction = time integration (EstimatedACPower) 
- EstimatedACPower = EstimatedDCPower \* InverterEfficiency \*  

(1- InverterMiscLosses) \* (1 – PlantMiscLosses) 

- EstimatedDCPower = NominalDCPower \* (InclineIrradiation / 1000) \* (1 - TemperatureLosses) \* (1 - InverterDCLosses) \* ModuleEfficiency 
- TemperatureLosses = (CellTemperature - 25) \* (ModuleTempCoeff / 100) 
- CellTemperature = ModuleTemperatureMeasured + 3 \* (InClineIrradiation / 1000) 

Parameters and measures:

- EstimatedACPower: estimated ac power to grid 
- EstimatedDCPower: estimated dc power from pv plant
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
- ModuleTempCoeff: module temperature coefficient as defined in plant setup![](p105alqw.002.png)
3. Incline Irradiation 

Incline irradiation is calculated from incline irradiation pyranometer sensors as first source. Sensors are filtered according to rules in chapter 3.2[.1. ](#_page24_x54.00_y663.04)

If data is missing for a period, data is backfilled from external data source. See chapter 3.2[.1.5. ](#_page26_x54.00_y282.04)

*2.1.3.1  East/West oriented plants* 

Incline irradiation for east/west oriented plants are calculated as the weighted average of east and west oriented irradiation (Weighted by nominal power in east and west direction)

4. Horizontal Irradiation 

Horizontal irradiation is calculated from horizontal irradiation pyranometer sensors as first source. Sensors are filtered according to rules in chapter 3.2[.1. ](#_page24_x54.00_y663.04)

If data is missing for a period, data is backfilled from external data source. See chapter 3.2[.1.5. ](#_page26_x54.00_y282.04)

5. Transposition Factor 

Transposition Factor (TF) is relation between in cline and horizontal irradiation: 

- *TF = Incline Irradiation / Horizontal Irradiation* 
6. Module Temperature 

Different module temperature KPI’s are present in the system based on measurement and calculations:

1. Module temperature: average of measured module temperature sensors 
1. Module temperature daylight: average of measured module temperature sensors during daylight, that is when irradiation is above 5 W/m2
1. Estimated cell temperature:  average of estimated cell temperature calculated from measured module temperature and incline irradiation measurements
1. Estimated cell temperature daylight: average of estimated cell temperature during daylight
1. Estimated cell temperature daylight weighted : irradiation weighted average of estimated cell temperature during daylight  
1. *Module temperature* 

Module temperature measured from each sensor is used as basis. It is filtered according to algorithm in[ 3.2.1 ](#_page24_x54.00_y663.04)and stored per 10 minute period in data warehouse. When reported, all values for a day are used.

If all module temperature from sensors are missing, values from external satellite weather source is used. Module temperature is then calculated based on formula:

*Module temperature = Ambient Temperature + (Incline Irradiation / 800) \* 25* 

2. *Module temperature daylight* 

Average value calculated base on the “Module Temperature” values in 2[.1.6.1. On](#_page9_x54.00_y616.04)ly 10 minute values with incline irradiation above 5 W/m2 is used in average.

3. *Estimated cell temperature ![](p105alqw.002.png)*

This  is  a  calculated  value  based  on  measured  module  temperature  and  incline  irradiation measurements: 

*Estimated cell temperature = Module Temperature + 3\* ( Incline Irradiation) / 1000* 

Value calculated per 10 minute interval and input to the algorithm is 10 minute values for plant filtered as in[ 3.2.1.](#_page24_x54.00_y663.04) 

4. *Estimated cell temperature daylight* 

Average value calculated base on the “Estimated cell temperature” values in 2[.1.6.3. Only](#_page10_x54.00_y84.04) 10 minute values with incline irradiation above 5 W/m2 is used in average. 

5. *Estimated cell temperature daylight weighted*  

Irradiation weighted average of estimated cell temperature during daylight. Input is the 10 minute values from [2.1.6.4. ](#_page10_x54.00_y174.04)Average value for a period is weighted based on incline irradiation measurements. 

*Estimated cell temperature daylight weighted = (Estimated cell temperature daylight \* Incline Irradiation) / sum(Incline Irradiation)* 

7. Soiling Index 

Soiling index for a plant is calculated as average soiling index calculated from soiling stations or reference cells. 

If plant is configured to use soiling stations, these measurements are used and reference cells are ignored. (configured in plant parameters)

1. *Reference cell calculations* 

All working reference cells are used to calculate the plant average value. 

Soiling index for a 10 minute period is calculated as relation between clean and dirty reference cells.

Reference cells are calibrated/normalized with the “cleaning date” as configured in the “Setup weather station” page (Last ref. cell cleaning date (dd.mm.yyyy). Normalization factor is calculated for that day, assuming both reference cells should be equal day after cleaning.

- Soiling Index = 100 \* (RefCellIrradiation\_Cleaned - RefCellIrradiation\_Dirty / RefCellDirtyCleanScale) / RefCellIrradiation\_Cleaned 
- RefCellIrradiation\_Cleaned: measured irradiation on clean reference cell
- RefCellIrradiation\_Dirty: measured irradiation on clean reference cell 
- RefCellDirtyCleanScale: normalization factor calculated based on cleaned date
- Filter: calculated when RefCellIrradiation\_Cleaned > 200 W/m2 
2. *Soiling Index calculations* 

Plant average soiling index is calculated from all working soiling index measurements. (no filtering on deviation from median etc.) 

8. Budget Production 

Budgeted production for a plant. Internal budget is default used.

9. Budget Irradiation 

Budgeted incline irradiation for a plant. Internal budget is default used.![](p105alqw.002.png)

2. Production Loss Calculations ![](p105alqw.002.png)

Production loss based on grid and inverter is calculated based on data from plants and stored in separate tables in the data warehouse for easy reporting. Data is updated when inverter state or other parameters are changed manually.

General rule: 

- When grid downtime losses are calculated, other losses are set to the percentage of the 10 minute period having grid down. If whole period has grid down, no other losses are calculated.
- Else when curtailment losses are calculated, other losses than clipping losses are set to the percentage of the 10 minute period having curtailment. If whole period has curtailment, no other losses are calculated.
- Else when clipping losses are calculated, other losses are set to the percentage of the 10 minute period having clipping. If whole period has clipping, no other losses are calculated.
1. Grid down time production losses 

Grid downtime is classified into following classes:

- Production time 
- Failure time 
- Idle time 
- Line restraint time 
- Unscheduled 

“Failure time”, “Idle time” and “Line restraint time” is counted as down time resulting in reduced plant availability and thus production loss due to down time.

Following algorithm is implemented in SCADA to estimate production loss:

- Production Loss Grid = EstimatedProduction \* AdjustmentFactor

Factors calculated as follows:

- EstimatedProduction:  
- Estimated production based on standard plant model (see chapter 2.1.2[) and fol](#_page8_x54.00_y194.04)lowing input: 
- Nominal power of plant (for E/W for inverters with same orientation)
- Incline Irradiation measurements (SolarGIS data if not present)
  - (for E/W for inverters with same orientation) 
- Estimated cell temperature together with module temperature coefficient (for E/W for inverters with same orientation)
- Module efficiency 
- Inverter efficiency 
- Loss factors (DC, inverter, plant) ![](p105alqw.002.png)
- AdjustmentFactor 
- Adjustment factor is calculated based on estimated production and measured production 1 hour before grid downtime starts 
- Adjustment factor is limited to the interval 0,7 - 1,3 
- For E/W for inverters with same orientation

For E/W installations, losses for east and west are calculated separately with incline irradiation and module temperature for each orientation and add together

2. Plant down time production losses This is plant downtime in kWh. 

Production loss is calculated for an inverter based on the state for the inverter at a given time (see chapter [ 3.1.1)](#_page23_x54.00_y456.04) 

Inverter downtime is classified into following classes: 

- Production time 
- Failure time 
- Idle time 
- Line restraint time 
- Not scheduled 

“Failure time” and “Idle time” is counted as down time resulting in reduced plant availability and thus production loss due to down time.

For each 10 min time period SCADA calculates the share of the total inverter DC capacity which is experiencing downtime (ShareNomPowerDown). As long as this share is below [80%], Alternative A should be used, while if the share of inverter capacity down is above [80%] – Alternative B should be applied (the same as applied in case of Production Loss on Grid).

- ShareNomPowerDown = TotalNomPowerDown / Pnom 

Factors calculated as follows:

- Pnom: total nominal DC power of plant 
- TotalNomPowerDown: total nominal DC power of all inverters experiencing down time 

Production loss for one inverter is calculated dividing “Production Loss Inverters” with number of inverters down. 

**Alternative A:** 

Following algorithm is implemented in SCADA to estimate production loss on an inverter (as long as the total inverter capacity down is below [80%]): 

- Production Loss Inverter = E\_meas \* NomPowerInverter / (Pnom – NomPowerInverter) 

Factors calculated as follows:

- E\_meas: measured energy production (see 2[.1.1) of ](#_page8_x54.00_y98.04)the plant during the period 
- For E/W oriented plants, energy is taken from inverters with same orientation
- NomPowerInverter: nominal DC power of the single inverter experiencing down time![](p105alqw.002.png)
- Pnom: total nominal DC power of all inverters 
- For E/W oriented plants, nominal power is summarized from inverters with same orientation 

**Alternative B:** 

Following algorithm is implemented in SCADA to estimate production loss on inverter (when the total inverter capacity down is above [80%]): 

- Production Loss Inverter = PR\_reference \* NomPowerInverter \* InclineIrradiation \* / Irr\_STC  

Factors calculated as follows:

- PR\_reference:  
- Calculate a reference “PR Gross Production Loss” (see 2[.4.3) for](#_page20_x54.00_y96.04) the reference period of 5 (full) days prior to the day in which the downtime occurs (including the effects of any production loss during that reference period) 
- NomPowerInverter:  
  - Nominal DC power of inverter 
- InclineIrradiation 
  - Incline pyranometer value for plant (see 2[.1.3) ](#_page9_x54.00_y116.04)
  - If no irradiation exists for 10 minute period: 
    - Use irradiation for same time previous day is used. 20 days back is checked. 
  - For E/W oriented plants, use irradiation from inverter orientation.
- Irr\_STC 
  - Irradiance at standard test conditions
  - Standard 1000 W/m2 
3. Tracker down time production losses

Following algorithm is implemented in SCADA to estimate production loss on trackers:

- Production Loss Trackers = E\_meas \*(1 – TA\_ForProdLoss) \* (TF - 1) 

Factors calculated as follows:

- E\_meas: measured actual production for plant (see 2[.1.1) ](#_page8_x54.00_y98.04)
- TAprodloss: Tracker availability (0-1) for plant (see [2.3.3) ta](#_page18_x54.00_y216.04)king into account available power on tracker for the time period. Removing power due to unavailable strings and inverters
- TF: Transposition Factor = Incline Irradiation / Horizontal Irradiation (see 2[.1.5) ](#_page9_x54.00_y346.04)
4. String down time production losses

String availability losses are calculated based on string availability for plant as described in chapter [2.3.4. ](#_page18_x54.00_y606.04)

- Production Loss Strings = E\_meas \* (1-SA) / SA 

Factors calculated as follows:

- E\_meas: measured actual production for plant (see 2[.1.1) ](#_page8_x54.00_y98.04)![](p105alqw.002.png)
- SA: String availability (0-1) for plant 
5. Soiling production losses 

Soiling losses are calculated as soiling index related to measured energy production:

Soiling losses = (E\_meas / (1-(SoilingIndex/100))) - E\_meas 

- E\_meas: measured plant energy production for period. (see 2.1.1[) ](#_page8_x54.00_y98.04)
- SoilingIndex: average soiling index for plant (see 1)[ ](#_page9_x54.00_y456.04)
6. Curtailment production losses

Curtailment losses are calculated for each 10 minute period based on registered curtailment periods. Curtailment is registered as state 6006 on grid as explained in chapter 3.1.2[. ](#_page24_x54.00_y192.04)

For each period, estimated production is calculated based on measured irradiation and available nominal power. The difference between estimated and measured value is defined as the losses.

Curtailment losses = (E\_est \* AdjustmentFactor) - E\_meas  

- E\_meas:  
  - measured plant energy production for period of curtailment (see 2.1.1[) ](#_page8_x54.00_y98.04)
- E\_est:  
- Estimated production based on standard plant model (see 2.1.2[) ](#_page8_x54.00_y194.04)
- Cut on max nominal AC power on plant. Estimated production above nominal power is classified as clipping losses 
- AdjustmentFactor 
- Adjustment factor is calculated based on estimated production and measured production last 30 minutes before curtailment starts 
- AdjustmentFactor = E\_meas / E\_est 
- E\_meas and E\_est as above 

If measured power is not close to the curtailment limit, the losses are set to 0. Detection limit is 98%, meaning measured power on PPC (or PPC power analyser) must be more than 98% of PPC active power setpoint value to calculate losses.

7. Clipping production losses 

Clipping is detected based on detection of output power close to maximum nominal output power. Detecting is done based on measured power on PPC vs. nominal dc power on plant and a per plant adjustment limit. If measured value is above nominal and no curtailment is active, clipping is detected.  

Losses are calculated for each 10 minute period the same way as for curtailment:

Clipping losses = (E\_est \* AdjustmentFactor) - E\_meas  

- E\_meas:  
  - measured plant energy production for period of curtailment (see 2.1.1[) ](#_page8_x54.00_y98.04)![](p105alqw.002.png)
- E\_est:  
  - Estimated production based on standard plant model (see 2.1.2[) ](#_page8_x54.00_y194.04)
- AdjustmentFactor 
  - Adjustment factor is calculated based on estimated production and measured production last 30 minutes before clipping starts 
- AdjustmentFactor = E\_meas / E\_est 
- E\_meas and E\_est as above 

Clipping losses are also  detected for period  of  curtailment, when estimated production is above nominal output on plant. The energy estimated above nominal max output is classified as clipping losses. 

3. Availability Calculations 

This chapter describes how the availability is calculated in the SCADA application. The following availabilities are calculated: 

- Plant availability 
- Grid availability 
- Tracker availability 
- String availability 
1. Plant availability 

Plant availability is calculated in three ways: 

1. *Plant availability daylight = Sum daylight time - Sum downtime inverters at daylight / Sum daylight time* 
1. *Plant availability full day = Sum time full day - Sum downtime inverters full day / Sum time full day* 
1. *Plant availability production loss = (E\_meas\_gross - Production Loss Inverters) / E\_meas\_gross* 

Definition of factors: 

- Sum daylight time: 
  - Calculated based on all states not having class “Not scheduled”, e.g. “No power production” 
  - See chapter [3.1.1. ](#_page23_x54.00_y456.04)
- Sum downtime inverters at daylight 
- Total down time inverters, weighted based on inverter nominal DC power.   
- Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time” 
- Sum time full day 
  - Total time for period ![](p105alqw.002.png)
- Sum downtime inverters full day  
  - Total down time 24/7, weighted based on inverter nominal DC power.  
  - Down time is calculated as sum of periods when inverter state is in state classes “Idle time” or “Failure time” or when state code>10000 (e.g. Stop, no power production)
- E\_meas\_gross = E\_meas + Production Loss Grid +Production Loss Inverters
- E\_meas: measured actual production for plant (see 2[.1.1) ](#_page8_x54.00_y98.04)
- Production Loss Grid: see 2[.2.1 ](#_page12_x54.00_y292.04)
- Production Loss Inverters: see 2[.2.2 ](#_page13_x54.00_y258.04)
2. Grid availability 

Grid availability is calculated in three ways: 

1. *Grid availability daylight (GAd) = (Sum daylight time - Sum downtime  grid at daylight) / Sum daylight time* 
1. *Grid availability full day (GAt) = (Sum time full day - Sum downtime  grid full day) / Sum time full day* 
1. *Grid availability production loss = (E\_meas\_gross – Production Loss Grid) / E\_meas\_gross* 

Definition of factors: 

- Sum daylight time: 
- Calculated based on all states not having class “Not scheduled” (E.g. “No power production”. See chapter [3.1.2.) ](#_page24_x54.00_y192.04)
- Sum downtime grid at daylight 
- Total down time  
- Down time is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint” 
- Sum time full day 
  - Total time for period 
- Sum downtime grid full day  
- Total down time 24/7  
- Down time full day is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint” or when state code>10000 (e.g. No power production, grid down) 
- E\_meas\_gross = E\_meas + Production Loss Grid + Production Loss Inverters 
- E\_meas: measured actual production for plant, see 2[.1.1 ](#_page8_x54.00_y98.04)
- Production Loss Grid: see 2[.2.1 ](#_page12_x54.00_y292.04)
- Production Loss Inverters: see 2[.2.2 ](#_page13_x54.00_y258.04)

For PR Gross calculation, a special formula is used: ![](p105alqw.002.png)

*“Grid availability daylight gross” (GAdg)* 

When grid is down, it might be that there is no irradiation measurement present. This will result in grid down time is already counted for in PR by having a reduced accumulated irradiation value for day and thus a higher PR. For the PR Gross, down time and daylight time is therefore only counted when there exist incline irradiation data and when this is above 5 W/m2 (this is taken from 10 minute average values in data warehouse). 

3. Tracker availability Following calculation applies: 
1. *Tracker availability daylight (TAd) = (Sum daylight time trackers  - Sum downtime trackers) / Sum daylight time trackers* 
1. *Tracker availability full day (TAt) = (Sum time full day - Sum downtime trackers) / Sum time full day* 
1. *Tracker availability for production loss calculation (TAprodloss) = (Sum time full day – (Sum downtime trackers \* Power availability on tracker)) / Sum time full day* 

Definition of factors: 

- Sum downtime trackers 
- Total down time. Down time is calculated as sum of periods when tracker state is in state classes “Idle time” or “Failure time”. Will only happen during day time. 
- Sum daylight time trackers: 
  - Calculated based on all states not having class “Not scheduled” 
  - E.g. “No power production”. See chapter 3[.1.3. ](#_page24_x54.00_y322.04)
- Sum time full day 
  - Total time for period. 
- Power availability on tracker 
- Factor from 0-1. Removing unavailable power due to string and inverter downtime
4. String availability 

String availability is calculated based on specific power on each string relative to plant median of specific power.  

When string has between 20% and 60% relative power, 50% availability is set for string. When relative power is below 20%, 0% availability is set on string.

String availability is calculated for the following aggregated periods (not 10 minute periods):

- Morning: 06:00 to 10:00 
- Midday: 10:00 to 14:00 
- Afternoon: 14:00 to 18:00 ![](p105alqw.002.png)

Exception rules are made to not get string downtime when inverter is not producing or tracker is malfunction: 

1. Inverter down: 
- When all strings connected to the inverter is down for the period, string availability is set to 100% for all strings on inverter. 
2. Tracker down; 
- Tracker availability is calculated for the tracker connected to a string:
- TrackerDowntimeFactor (0-1) per string: 
- Calculated as average value for morning, midday and afternoon for each string 
- Limit to detect string availability for a string is adjusted according to following formula: 
- 20% \* (1 - 0.5 \* TrackerDowntimeFactor) 
- 60% \* (1 - 0.5 \* TrackerDowntimeFactor) 

String availability for plant is calculated as the weighted average (weighted by nominal power Wp) of availability for all strings.  

4. Performance Calculations 
1. PR Net  

This is the PR basic calculation only considering production and irradiation. 

This formula is only taking into account irradiance and production measurements. It does not take into account the module degradation in the nominal power.

*PR net = E\_Meas \* Is / Pnom / Iacc* 

- *E\_Meas: Measured energy production, manually adjusted if necessary (see 2.[1.1)* ](#_page8_x54.00_y98.04)*
- *Is: Irradiation at standard test conditions, constant 1000 W/m2* 
- *Pnom: nominal DC power of plant. Sum of installed modules.* 
- *Iacc: accumulated incline irradiation in kWh/m2. (See [2.1.3)* ](#_page9_x54.00_y116.04)*
2. PR Gross 

This formula uses PR net as basis.  It divides by availability to get a PR only for time when park has produced.  

PR Gross = PR Net / PAd / GAdg 

- PR Net: performance ratio net (see 2[.4.1) ](#_page19_x54.00_y450.04)
- PAd: Plant availability daylight (see chapter 2[.3.1) ](#_page16_x54.00_y453.04)
- GAdg: Grid availability daylight gross (see chapter 2[.3.2) ](#_page17_x54.00_y270.04)
3. PR Gross Production Loss ![](p105alqw.002.png)

Uses  PR  net  as  basis,  but  production  is  using  measured  production  +  production  losses  due  to downtime. 

*PR Gross Prod Loss = E\_Meas\_Loss \* Is / Pnom / Iacc* 

- *E\_Meas\_Loss: Measured energy production, manually adjusted if necessary + production loss due to inverters and grid downtime* 
- *E\_Meas\_Loss = E\_Meas + Production Loss Inverters + Production Loss Grid* 
- *E\_Meas: measured production, see [2.1.1*  ](#_page8_x54.00_y98.04)*
- *Production Loss Inverters: see [2.2.2* ](#_page13_x54.00_y258.04)*
- *Production Loss Grid: see [2.2.1* ](#_page12_x54.00_y292.04)*
- *Is: Irradiance at standard test conditions, constant 1000 W/m2* 
- *Pnom: nominal DC power of plant* 
- *Iacc: accumulated irradiation in the module plan, see [2.1.3*   ](#_page9_x54.00_y116.04)*
- *If data missing, irradiation for same time previous day is used. 30 days back is checked and 5 first day with irradiation is used* 
4. PR Net Temp Adjusted 

Temp adjusted PR is calculated as shown below: *PR Net Temp Adjusted = PR Net / (1 - Ptpv)*  

- *PR Net: see[ 2.4.1* ](#_page19_x54.00_y450.04)*
- *Ptpv: Thermal losses factor of Module* 
- *Ptpv = (Tmda - Tmdb) \* ɣ / 100* 
- *Tmda: Module temperature daylight measured. Average measured module temperature weighted with incline irradiation measured (10 minute intervals) when irradiation is above 5 W/m2* 
- *Tmdb: Module temperature daylight budget number. Average number for period. Budget value, originally from PVsyst* 
- *ɣ:  Power temperature coefficient of the Module, as supplied by the Module producer (%/°C)* 
5. PR Gross Temp Adjusted 

Temp adjusted PR is calculated as shown below: *PR Gross Temp Adjusted = PR Gross / (1 - Ptpv)*  

- *PR Gross: see[ 2.4.2* ](#_page19_x54.00_y632.04)*
- *Ptpv: See definition in [2.4.4, PR Net Temp Adjusted* ](#_page20_x54.00_y388.04)*
6. PR Gross Production Loss Temp Adjusted ![](p105alqw.002.png)

Temp adjusted PR is calculated as shown below:

*PR Gross Production Loss Temp Adjusted = PR Gross Production Loss / (1-Ptpv)*  

- *PR Gross Production Loss: see [2.4.3* ](#_page20_x54.00_y96.04)*
- *Ptpv: See definition in [2.4.4, PR Net Temp Adjusted* ](#_page20_x54.00_y388.04)*
7. PR Contractual 

Adjusted per customer / PPA. 

8. Energy Performance Index 

Energy Performance Index (EPI) is calculated as the relation between the production actual vs. budget and the irradiation actual vs budget.

The actual formula is: 

*EPI = 100 \* (100 + (Actual Production - Budget Production ) / Budget Production )) / (100 + (Actual Irradiation- Budget Irradiation) / Budget Irradiation)* 

- *Actual Production: see [2.1.1* ](#_page8_x54.00_y98.04)*
- *Budget Production: see [2.1.8* ](#_page10_x54.00_y675.04)*
- *Actual Irradiation: see [2.1.3* ](#_page9_x54.00_y116.04)*
- *Budget Irradiation: see [2.1.9* ](#_page10_x54.00_y729.04)*
9. Inverter PR 

This is the PR basic calculation only considering production and irradiation. *Inverter PR = E\_Meas\_Inverter \* Is / Pnom\_Inverter / Iacc* 

- *E\_Meas: Measured energy productionon inverter taken from inveter energy meter on AC side* 
- *Is: Irradiation at standard test conditions, constant 1000 W/m2* 
- *Pnom: nominal DC power of inverter. Sum of installed modules on inverter.* 
- *Iacc: accumulated incline irradiation in kWh/m2 for plant. (See 2[.1.3)* ](#_page9_x54.00_y116.04)*

3  DATA COLLECTION ![](p105alqw.002.png)

Data is collected from plant equipment and stored in raw time series databases for further processing. This includes data from all types og devices. Data is stored in a buffer database on site and replicated with a secure store and forward functionality to the portfolio solution. Alarms and events are calculated and stored in event database.

The power view information model contains meta data for the plant, like nominal powers, device position and relation between equipment on site. 

Satellite weather data and forecasting data is collected from service providers.

Stored production data, plant meta data and data from forecast and weather providers are used to calculate all the KPI’s described in this document in the PowerView Analytics Engine. 

![](p105alqw.003.jpeg)

*Figure 1: General PowerView™ dataflow and functional details* 

1. Equipment state registration![](p105alqw.002.png)

In SCADA, currently three equipment types have state logging:

- Inverters 
- Grid connection 
- Tracker 

The  state  of  each  of  the  equipment  within  these  equipment  types  are  continuously  logged  in  a database. When the state is changed, the time of the change is logged together with the new state type.  

State is automatically logged based on signals from the plant equipment and instrumentation. E.g. for the inverters, the operation mode and error signals are used to decide what state is set.

State can be manually changed in the database using web input screens in plant web portal (PS: not available in central web portal).  

The state codes are classified into state classes:

- Production time 
- Failure time (defined as downtime) 
- Idle time (defined as downtime) 
- Line restraint time 
- Not scheduled 

Inverter state and grid state should not have down time at same time, so when grid is down, down time is not registered on inverter. This must also be considered when changing states manually, possibly both changing inverter and grid state.

1. Inverter state 

State of inverters are calculated automatically based on following input signals: 

- Operation mode reported by inverter
- Alarms reported by inverter 
- Measures irradiation from plant pyranometer sensors
- Grid state 

The following main principle will apply for calculation of the downtimes:

- During night (irradiation below 5 W/m2) no downtime is registered. (states not idle time or failure time) 
- “Grid down” result in line restraint time. 
- All stops on inverter not due to grid down, is “Idle” or “Failure” time resulting in downtime and reduced availability  
- All manual codes are grouped as “Idle” time (resulting in downtime), but classified to make it possible to extract and group in special reports if needed 
- When moving downtime from plant to grid, “Grid down” state on inverter shall be used (“line restraint” not resulting in plant downtime). At same time, “No operation” must ![](p105alqw.002.png)be set on grid for same period to make sure grid availability is used. 
- During night, time must be set to one of the “Not scheduled” states if manually corrected. If not, daytime availability will be wrong. Total time to calculate availability is based on states not being “Not scheduled” 
2. Grid state 

State of grid is collected automatically based on following input:

- State of main breakers connecting substation to grid
- Active power measurement from power analysers 
- Active power setpoint on PPC (curtailment state)
- Voltage and frequency measurements from power analyser
3. Tracker state 

State of trackers is collected automatically based on following input:

- State/mode signals from tracker control unit 
- Alarm signals from tracker control unit 
- Measures irradiation from plant pyranometer sensors
- Average value from incline pyranometers

States and state calculation will vary between tracker suppliers. General rules:

- Tracker is operating when following the sun 
- When tracker is in a manual mode and/or in a fixed position, it is defined as idle
- When tracker reports an error, it is in failure mode.
- Night-time is defined as Not Scheduled 
- Grid down is defined as Line Restraint.  
- Optional states to calculate tracker out of position. Used on some plants.
- Warning as production (small deviation), error as alarm (large deviation)
2. Data filtering 

Data is filtered in reports based on raw measurement data from plant logging.

1. Weather sensor filtering 

All weather data read with bad quality from sensor (e.g. due to comm problems) will be rejected. In addition, below filtering applies. 

1. *Filtering with out-of-order status* 

Sensors can be configured as out of order in user interface. These values are set to bad and not used in plant data calculations. 

2. *Statistics filtering ![](p105alqw.002.png)*

Remove points when the absolute value of the median is within interval X and point is more than Y% away from median. The median value calculated is the “continuous” median, that is not necessary one of the sample values if it is an even number of sensors. 

Remove points outside interval Z 

- Ambient Temperature (°C) 
  - X={2;~} °C , Y=50% 
  - Z={-100 ; 100} 
- Module Temperature  (°C) 
  - X={2;~} °C , Y=50% 
  - Z={-100 ; 100} 
- Wind Speed (m/s) 
  - X={1;~}  m/s, Y=50% 
  - Z={0 ; 100} 
- Horizontal Irradiation Pyranometer (W/m2) 
  - Remove points < 5 W/m2 when power is above 5% of nominal power 
  - Remove points > 10 W/m2 when median is below 5 W/m2
  - X={5;~}  W/m2, Y=50% 
  - Z={0 ; 1500} 
- InCline Irradiation Pyranometer (W/m2) 
  - Remove points < 5 W/m2 when power is above 5% of nominal power 
  - Remove points > 10 W/m2 when median is below 5 W/m2
  - X={5;~}  W/m2, Y=50% 
  - Z={0 ; 1500} 
- Reference cells  (W/m2) 
  - Z={0 ; 1500} 
- Soiling index (%) 
  - Z={0 ; 20} 
- WindDirection (°) 
  - Z={0 ; 360} 
- Humidity (%) 
  - Z={0 ; 200} 
- Rain intensity (mm/h) 
- Z={0 ; 500} ![](p105alqw.002.png)
3. *Incline irradiaiton tracker filtering* 

Incline irradiation values from pyranometer are removed based on status of connected tracker. If state is Idle or Failure (see chapter 3[.1.3) on](#_page24_x54.00_y322.04) tracker pyranometer values is marked with bad quality and not included in plant average value.  

Connected tracker is configured in screen as shown below. Tracker filtering can be disabled using checkbox in screen. This can be done if status signal of tracker is not reliable.

4. *Weather data filtering reporting*  

Data quality is stored in data warehouse and can be reported using “weather data details” report as shown below. 

5. *Backfilling irradiation data with data interpolation* 

If  irradiation  data  is  missing  for  shorter  periods  for  a  site,  the  data  missing  is  backfilled  with interpolated data. This goes for both incline and horizontal irradiation.

This can be the result of e.g. all values being removed from the median filtering. 

Periods of 90 minutes or less with missing data is backfilled.

Algorithm uses is a linear interpolation of the irradiation values from start to end of the interval.

6. *Backfilling data from external weather source* 

If weather sensor data is  missing, it is backfilled from external weather data. This is true for the following parameters: 

- Incline Irradiation 
  - If horizontal irradiation data exists, TF is calculated from the external data and incline irradiation calculated based on measured horizontal irradiation and TF from external data: incline irradiation = horizontal irradiation \* TF 
  - If both incline and horizontal irradiation is missing, value is filled directly
- Horizontal Irradiation 
  - If incline irradiation data exists, TF is calculated from the external data and horizontal irradiation calculated based on measured incline irradiation and TF from external data: horizontal irradiation = incline irradiation / TF 
  - If both incline and horizontal irradiation is missing, value is filled directly
- Wind Speed 
- Wind Direction 
- Ambient Temperature 
- Module Temperature 
- Calculated from ambient temperature and horizontal irradiation using formula: 
- Module temperature = Ambient Temperature + (Incline Irradiation / 800) \* 25 
- Air Pressure 
- Humidity ![](p105alqw.002.png)
- Rain Amount 
2. Meter data filtering 

Obviously wrong active energy meter readings  are filtered out and not added to data warehouse database using following algorithm:

- Calculate max possible production from last 10-minute period production was more than 0
  - Use nominal AC power for plant and time since last energy registration on meter
- Add 50 % as safety margin 
- If above this limit, reject value. 

*3.2.2.1  Meter data filtering reporting*  

Weekly mail is sent to stakeholder, summarizing rejected meter values.

3. Manual Data Correction 

Data is corrected manually in web pages in plant portal and central portal. This chapter describes the functionality.

1. Central Web Portal 
1. *Production correction* 

Production number is read from energy meters and summarized and stored as plant data per 10 minute. This plant data can be manually corrected. Meter data as input to the plant data is not corrected in this process. 

User enter 10 minute data to be changed. Values can be positive or negative. Reason for change is added as text. Production values are updated and used in KPI calculations. 

See also [ 2.1.1.](#_page8_x54.00_y98.04) 

2. *Production adjustment factor* 

The production adjustment factor is used to calculate the Kd factor in contractual PR. The screen enters a adjustment factor from 0-1 per plant and day, and factor is used to calculate other losses for the Kd factor (see [2.4.7) ](#_page21_x54.00_y192.04)

3. *Irradiation adjustment* 

Irradiation number are read from pyranometers and summarized and stored as plant data per 10 minute (see [2.1.3 a](#_page9_x54.00_y116.04)nd [2.1.4).](#_page9_x54.00_y262.04) Plant values can be updated using a web screen in portal. Only irradiation energy 

data used for PR calculation is updated.  

4. *Budget updates* 

Budgets are updated in budget screen.

5. *Edit plant comments* 

Plant comment screen is used to update daily textual comments used in reporting

6. *Update Facility Weather Data* 

This function is used to update weather data for a facility. User can update the data on a facility in 3 ways: 

- Update from sensors values. E.g. when one or more sensors are set out of order.
- Update from historical SolarGIS data ![](p105alqw.002.png)
- Update from forecast SolarGIS data 
2. Plant web portals 

*3.3.2.1  Equipment Down Times* 

Registered states for each equipment is corrected in the plant web portal. See also [3.1. ](#_page23_x54.00_y84.04)
© 2021 Prediktor AS        pg. 29 
