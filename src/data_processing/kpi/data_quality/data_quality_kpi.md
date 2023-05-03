# Data Quality KPI

Data quality KPI data is calculated and stored in the data base for reports and dashboards. 

Total data quality KPI for a plant and period is calculated weighing each of th 15 sub factors with the Weight in the table below.

|No	|Test Name		|Weight	|Criteria	|Top Score	|Low Score	|Calculation Details|
|---------|---------|---------|---------|---------|---------|---------|
|1|	Meter consistency|		0.15|	%-ratio of sum of main meter(s) vs. back-up meters vs. meter proxy (PPC and/or MV meters)	|Main meter(s) + back up meter(s) + MV meters (<1% diff)|	Main meter(s) + back up meter(s) + MV meters (<5% diff)	|Mainly backup meters and power analysers. Not all plants has MV meters. Active energy summarized per meter group and day. Max difference from meter group Main is calculated. See Equipment setup report for meter group settings. Only summarizing energy when irradiation is above 100 W/m2.|
|2|	Inverter AC output consistency|		0.2 (0.25 if not trackers)|	Sum of AC-inverter output vs. sum of main meter|	Sum of AC-inverter output < 3% of main meters	|Sum of AC-inverter output more than 10% of main meeters|	Looking at AC energy on inverter and total production on plant (also manually corrected). Calculating absolute difference in percent. Adjusting for AC losses based on AC losses set in plant parameters. Only using data when irradiation is above 100 W/m2.|
|3|	DC level consistency|		0.15 (0.2 if not trackers)|	Sum of DC-inverter input vs. measured sum of string combiner output for each inverter|	Sum/average of inverter DC-input < 5% of sum/average of DC string-output calculated first for each inverter and then averaged across all inverters|	Sum/average of inverter DC-input < 15% of sum/average of DC string-output calculated first for each inverter and then averaged across all inverters	|Difference between current (current-hours) on string measurement and inverter DC input measures. Difference is calcualted per inverter as percentage value per day, and average absolute value for all inverters used as input to KPI.Inverter DC current calculated as average DC current from 6-18 mulitplied by number of hours. DC current on string is sum of current-hours for connected strings in morning (6-10), midday (10-14) and afternoon (14-18) based on DC current measurement.|
|4|	Tracker data availability|		0.1|	Availability of tracker data (angles) - % of total amount of trackers|	100% of tracker signals available|	0% of tracker signals available	|Measured angle tag on tracker is used. Counting number of 10 minute values missing from tracker (no communication with tracker) in data warehouse and counting total missing values vs. total values for all trackers. Only data counted when irradiation is above 100 W/m2.|
|5|	GHI consistency|		0.05|	% deviation between GHI pyranometers that are not excluded from filtering |	Average %-deviation across all sensors to median is less than 2%|	Average %-deviation across all sensors to median is less than 6%|	Looking at 10 minute values in data warehouse. Only data not manual filtered using the sensor out of order function in the SCADA system is used. Looking at all data points, also data with obvious wrong values due to wrong calibrated on non-working sensor. Calculating average value for day for each sensor when plant irradiation level is above 100 W/m2. Median value calculated for all sensors. Max difference for all sensors compared to median is used as concistency input.|
|6|	GHI data availability|		0.05|	% of data excluded from all pyranometers|	0% of data excluded based on filtering|	100% of data excluded based on filtering	|Looking at 10 minute values in data warehouse. Values not beeing manual filtered as sensor out of order, automatically filtered by DWH filtering algoruthm (level, median and tracker) and values not having missing communication is counted as good/OK values. Only considering data points when irradiation is above 100 W/m2. See Weather sensor report|
|7|	GII consistency|		0.05|	% deviation between GII pyranometers that are not excluded from the filtering|	Average %-deviation across all sensors to median is less than 3%|	Average %-deviation across all sensors to median is less than 8%	|Same principle as GHI
|8|	GII data availability|		0.05|	% of data excluded from all pyranometers|	0% of data excluded based on filtering|	100% of data excluded based on filtering|	Same principle as GHI|
|9|	Module temp consistency|		0.05|	Deviation in delta T between module temp sensors that are not excluded from the filtering|	Average deviation (in C) to median is less than 2 C	|Average deviation (in C) to median is less than 8 C	|Same principle as GHI, but using C as unit og deviation and not percentage|
|10|	Module temp data availability|		0.05|	% of data excluded from module temp sensors|	0% of data excluded based on filtering|	100% of data excluded based on filtering	|Same principle as GHI|
|11|	Soiling sensor data availability|		0.05|	% of data excluded from soiling sensor|	0% of data excluded based on filtering|	100% of data excluded based on filtering|	Using soiling station data if that is used, and clean reference cell if only reference cells are used|
|12|	Ambient temperature consistency	|	0.0125|	Deviation in delta T between ambient temp sensors|	Average deviation (in C) to median is less than 1 C|	Average deviation (in C) to median is less than 4 C|	Same principle as GHI, but using C as unit og deviation and not percentage|
|13|	Ambient temperature data availability|		0.0125|	% of data excluded from temperature sensor in data warehouse calculation|	0% of data excluded based on filtering	|100% of data excluded based on filtering	|Same principle as GHI|
|14|	Wind sensor consistency|		0.0125|	Deviation in m/s between wind sensors|	Average deviation (in m/s) to median is less than 1 m/s	|Average deviation (in m/s) to median is less than 3 m/s	|Same principle as GHI, but using m/s as unit og deviation and not percentage|
|15|	Wind sensor data availability	|	0.0125|	% of data excluded from wind sensor in data warehouse calculation|	0% of data excluded based on filtering	|100% of data excluded based on filtering|	Same principle as GHI|