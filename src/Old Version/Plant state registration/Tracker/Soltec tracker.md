# Soltec Tracker

Equipment status and downtime is to be logged for the equipment below:

* One registration for each tracker
* Trafo switch open affect downtime on all applicable trackers

State logging is set up for all trackers. Each tracker unit is considered a process unit. Naming as below:

\<Country\>-\<Site\>-TR.TXYCZZ:

* Country is two characters code.
* Site is two characters code.
* X is plant number within site
* Y is number for TCS station in plant
* C is tracker column
* ZZ is Tracker number

Received operating state is derived from status tags for each Tracker].

When it is detected externally that there is no irradiation to generate power on the Trackers (below 5 W/m2), code 7100 is set.

When it is detected grid is down, code 7105 is set.

Following codes are used:

|Code|Name|Class|Calculation|Colour|
|---|---|---|---|---|
|7000|Defense position|Line Restraint Time|Working mode = 0|Yellow|
|7001|Tracking the Sun|Production Time|Working mode = 1|Green|
|7003|Move to a target roll|Line Restraint Time|Working mode = 3|Yellow|
|7004|Move to the East limit|Line Restraint Time|Working mode = 4|Yellow|
|7005|Move to the West limit|Line Restraint Time|Working mode = 5|Yellow|
|7006|Stop the motor|Idle Time|Working mode = 6|Gray|
|7204|Communication down|Failure Time|Communication down|Red|
|7205|Wind alarm state|Failure Time|Fault wind gateway|Red|
|7100|No production|Not Scheduled|Irradiation < 5|Gray|
|7101|Preventive Maintenance|Unscheduled Time|Manual input||
|7102|Corrective Maintenance|Failure Time|Manual input||
|7103|Downtime due to utility|Line Restraint Time|Manual input||
|7104|Downtime due to Force Majeure|Line Restraint Time|Manual input||
|7105|Grid down|Line Restraint Time|Grid connection detected down|Gray|
