# GE Inverter

State logging is set up for all inverters. Each inverter within the SKiD is considered a process unit. Naming is set to:

\<Country\>-\<Site\>-TSXY.I0Z:
 
* Country is two characters code.
* Site is two characters code.
* X is plant number within site
* Y is number of TCS station in plant.
* Z is inverter number

Example:

* NO-OS-TS12.I04 for Oslo 1, TSC 2, inverter 4

Received operating state is derived from status tags for each inverter.

When it is detected externally that there is no irradiation to generate power on the inverters (below 5 W/m2), code 1500 is set.

When it is detected grid is down, code 1501 is set.

Following codes are used:

|Code|Name|Class|Calculation|
|---|---|---|---|
|295|MPP reached|Production time|Inverter status  tag & incline irradiation > 5W/m2|
|309|Operation|Production time|Inverter status  tag & incline irradiation > 5W/m2|
|1468|MPP search|Production time|Inverter status  tag & incline irradiation > 5W/m2|
|1470|Fault|Failure time|Inverter status  tag & incline irradiation > 5W/m2|
|1500|No power production|Line restraint time|incline irradiation > 5W/m2|
|1501|Grid down|Line restraint time|Grid not connected|
|2000|Preventive Maintenance|Unscheduled|Inverter status  tag & incline irradiation > 5W/m2|
|2001|Corrective Maintenance|Failure time|Inverter status  tag & incline irradiation > 5W/m2|
|2002|Downtime due to utility|Line restraint time|Inverter status  tag & incline irradiation > 5W/m2|
|2003|Downtime due to Force Majeure|Line restraint time|Inverter status tag & incline irradiation > 5W/m2|
|2300|Ready to switch on|Idle time|Inverter status  tag & incline irradiation > 5W/m2|
|2306|Switching ON disabled|Failure time|Inverter status  tag & incline irradiation > 5W/m2|
|2308|Line loss|Idle time|Inverter status  tag & incline irradiation > 5W/m2|
|2311|Internal limit active|Production time|Inverter status  tag & incline irradiation > 5W/m2|
|2312|FRT|Failure time|Inverter status  tag & incline irradiation > 5W/m2|
|2320|Manual stop|Idle time|Inverter status  tag & incline irradiation > 5W/m2|
|2322|Waiting|Line restraint time|Inverter status  tag & incline irradiation < 120W/m2|
|2323|Cooling initialization|Line restraint time|Inverter status  tag & incline irradiation < 120W/m2|
|2327|PV power reduction|Production time|Inverter status  tag & incline irradiation > 5|
|3322|Waiting, Idle|Idle time|Inverter status  tag & incline irradiation > 120W/m2|
|3323|Cooling initialization, Idle|Idle time|Inverter status  tag & incline irradiation > 120W/m2|
|10381|Stop, no power production|Not Scheduled|Inverter status  tag & incline irradiation > 5W/m2|
|12100|Error, no power production|Not Scheduled|Inverter status  tag & incline irradiation > 5W/m2|
