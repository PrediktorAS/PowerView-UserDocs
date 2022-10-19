# KPI CALCULATIONS

This document describes the implementation of the data collection structures and calculations implemented in SCADA to calculate the different KPI’s.

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
|Revenue Losses |Grid down time revenue loss |Revenue losses due to down time on grid  (reduced grid availability) |X |

|||Energy tariff taken from internal original budget ||
| :- | :- | - | :- |
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
