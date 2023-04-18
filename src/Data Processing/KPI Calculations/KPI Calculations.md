# KPI Calculations

Table below summarises KPI's:

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Yield and Weather | Actual Production | Production for plant. Aggregated from energy meters and possibly manually corrected in correction page |
| Yield and Weather | Estimated Production | Estimated production based on weather data measurements |
| Yield and Weather | Incline Irradiation | Accumulated incline irradiation energy. Calculated from plant sensors, possibly backfilled from external weather source. Can also be manually corrected in correction page. |
| Yield and Weather | Horizontal Irradiation | Accumulated horizontal irradiation energy. Calculated from plant sensors, possibly  backfilled from external weather source. Can also be manually corrected in correction page. |
| Yield and Weather | Transposition Factor | Relation between incline and horizontal irradiation |
| Yield and Weather | Module Temperature | Different calculations based on module temperature measurements and incline irradiation.  |
| Yield and Weather | Soiling Index | Plant soiling index, from 0-100. Average value calculated from soiling stations or reference cells |
| Yield and Weather | Budget Production | Budget production for a plant.  |
| Yield and Weather | Budget Irradiation | Budget incline irradiation for a plant |
| Production Loss | Grid down time production losses | Production losses due to down time on grid (reduced grid availability) |
| Production Loss | Plant down time production losses | Production losses due to down time on inverters (reduced plant availability) |
| Production Loss | Tracker down time production losses | Production losses due to non-working trackers (reduced tracker availability) |
| Production Loss | String down time production losses | Production losses due to non-available strings (reduced string availability) |
| Production Loss | Curtailment production losses | Production losses due to plant curtailment |
| Production Loss | Clipping production losses | Production losses due to plant clipping |
| Production Loss | Soiling production losses | Production losses due to panel soiling |
| Production Loss | Snow production losses | Production losses due to snow on panels. |
| Revenue Losses | Grid down time revenue loss | Revenue losses due to down time on grid  (reduced grid availability). Energy tariff taken from internal original budget |
| Revenue Loss | Plant down time revenue loss | Revenue losses due to down time on inverters (reduced plant availability). Energy tariff taken from internal original budget |
| Revenue Loss | Tracker down time revenue loss | Revenue losses due to non-working trackers (reduced tracker availability). Energy tariff taken from internal original budget |
| Revenue Loss | String down time revenue losses | Revenue losses due to non-available strings (reduced string availability). Energy tariff taken from internal original budget |
| Revenue Loss | String down time revenue losses | Revenue losses due to plant curtailment. Energy tariff taken from internal original |budget
| Revenue Loss | Curtailment revenue losses | Revenue losses due to plant clipping. Energy tariff taken from internal original budget |
| Revenue Loss | Snow production losses | Revenue losses due to snow on panels. Price taken from internal original budget |
| Revenue Loss | Clipping revenue losses | Revenue losses due to panel soiling. Energy tariff taken from internal original budget |
| Availability | Plant availability daylight | Plant availability measured as Daylight time – Plant downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | Plant availability full day | Plant availability measured as Full day time – Plant downtime (in minutes) / Full day time (24 hours) |
| Availability | Plant availability production loss | Plant availability measured as Total production including losses – Inverter losses / (Total production including losses) |
| Availability | Grid availability daylight | Grid availability measured as Daylight time – Grid downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | Grid availability full day | Grid availability measured as Full day time – Grid downtime (in minutes) / Full day time (24 hours) |
| Availability | Grid availability production loss | Grid availability measured as Total production including losses – Grid losses / (Total production including losses) |
| Availability | Tracker availability daylight | Tracker availability measured as Daylight time – tracker downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | Tracker availability full day | Tracker availability measured as Full day time – tracker downtime (in minutes) / Full day time (24 hours) |
| Availability | Tracker availability production loss | Tracker availability measured as Total production including losses / (Total production including losses + Tracker losses) |
| Availability | String availability | Availability of strings calculated based on string production and detection of non producing strings. |
| Availability | String availability production loss | String availability measured as Total production including losses / (Total production including losses + String losses) |
| Performance | PR Contractual LD (warranty) | PR from contract for a given plant related to bonus calculations |
| Performance | PR Contractual Bonus | PR from contract for a given plant related to warranty issues |
| Performance | PR Net | PR basic calculation. Only looking at irradiance and production. Does not adjust for the module degradation in the nominal power. |
| Performance | PR Gross | Uses PR net as basis. Divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced  |
| Performance | PR Gross Production Loss | Uses PR net as basis, but production is using measured production + estimated production  |losses due to Plant and Grid downtime. |
| Performance | PR Net Temp Adjusted | Temperature adjusted PR calculation. Basis is “PR Net” |
| Performance | PR Gross Temp Adjusted | Temperature adjusted PR calculation. Basis is “PR Gross” |
| Performance | PR Gross Production Loss Temp Adjusted | Temperature adjusted PR calculation. Basis is “PR Gross Production Loss” |
| Performance | Energy Performance Index | Performance of production vs. irradiation, related to budget and actual |
| Performance  | Inverter PR | PR net per inverter calculated based on above formula and production per inverter |