# KPI Calculations

Table below summarises KPI's:

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Yield and Weather | [Actual Production](Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) | Production for plant. Aggregated from energy meters and possibly manually corrected in correction page |
| Yield and Weather | [Estimated Production](Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md) | Estimated production based on weather data measurements |
| Yield and Weather | [Incline Irradiation](Yield%20and%20Weather/Incline%20Irradiation/Incline%20Irradiation.md) | Accumulated incline irradiation energy. Calculated from plant sensors, possibly backfilled from external weather source. Can also be manually corrected in correction page. |
| Yield and Weather | [Horizontal Irradiation](Yield%20and%20Weather/Horizontal%20Irradiation/Horizontal%20Irradiation.md) | Accumulated horizontal irradiation energy. Calculated from plant sensors, possibly  backfilled from external weather source. Can also be manually corrected in correction page. |
| Yield and Weather | [Transposition Factor](Yield%20and%20Weather/Transposition%20Factor/Transposition%20Factor.md) | Relation between incline and horizontal irradiation |
| Yield and Weather | [Module Temperature](Yield%20and%20Weather/Module%20Temperature/Module%20Temperature.md) | Different calculations based on module temperature measurements and incline irradiation.  |
| Yield and Weather | [Soiling Index](Yield%20and%20Weather/Soiling%20Index/Soiling%20Index.md) | Plant soiling index, from 0-100. Average value calculated from soiling stations or reference cells |
| Yield and Weather | [Budget Production](Yield%20and%20Weather/Budget%20Production/Budget%20Production.md) | Budget production for a plant.  |
| Yield and Weather | [Budget Irradiation](Yield%20and%20Weather/Budget%20Irradiation/Budget%20Irradiation.md) | Budget incline irradiation for a plant |
| Production Loss | [Grid down time production losses](Production%20Losses/Grid%20down%20time%20production%20losses/Grid%20down%20time%20production%20losses.md) | Production losses due to down time on grid (reduced grid availability) |
| Production Loss | [Plant down time production losses](Production%20Losses/Plant%20down%20time%20production%20losses/Plant%20down%20time%20production%20losses.md) | Production losses due to down time on inverters (reduced plant availability) |
| Production Loss | [Tracker down time production losses](Production%20Losses/Tracker%20down%20time%20production%20losses/Tracker%20down%20time%20production%20losses.md) | Production losses due to non-working trackers (reduced tracker availability) |
| Production Loss | [String down time production losses](Production%20Losses/String%20down%20time%20production%20losses/String%20down%20time%20production%20losses.md) | Production losses due to non-available strings (reduced string availability) |
| Production Loss | [Curtailment production losses](Production%20Losses/Curtailment%20production%20losses/Curtailment%20production%20losses.md) | Production losses due to plant curtailment |
| Production Loss | [Clipping production losses](Production%20Losses/Clipping%20production%20losses/Clipping%20production%20losses.md) | Production losses due to plant clipping |
| Production Loss | [Soiling production losses](Production%20Losses/Soiling%20production%20losses/Soiling%20production%20losses.md) | Production losses due to panel soiling |
| Production Loss | [Snow production losses](Production%20Losses/Snow%20production%20losses/Snow%20production%20losses.md) | Production losses due to snow on panels. |
| Revenue Loss | [Grid down time revenue loss](Production%20Losses/Grid%20down%20time%20production%20losses/Grid%20down%20time%20production%20losses.md) | Revenue losses due to down time on grid  (reduced grid availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Plant down time revenue loss](Production%20Losses/Plant%20down%20time%20production%20losses/Plant%20down%20time%20production%20losses.md) | Revenue losses due to down time on inverters (reduced plant availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Tracker down time revenue loss](Production%20Losses/Tracker%20down%20time%20production%20losses/Tracker%20down%20time%20production%20losses.md) | Revenue losses due to non-working trackers (reduced tracker availability). Energy tariff taken from internal original budget |
| Revenue Loss | [String down time revenue losses](Production%20Losses/String%20down%20time%20production%20losses/String%20down%20time%20production%20losses.md) | Revenue losses due to non-available strings (reduced string availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Curtailment revenue losses](Production%20Losses/Curtailment%20production%20losses/Curtailment%20production%20losses.md) | Revenue losses due to plant clipping. Energy tariff taken from internal original budget |
| Revenue Loss | [Snow production losses](Production%20Losses/Snow%20production%20losses/Snow%20production%20losses.md) | Revenue losses due to snow on panels. Price taken from internal original budget |
| Revenue Loss | [Clipping revenue losses](Production%20Losses/Clipping%20production%20losses/Clipping%20production%20losses.md) | Revenue losses due to panel soiling. Energy tariff taken from internal original budget |
| Availability | [Plant availability daylight](Availability%20and%20downtime/Plant%20availability/Plant%20availability.md) | Plant availability measured as Daylight time – Plant downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Plant availability full day](Availability%20and%20downtime/Plant%20availability/Plant%20availability.md) | Plant availability measured as Full day time – Plant downtime (in minutes) / Full day time (24 hours) |
| Availability | [Plant availability production loss](Availability%20and%20downtime/Plant%20availability/Plant%20availability.md) | Plant availability measured as Total production including losses – Inverter losses / (Total production including losses) |
| Availability | [Grid availability daylight](Availability%20and%20downtime/Grid%20availability/Grid%20availability.md) | Grid availability measured as Daylight time – Grid downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Grid availability full day](Availability%20and%20downtime/Grid%20availability/Grid%20availability.md) | Grid availability measured as Full day time – Grid downtime (in minutes) / Full day time (24 hours) |
| Availability | [Grid availability production loss](Availability%20and%20downtime/Grid%20availability/Grid%20availability.md) | Grid availability measured as Total production including losses – Grid losses / (Total production including losses) |
| Availability | [Tracker availability daylight](Availability%20and%20downtime/Tracker%20availability/Tracker%20availability.md) | Tracker availability measured as Daylight time – tracker downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Tracker availability full day](Availability%20and%20downtime/Tracker%20availability/Tracker%20availability.md) | Tracker availability measured as Full day time – tracker downtime (in minutes) / Full day time (24 hours) |
| Availability | [Tracker availability production loss](Availability%20and%20downtime/Tracker%20availability/Tracker%20availability.md) | Tracker availability measured as Total production including losses / (Total production including losses + Tracker losses) |
| Availability | [String availability](Availability%20and%20downtime/String%20availability/String%20availability.md) | Availability of strings calculated based on string production and detection of non producing strings. |
| Availability | [String availability production loss](Availability%20and%20downtime/String%20availability/String%20availability.md) | String availability measured as Total production including losses / (Total production including losses + String losses) |
| Performance | [PR Contractual](Performance/PR%20Contractual/PR%20Contractual.md) | PR from contract for a given plant |
| Performance | [PR Net](Performance/PR%20Net/PR%20Net.md) | PR basic calculation. Only looking at irradiance and production. Does not adjust for the module degradation in the nominal power. |
| Performance | [PR Gross](Performance/PR%20Gross/PR%20Gross.md) | Uses PR net as basis. Divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced  |
| Performance | [PR Gross Production Loss](Performance/PR%20Gross%20Production%20Loss/PR%20Gross%20Production%20Loss.md) | Uses PR net as basis, but production is using measured production + estimated production  |losses due to Plant and Grid downtime. |
| Performance | [PR Net Temp Adjusted](Performance/PR%20Net%20Temp%20Adjusted/PR%20Net%20Temp%20Adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Net” |
| Performance | [PR Gross Temp Adjusted](Performance/PR%20Gross%20Temp%20Adjusted/PR%20Gross%20Temp%20Adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross” |
| Performance | [PR Gross Production Loss Temp Adjusted](Performance/PR%20Gross%20Production%20Loss%20Temp%20Adjusted/PR%20Gross%20Production%20Loss%20Temp%20Adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross Production Loss” |
| Performance | [Energy Performance Index](Performance/Energy%20Performance%20Index/Energy%20Performance%20Index.md) | Performance of production vs. irradiation, related to budget and actual |
| Equipment specific | [Inverter](Equipment%20Specific/Inverter/Inverter.md)| KPI's per inverter |
| Equipment specific | [String](Equipment%20Specific/String/String.md)| KPI's per string |
| Equipment specific | [Tracker](Equipment%20Specific/Tracker/Tracker.md)| KPI's per tracker |
