# PR Gross Temp Adjusted

The temp adjusted PR is calculated as shown below:

PR Gross Temp Adjusted = [PR Gross](pr_gross.md) / (1 - Ptpv) 

-	Ptpv: Thermal losses factor of Module
    - Ptpv = (Tmda - Tmdb) * ɣ / 100
        - Tmda: Estimated cell temperature daylight weighted measured. Average measured [module temperature](../yield_and_weather/module_temperature.md) weighted with incline irradiation measured (10 minute intervals) when irradiation is above 5 W/m2
        - Tmdb: Estimated cell temperature daylight budget number. Average number for period (e.g. from PVsyst)
        - ɣ:  Power temperature coefficient of the Module, as supplied by the Module producer (%/°C)

