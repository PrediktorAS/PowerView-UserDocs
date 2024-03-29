# KPI Calculations

Table below summarises KPI's:

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Yield and Weather | [Actual Production](./yield_and_weather/production.md) | Production for plant. Aggregated from energy meters and possibly manually corrected in correction page |
| Yield and Weather | [Actual Production No Grid Outage or Curtailment](./yield_and_weather/production.md) | Production for plant summarized only for periods having no curtailment or grid outage. |
| Yield and Weather | [Estimated Production](./yield_and_weather/production.md) | Estimated production based on weather data measurements |
| Yield and Weather | [Incline Irradiation](./yield_and_weather/irradiation.md) | Accumulated incline irradiation energy. Calculated from plant sensors, possibly backfilled from external weather source. Can also be manually corrected in correction page. |
| Yield and Weather | [Incline Irradiation No Grid Outage or Curtailment](./yield_and_weather/irradiation.md) | Accumulated incline irradiation energy summarized only for periods having no curtailment or grid outage. |
| Yield and Weather | [Horizontal Irradiation](./yield_and_weather/irradiation.md) | Accumulated horizontal irradiation energy. Calculated from plant sensors, possibly  backfilled from external weather source. Can also be manually corrected in correction page. |
| Yield and Weather | [Transposition Factor](./yield_and_weather/transposition_factor.md) | Relation between incline and horizontal irradiation |
| Yield and Weather | [Module Temperature](./yield_and_weather/module_temperature.md) | Different calculations based on module temperature measurements and incline irradiation.  |
| Yield and Weather | [Soiling Index](./yield_and_weather/soiling_index.md) | Plant soiling index, from 0-100. Average value calculated from soiling stations or reference cells |
| Yield and Weather | [Budget Production](./yield_and_weather/production.md) | Budget production for a plant.  |
| Yield and Weather | [Budget Irradiation](./yield_and_weather/irradiation.md) | Budget incline irradiation for a plant |
| Production Loss | [Grid downtime production losses](./production_losses/grid_down_time_production_losses.md) | Production losses due to downtime on grid (reduced grid availability) |
| Production Loss | [Plant downtime production losses](./production_losses/plant_down_time_production_losses.md) | Production losses due to downtime on inverters (reduced plant availability) |
| Production Loss | [Tracker downtime production losses](./production_losses/tracker_down_time_production_losses.md) | Production losses due to non-working trackers (reduced tracker availability) |
| Production Loss | [String downtime production losses](./production_losses/string_down_time_production_losses.mdd) | Production losses due to non-available strings (reduced string availability) |
| Production Loss | [Curtailment production losses](./production_losses/curtailment_production_losses.md) | Production losses due to plant curtailment |
| Production Loss | [Clipping production losses](./production_losses/clipping_production_losses.md) | Production losses due to plant clipping |
| Production Loss | [Soiling production losses](./production_losses/soiling_production_losses.md) | Production losses due to panel soiling |
| Production Loss | [Snow production losses](./production_losses/snow_production_losses.md) | Production losses due to snow on panels. |
| Production Loss | [Manually excluded energy losses](production_losses/manually_excluded_energy_losses.md) | Production losses manually registered. |
| Revenue Loss | [Grid downtime revenue loss](./production_losses/grid_down_time_production_losses.md) | Revenue losses due to downtime on grid  (reduced grid availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Plant downtime revenue loss](./production_losses/plant_down_time_production_losses.md) | Revenue losses due to downtime on inverters (reduced plant availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Tracker downtime revenue loss](./production_losses/tracker_down_time_production_losses.md) | Revenue losses due to non-working trackers (reduced tracker availability). Energy tariff taken from internal original budget |
| Revenue Loss | [String downtime revenue losses](./production_losses/string_down_time_production_losses.md) | Revenue losses due to non-available strings (reduced string availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Curtailment revenue losses](./production_losses/curtailment_production_losses.md) | Revenue losses due to plant clipping. Energy tariff taken from internal original budget |
| Revenue Loss | [Clipping revenue losses](./production_losses/clipping_production_losses.md) | Revenue losses due to panel soiling. Energy tariff taken from internal original budget |
| Revenue Loss | [Soiling revenue losses](./production_losses/soiling_production_losses.md) | Revenue losses due to panel soiling. Energy tariff taken from internal original budget |
| Revenue Loss | [Snow revenue losses](./production_losses/snow_production_losses.md) | Revenue losses due to snow on panels. Energy tariff taken from internal original budget |
| Revenue Loss | [Manually excluded revenue losses](production_losses/manually_excluded_energy_losses.md) | Revenue losses manually registered. Energy tariff taken from internal original budget |
| Availability | [Plant availability daylight](./availability_and_downtime/plant_availability.md) | Plant availability measured as Daylight time – Plant downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Plant availability full day](./availability_and_downtime/plant_availability.md) | Plant availability measured as Full day time – Plant downtime (in minutes) / Full day time (24 hours) |
| Availability | [Plant availability production loss](./availability_and_downtime/plant_availability.md) | Plant availability measured as Total production including losses – Inverter losses / (Total production including losses) |
| Availability | [Grid availability daylight](./availability_and_downtime/grid_availability.md) | Grid availability measured as Daylight time – Grid downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Grid availability full day](./availability_and_downtime/grid_availability.md) | Grid availability measured as Full day time – Grid downtime (in minutes) / Full day time (24 hours) |
| Availability | [Grid availability production loss](./availability_and_downtime/grid_availability.md) | Grid availability measured as Total production including losses – Grid losses / (Total production including losses) |
| Availability | [Tracker availability daylight](./availability_and_downtime/tracker_availability.md) | Tracker availability measured as Daylight time – tracker downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Tracker availability full day](./availability_and_downtime/tracker_availability.md) | Tracker availability measured as Full day time – tracker downtime (in minutes) / Full day time (24 hours) |
| Availability | [Tracker availability production loss](./availability_and_downtime/tracker_availability.md) | Tracker availability measured as Total production including losses / (Total production including losses + Tracker losses) |
| Availability | [String availability](./availability_and_downtime/string_availability.md) | Availability of strings calculated based on string production and detection of non producing strings. |
| Availability | [String availability production loss](./availability_and_downtime/string_availability.md) | String availability measured as Total production including losses / (Total production including losses + String losses) |
| Performance | [PR Contractual](./performance/pr_contractual.md) | PR from contract for a given plant |
| Performance | [PR Net](./performance/pr_net.md) | PR basic calculation. Only looking at irradiance and production. Does not adjust for the module degradation in the nominal power. |
| Performance | [PR Gross](./performance/pr_gross.md) | Uses PR net as basis. Divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced  |
| Performance | [PR Gross Production Loss](./performance/pr_gross_production_loss.md) | Uses PR net as basis, but production is using measured production + estimated production  |losses due to Plant and Grid downtime. |
| Performance | [PR Net Temp Adjusted](./performance/pr_temperature_adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Net” |
| Performance | [PR Gross Temp Adjusted](./performance/pr_temperature_adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross” |
| Performance | [PR Gross Production Loss Temp Adjusted](./performance/pr_temperature_adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross Production Loss” |
| Performance | [Energy Performance Index](./performance/energy_performance_index.md) | Performance of production vs. irradiation, related to budget and actual |
| Equipment specific | [Inverter](equipment_specific/equipment_inverter.md)| KPI's per inverter |
| Equipment specific | [String](equipment_specific/equipment_string.md)| KPI's per string |
| Equipment specific | [Tracker](equipment_specific/equipment_tracker.md)| KPI's per tracker |
