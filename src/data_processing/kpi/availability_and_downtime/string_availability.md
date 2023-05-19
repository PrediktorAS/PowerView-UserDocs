# String availability

Following calculation applies:
1.	String availability = weighted average (weighted by nominal power Wp) of availability for all strings.
2.	String availability production loss = E_meas_gross / (E_meas_gross +[String Downtime Production Loss](../production_losses/string_down_time_production_losses.md))

## String availability
String availability is calculated based on specific power on each string relative to group (combiner) median of specific power. 

When string has between 20% and 60% relative power, 50% availability is set for string. When relative power is below 20%, 0% availability is set on string.
String availability is calculated for the following aggregated periods (not 10 minute periods):
- Morning: 06:00 to 10:00
- Midday: 10:00 to 14:00
- Afternoon: 14:00 to 18:00

Exception rules are made to not get string downtime when inverter is not producing or tracker is malfunction:
1.	Inverter down or string combiner down:
    - When all strings connected to the inverter is down for the period, string availability is set to 100% for all strings on inverter.
    - When inverter has more than 50% registered downtime for period, string availability is set to 100% for all strings on inverter.
    - When string combiner median of specific power is less that 0.3, string availability is set to 100% for combiner
2.	Tracker down:
    - Tracker availability is calculated for the tracker connected to a string:
        - TrackerDowntimeFactor (0-1) per string:
	        - Calculated as average value for morning, midday and afternoon for each string
        - Limit to detect string availability for a string is adjusted according to following formula:
            - 20% * (1 - 0.5 * TrackerDowntimeFactor)
            - 60% * (1 - 0.5 * TrackerDowntimeFactor)

String availability for plant is calculated as the weighted average (weighted by nominal power WDCp) of availability for all strings. 

## String availability production loss
- String availability production loss = E_meas_gross / (E_meas_gross + [String Downtime Production Loss](../production_losses/string_down_time_production_losses.md))
    - E_meas_gross = [Actual Production](../yield_and_weather/production.md) + [Grid Downtime production Loss](../production_losses/grid_down_time_production_losses.md) + [Plant Downtime Production Loss](../production_losses/plant_down_time_production_losses.md) + [String Downtime Production Loss](../production_losses/string_down_time_production_losses.md) + [Curtailment Production Loss](../production_losses/curtailment_production_losses.md) + [Clipping Production Loss](../production_losses/clipping_production_losses.md) + [Soiling Production Loss](../production_losses/soiling_production_losses.md) + [Snow Production Loss](../production_losses/snow_production_losses.md) + [Tracker Downtime Production Loss](../production_losses/tracker_down_time_production_losses.md)
    

