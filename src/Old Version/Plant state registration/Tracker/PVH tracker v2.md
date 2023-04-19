# PVH Tracker v2

Trackers are controlled with common NCU control unit from Suntrack.

Equipment status and downtime is to be logged for the equipment below:

* One registration for each tracker   

Each state change is logged in the ACT DB SQL database and transferred to data warehouse. This is used for availability calculations and performance ratio reporting.

State logging is set up for all trackers. Each tracker unit is considered a process unit with naming:

* Tracker process unit naming:
    * NO-OS-TR-TXX.TYYY
        * XX: station name from 01 to number of stations
        * YYY: TCU number from 001 to number of trackers per NCU

Received operating state is derived from status tags for each Tracker.

When it is detected externally that there is no irradiation to generate power on the Trackers (below 5 W/m2), code 7100 is set.

When it is detected grid is down, code 7105 is set.

Following codes are used:

|Code|Name|Class|Calculation|Colour|
|---|---|---|---|---|
|7000|Manual mode|Line Restraint Time|Main state=1 (Manual) AND No alarms|Yellow|
|7001|Tracking the Sun|Production Time|Main state=2 (Auto) AND No alarms|Green|
|7006|Stopped|Idle time|Main state=0 Stopped|Grey|
|7401|Warning mode|Production time|One or more of the alarms:<br><li> Alarm indicator: SW version is a test build for accelarated time test.<br><li> AlarmZigbee_s1: Zigbee Module Communication Failure<br><li> Alarm indicator: Low speed condition detected at axis1.<br><li> Alarm indicator: UTC time has never been set.|Yellow|
|7402|Fault mode|Failure Time|One or more of the alarms:<br><br><li> Alarm Indicator: Communication Failure<br><li> Alarm indicator: System monitor has detected an out of range or fault condition (check system monitor status)<br><li> Alarm indicator: Emergency stop button pressed<br><li> Alarm indicator: Hardware limit switch reached (axis1 Bottom)<br><li> Alarm indicator: Hardware limit switch reached (axis1 Top)<br><li> Alarm indicator: Blocked condition detected at axis1.<br><li> Alarm indicator: Motor Overcurrent detected by software detector<br><li> Alarm indicator: Motor Overcurrent detected by hardware protection|Red|
|7403|Safe position|Idle time|Safe position state|Red|
|7404|East position|Idle time|East position|Grey|
|7405|West position|Idle time|West position|Grey|
|7410|Communication Error|Failure Time|Communcation on NCU down (connected tag false)<br>Alarms NCU:<br>Gateway 1 Communication failure or Gateway 2 Communication failure (the one used for the slave)<br>Commissioning Status wrong. (not defined)|White|
|7100|No production|Not Scheduled|Irradiation < 5|Gray|
|7101|Preventive Maintenance|Unscheduled Time|Manual input||
|7102|Corrective Maintenance|Failure Time|Manual input||
|7103|Downtime due to utility|Line Restraint Time|Manual input||
|7104|Downtime due to Force Majeure|Line Restraint Time|Manual input||
|7105|Grid down|Line Restraint Time|Grid connection detected down|Gray|
 