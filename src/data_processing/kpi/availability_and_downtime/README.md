# Availability and Downtime

Availability is calculated on different levels of a solar plant:
- Grid
- Inverter / plant
- Tracker
- String

Availability is calculated based on state registration and down time calculations as described in [Equipment States](../../../Data%20Collection%20&%20Data%20Flow/Equipment%20States/Equipment%20States.md)

For detailes on KPI's calculated

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Availability | [Plant availability daylight](plant_availability.md) | Plant availability measured as Daylight time – Plant downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Plant availability full day](plant_availability.md) | Plant availability measured as Full day time – Plant downtime (in minutes) / Full day time (24 hours) |
| Availability | [Plant availability production loss](plant_availability.md) | Plant availability measured as Total production including losses – Inverter losses / (Total production including losses) |
| Availability | [Grid availability daylight](grid_availability.md) | Grid availability measured as Daylight time – Grid downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Grid availability full day](grid_availability.md) | Grid availability measured as Full day time – Grid downtime (in minutes) / Full day time (24 hours) |
| Availability | [Grid availability production loss](grid_availability.md) | Grid availability measured as Total production including losses – Grid losses / (Total production including losses) |
| Availability | [Tracker availability daylight](tracker_availability.md) | Tracker availability measured as Daylight time – tracker downtime (in minutes) / Daylight time (when irradiance is above 5 W/m2) |
| Availability | [Tracker availability full day](tracker_availability.md) | Tracker availability measured as Full day time – tracker downtime (in minutes) / Full day time (24 hours) |
| Availability | [Tracker availability production loss](tracker_availability.md) | Tracker availability measured as Total production including losses / (Total production including losses + Tracker losses) |
| Availability | [String availability](string_availability.md) | Availability of strings calculated based on string production and detection of non producing strings. |
| Availability | [String availability production loss](string_availability.md) | String availability measured as Total production including losses / (Total production including losses + String losses) |
