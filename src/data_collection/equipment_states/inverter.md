# Inverter States

State of inverters are calculated automatically based on following input signals:
- Operation mode reported by inverter
- Alarms reported by inverter
- Power measured from inverter
- Measures irradiation from plant pyranometer sensors
    - Average value from horizontal pyranometers (including installation on control building)
- Grid state

The following main principle will apply for calculation of the downtimes:
- During night (irradiation below 5 W/m2) no downtime is registered. (states not idle time or failure time)
- “Grid down” result in line restraint time.
- All stops on inverter not due to grid down, is “Idle” or “Failure” time resulting in downtime and reduced availability 
- All manual codes are grouped as “Idle” time (resulting in downtime), but classified to make it possible to extract and group in special reports if needed
- When moving downtime from plant to grid, “Grid down” state on inverter shall be used (“line restraint” not resulting in plant downtime). At same time, “No operation” must be set on grid for same period to make sure grid availability is used. 
- During night, time must be set to one of the “Not scheduled” states if manually corrected. If not, daytime availability will be wrong. Total time to calculate availability is based on states not being “Not scheduled”

Standard state codes shown below:

|StateType|StateCode|StateName|StateClass|
|------------|---------|---------|---------|
|Inverter|	309	|Operation|	Production time|
|Inverter|	310	|Operation with warning|Production time|
|Inverter|	311	|Operation with failure|Production time|
|Inverter|	401	|Warning Idle|	Idle time|
|Inverter|	402	|Stopped	|Idle time|
|Inverter|	403	|Not started	|Idle time|
|Inverter|	404	|Waiting for PV	|Line restraint time|
|Inverter|	455	|Warning Production	|Production time|
|Inverter|	1800	|Failure	|Failure time|
|Inverter|	2000	|Preventive Maintenance	|Unscheduled|
|Inverter|	2001	|Corrective Maintenance	|Failure time|
|Inverter|	2002	|Downtime due to utility	|Line restraint time|
|Inverter|	2003	|Downtime due to Force Majeure	|Line restraint time|
|Inverter|	1500	|No power production	|Not Scheduled|
|Inverter|	1501	|Grid down	|Line restraint time|
|Inverter|	1502	|Grounded	|Idle time|
|Inverter|	1503	|Statcom	|Line restraint time|
|Inverter|	10200	|Night failure	|Not Scheduled|
|Inverter|	10201	|Night warning	|Not Scheduled|
|Inverter|	10202	|Night grounded	|Not Scheduled|

 