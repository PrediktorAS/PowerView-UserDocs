# Temperature adjusted PR calculations

The temperature of a module affects its performance. The KPIs can be adjusted to reflect the performance of the modules at the actual temperature. For more information on the temperature of the modules, see [Module Temperature](../yield_and_weather/module_temperature.md).

## Formula for thermal losses factor of the module (Ptpv)

> Ptpv = (Tmda - Tmdb) * ɣ / 100

### Variables
- `Tmda`: Estimated cell temperature daylight weighted measured. Average measured [module temperature](../yield_and_weather/module_temperature.md) weighted with incline irradiation measured (10 minute intervals) when irradiation is above 5 W/m2
- `Tmdb`: Estimated cell temperature daylight budget number. Average number for period (e.g. from PVsyst)
- `ɣ`:  Power temperature coefficient of the Module, as supplied by the Module producer (%/°C)


## KPIs adjusted for thermal losses factor of the module

> PR Net Temp Adjusted = [PR Net](pr_net.md) * (1 - Ptpv)

> PR Gross Temp Adjusted = [PR Gross](pr_gross.md) * (1 - Ptpv)

> PR Gross Production Loss Temp Adjusted = [PR Gross Production Loss](pr_gross_production_loss.md) * (1 - Ptpv)