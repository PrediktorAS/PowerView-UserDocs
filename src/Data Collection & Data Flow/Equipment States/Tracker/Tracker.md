# Tracker States

State of trackers is collected automatically based on following input:
- State/mode signals from tracker control unit
- Alarm signals from tracker control unit
- Measures incline irradiation 

States and state calculation will vary between tracker suppliers. General rules:
- Tracker is operating when following the sun
- When tracker is in a manual mode and/or in a fixed position, it is defined as idle
- When tracker reports an error, it is in failure mode.
- Night-time is defined as Not Scheduled
- Grid down is defined as Line Restraint. 
- Optional states to calculate tracker out of position. 
    - Warning as production (small deviation), error as alarm (large deviation)

Standard state codes shown below:

|StateType|StateCode|StateName|StateClass|
|------------|---------|---------|---------|
|Tracker|	7000	|Manual mode	|Line restraint time|
|Tracker|	7001	|Tracking the Sun	|Production time|
|Tracker|	7002	|Park position	|Line restraint time|
|Tracker|	7004	|Go east	|Line restraint time|
|Tracker|	7005	|Go west	|Line restraint time|
|Tracker|	7006	|Stopped	|Idle time|
|Tracker|	7100	|No production	|Not Scheduled|
|Tracker|	7101	|Preventive Maintenance	|Unscheduled|
|Tracker|	7102	|Corrective Maintenance	|Failure time|
|Tracker|	7103	|Downtime due to utility	|Line restraint time|
|Tracker|	7104	|Downtime due to Force Majeure	|Line restraint time|
|Tracker|	7105	|Grid down	|Line restraint time|
|Tracker|	7401	|Warning mode	|Production time|
|Tracker|	7402	|Fault mode	|Failure time|
|Tracker|	7403	|Emergency mode	|Idle time|
|Tracker|	7410	|Communication Error	|Failure time|
|Tracker|	7411	|Backtracking mode	|Production time|

