# GPTech Inverter

When it is detected externally that there is no irradiation to generate power on the inverters (below 5 W/m2), code 1500 is set.

When it is detected grid is down, code 1501 is set.

Following codes are used:

|Code|Name|Class|Calculation|Colour|
|---|---|---|---|---|
|309|Operation|Production Time|Module status = 10 & WD3 status = 1|Green|
|2201|No Active|Idle Time|Module status = 0 & WD3 status = 1|Grey|
|2202|Disconnected|Idle Time|Module status = 1 & WD3 status = 1|Grey|
|2203|Test Mode|Idle Time|Module status = 2 & WD3 status = 1|Grey|
|2204|DC Precharge|Line Restraint Time|Module status = 3 & WD3 status = 1|Yellow|
|2205|DC Connected|Line Restraint Time|Module status = 4 & WD3 status = 1|Yellow|
|2206|DC Connected End|Line Restraint Time|Module status = 5 & WD3 status = 1|Yellow|
|2207|AC Capacitor Precharge|Line Restraint Time|Module status = 6 & WD3 status = 1|Yellow|
|2208|AC Precharge|Line Restraint Time|Module status = 7 & WD3 status = 1|Yellow|
|2209|AC Connected|Line Restraint Time|Module status = 8 & WD3 status = 1|Yellow|
|2210|AC Connected End|Line Restraint Time|Module status = 9 & WD3 status = 1|Yellow|
|2211|Q at night mode|Not scheduled|Module status = 11 & WD3 status = 1|Grey|
|2212|WD3 Standby|Idle Time|WD3 status = 0|Grey|
|2213|WD3 Stopping|Idle Time|WD3 status = 2|Yellow|
|2214|WD3 Error|Failure time|WD3 status = 3|Red|
|2000|Preventive Maintenance|Unscheduled Time|Manual input||
|2001|Corrective Maintenance|Failure Time|Manual input||
|2002|Downtime due to utility|Line Restraint Time|Manual input||
|2003|Downtime due to Force Majeure|Line Restraint Time|Manual input||
