# String availability

Following calculation applies:
1.	String availability = weighted average (weighted by nominal power Wp) of availability for all strings.
2.	String availability production loss = E_meas_gross / (E_meas_gross +[String Downtime Production Loss](../../Production%20Losses/String%20down%20time%20production%20losses/String%20down%20time%20production%20losses.md))

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
- String availability production loss = E_meas_gross / (E_meas_gross + [String Downtime Production Loss](../../Production%20Losses/String%20down%20time%20production%20losses/String%20down%20time%20production%20losses.md))
    - E_meas_gross = [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) + [Grid Downtime production Loss](../../Production%20Losses/Grid%20down%20time%20production%20losses/Grid%20down%20time%20production%20losses.md) + [Plant Downtime Production Loss](../../Production%20Losses/Plant%20down%20time%20production%20losses/Plant%20down%20time%20production%20losses.md) + [String Downtime Production Loss](../../Production%20Losses/String%20down%20time%20production%20losses/String%20down%20time%20production%20losses.md) + [Curtailment Production Loss](../../Production%20Losses/Curtailment%20production%20losses/Curtailment%20production%20losses.md) + [Clippping Production Loss](../../Production%20Losses/Clipping%20production%20losses/Clipping%20production%20losses.md) + [Soiling Production Loss](../../Production%20Losses/Soiling%20production%20losses/Soiling%20production%20losses.md) + [Snow Production Loss](../../Production%20Losses/Snow%20production%20losses/Snow%20production%20losses.md) + [Tracker Downtime Production Loss](../../Production%20Losses/Tracker%20down%20time%20production%20losses/Tracker%20down%20time%20production%20losses.md)
    

