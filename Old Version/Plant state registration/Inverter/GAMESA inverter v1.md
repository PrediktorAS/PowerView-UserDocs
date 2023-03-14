# GAMESA Inverter v1

Received operating state is derived from state tags for each inverter bridge:

* SM.State1
* SM.State2

|Codes|Name|
|---|---|
|0|Emergency|
|1|Stop|
|3|Grid connection|
|4|Generating|
|5|Test 1|
|6|Dip|
|8|Precharge|
|9|Charge|
|10|Grid disconnection|
|11|Waiting|

When it is detected externally that there is no irradiation to generate power on the inverters (below 5 W/m2), code 1500 is set.

When it is detected grid is down, code 1501 is set.

Following codes are used:

|Code|Name|Class|Calculation|Colour|
|---|---|---|---|---|
|309|Operation|Production Time|State = 4|Green|
|381|Stop|Idle time|State = 1|Grey|
|2100|Emergency|Failure time|State = 0|Red|
|2103|Grid connection|Line Restraint Time|State = 3|Yellow|
|2105|Test 1|Line Restraint Time|State = 5|Yellow|
|2106|Dip|Production Time|State = 6|Yellow?|
|2108|Precharge|Line Restraint Time|State = 8|Yellow|
|2109|Charge|Line Restraint Time|State = 9|Yellow|
|2110|Grid disconnection|Line Restraint Time|State = 10|Yellow|
|2111|Waiting|Not scheduled|State = 11|Grey|
|2000|Preventive Maintenance|Unscheduled Time|Manual input||
|2001|Corrective Maintenance|Failure Time|Manual input||
|2002|Downtime due to utility|Line Restraint Time|Manual input||
|2003|Downtime due to Force Majeure|Line Restraint Time|Manual input||
|1500|No power production|Not Scheduled|External|Grey|
|1501|Grid down|Line Restraint Time|External|Grey|
|10381|Stop, no power production|Not Scheduled|State = 1 && external|Grey|
|12100|Error, no power production|Not Scheduled|State = 0 && external|Red|
|16500|No power production, grid down|Not Scheduled|External|Grey|
