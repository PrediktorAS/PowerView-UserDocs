[//]: # (MBo: Fra KPI Calculations.pdf)

# KPI CALCULATIONS

This document describes the implementation of the data collection structures and calculations implemented in SCADA to calculate the different KPI’s.

|**KPI Type** |**KPI name** |**KPI description** |**Default** |
| - | - | - | - |
|Yield and Weather |[Actual Production](yieldweathercalc.md#actualproduction)  |Production for plant. Aggregated from energy meters and possibly manually corrected in correction page |X |
|Yield and Weather |[Estimated Production](yieldweathercalc.md#estimated-production)  |Estimated production based on weather data measurements |X |
|Yield and Weather |[Incline Irradiation](yieldweathercalc.md#incline-irradiation) |Accumulated incline irradiation energy. Calculated from plant sensors, possibly backfilled from external weather source. Can also be manually corrected in correction page. |X |
|Yield and Weather |[Horizontal Irradiation](yieldweathercalc.md#horizontal-irradiation) |Accumulated horizontal irradiation energy. Calculated from plant sensors, possibly backfilled from external weather source. Can also be manually corrected in correction page. |X |
|Yield and Weather |[Transposition Factor](yieldweathercalc.md#transposition-factor) |Relation between incline and horizontal irradiation |X |
|Yield and Weather |[Module Temperature](yieldweathercalc.md#moduletemp) |Different calculations based on module temperature measurements and incline irradiation.  |X |
|Yield and Weather |[Soiling Index](yieldweathercalc.md#soiling-index) |Plant soiling index, from 0-100. Average value calculated from soiling stations or reference cells |X |
|Yield and Weather |[Budget Production](yieldweathercalc.md#budget-production) |Budget production for a plant.  |X |
|Yield and Weather |[Budget Irradiation](yieldweathercalc.md#budget-irradiation) |Budget incline irradiation for a plant |X |
|Production Loss |[Grid down time production losses](productionlosscalc.md#grid-down-time-production-losses) |Production losses due to down time on grid (reduced grid availability) |X |
|Production Loss |[Plant down time production losses](productionlosscalc.md#plant-down-time-production-losses) |Production losses due to down time on inverters (reduced plant availability) |X |
|Production Loss |[Tracker down time production losses](productionlosscalc.md#tracker-down-time-production-losses) |Production losses due to non-working trackers (reduced tracker availability) |X |
|Production Loss |[String down time production losses](productionlosscalc.md#string-down-time-production-losses) |Production losses due to non-available strings (reduced string availability) |X |
|Production Loss |[Curtailment production losses](productionlosscalc.md#curtailment-production-losses) |Production losses due to plant curtailment |X |
|Production Loss |[Clipping production losses](productionlosscalc.md#clipping-production-losses) |Production losses due to plant clipping |X |
|Production Loss |[Soiling production losses](productionlosscalc.md#soiling-production-losses) |Production losses due to panel soiling Price taken from internal original budget |X |
|Revenue Loss |Grid down time revenue loss |Revenue losses due to down time on grid  (reduced grid availability)  Energy tariff taken from internal original budget |X |
|Revenue Loss |Plant down time revenue loss |Revenue losses due to down time on inverters (reduced plant availability)  Energy tariff taken from internal original budget |X |
|Revenue Loss |Tracker down time revenue loss |Revenue losses due to non-working trackers (reduced tracker availability)  Energy tariff taken from internal original budget |X |
|Revenue Loss |String down time revenue losses |Revenue losses due to non-available strings (reduced string availability)  Energy tariff taken from internal original budget |X |
|Revenue Loss |String down time revenue losses |Revenue losses due to plant curtailment Energy tariff taken from internal original budget |X |
|Revenue Loss |Curtailment revenue losses |Revenue losses due to plant clipping Energy tariff taken from internal original budget |X |
|Revenue Loss |Clipping revenue losses |Revenue losses due to panel soiling Energy tariff taken from internal original budget |X |
|Availability |[Plant availability daylight](availabilitycalc.md#plant-availability) |Plant availability measured as Daylight time – Plant downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) ||
|Availability |[Plant availability full day](availabilitycalc.md#plant-availability) |Plant availability measured as Full day time – Plant downtime (in minutes) / Full day time (24 hours) ||
|Availability |[Plant availability production loss](availabilitycalc.md#plant-availability) |Plant availability measured as Total production including losses – Inverter losses / (Total production including losses) |X |
|Availability |[Grid availability daylight](availabilitycalc.md#grid-availability) |Grid availability measured as Daylight time – Grid downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) ||
|Availability |[Grid availability full day](availabilitycalc.md#grid-availability) |Grid availability measured as Full day time – Grid downtime (in minutes) / Full day time (24 hours) ||
|Availability |[Grid availability production loss](availabilitycalc.md#grid-availability) |Grid availability measured as Total production including losses – Grid losses / (Total production including losses) |X |
|Availability |[Tracker availability daylight](availabilitycalc.md#tracker-availability) |Tracker availability measured as Daylight time – tracker downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |X |
|Availability |[Tracker availability full day](availabilitycalc.md#tracker-availability) |Tracker availability measured as Full day time – tracker downtime (in minutes) / Full day time (24 hours) ||
|Availability |[String availability](availabilitycalc.md#string-availability) |Availability of strings calculated based on string production and detection of non producing strings. |X |
|Performance |[PR Contractual](performancecalc.md#pr-contractual)  |PR from contract for a given plant. Can be adapted to customer requirements from PPA ||
|Performance |[PR Net](performancecalc.md#pr-net) |PR basic calculation. Only looking at irradiance and production. Does not adjust for the module degradation in the nominal power. ||
|Performance |[PR Gross](performancecalc.md#pr-gross) |Uses PR net as basis. Divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced.  ||
|Performance |[PR Gross Production Loss](performancecalc.md#pr-gross-production-loss) |Uses PR net as basis, but production is using measured production + estimated production losses due to Plant and Grid downtime. |X |
|Performance |[PR Net Temp Adjusted](performancecalc.md#pr-net-temp-adjusted) |Temperature adjusted PR calculation. Basis is “PR Net” ||
|Performance |[PR Gross Temp Adjusted](performancecalc.md#pr-gross-temp-adjusted) |Temperature adjusted PR calculation. Basis is “PR Gross” ||
|Performance |[PR Gross Production Loss Temp Adjusted](performancecalc.md#pr-gross-production-loss-temp-adjusted) |Temperature adjusted PR calculation. Basis is “PR Gross Production Loss” ||
|Performance |[Energy Performance Index](performancecalc.md#energy-performance-index) |Performance of production vs. irradiation, related to budget and actual ||
|Performance  |[Inverter PR](performancecalc.md#inverter-pr) |PR net per inverter calculated based on above formula and production per inverter. ||
