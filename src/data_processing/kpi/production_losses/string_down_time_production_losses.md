# String down time production losses

String losses are calculated in two ways:
- String losses per plant
- String losses per string set (channel)

## String losses per plant
String availability losses are calculated based on [String Availability](../availability_and_downtime/string_availability.md) for plant, but only availability during midday hours are used for the entire day.
- Production Loss Strings = [Actual Production](../yield_and_weather/actual_production.md) * (1 - SA_midday) / SA_midday
    - SA_midday: String availability (0-1) for plant during midday 10-14 hours

## String losses per string set (channel) 
Losses cacluated per string based on [String Availability](../availability_and_downtime/string_availability.md) per string during mid day.

- Production Loss Strings =  NominalPower * (SpecificEnergyPlantMedian - SpecificEnergyString)
    - NominalPower: nominal DC power for string
    - SpecificEnergyPlantMedian: median specific energy (Wh/Wdcp) for all strings in plant
    - SpecificEnergyString: specific energy (Wh/WDCp) for string