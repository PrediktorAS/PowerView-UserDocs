# PR Net Temp Adjusted

The temp adjusted PR is calculated as shown below:

PR Net Temp Adjusted = [PR Net](../PR%20Net/PR%20Net.md) / (1 - Ptpv) 

-	Ptpv: Thermal losses factor of Module
    - Ptpv = (Tmda - Tmdb) * ɣ / 100
        - Tmda: Estimated cell temperature daylight weighted measured. Average measured [module temperature](../../Yield%20and%20Weather/Module%20Temperature/Module%20Temperature.md) weighted with incline irradiation measured (10 minute intervals) when irradiation is above 5 W/m2
        - Tmdb: Estimated cell temperature daylight budget number. Average number for period (e.g. from PVsyst)
        - ɣ:  Power temperature coefficient of the Module, as supplied by the Module producer (%/°C)

