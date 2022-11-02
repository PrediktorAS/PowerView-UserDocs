# PVH Tracker v1

Received operating state is derived from status tags for each Tracker].

When it is detected externally that there is no irradiation to generate power on the Trackers (below 5 W/m2), code 7100 is set.

When it is detected grid is down, code 7105 is set.

Following codes are used:

|Code|Name|Class|Calculation|Colour|
|---|---|---|---|---|
|7000|Manual mode|Line Restraint Time|Tracker mode = 10|Yellow|
|7001|Tracking the Sun|Production Time|Tracker mode = 20|Green|
|7401|Warning mode|Line Restraint Time|Tracker mode = 30/31|Yellow|
|7402|Fault mode|Failure Time|Tracker mode = 40|Red|
|7403|Tracker out of safety range|Line Restraint Time|!(Inc.meter east&west)|Yellow|
|7404|Tracker East|Line Restraint Time|Inc.meter east|Yellow|
|7405|Tracker West|Line Restraint Time|Inc.meter west|Yellow|
|7406|Tracker Centered|Line Restraint Time|Inc.meter east&west|Yellow|
|7407|E-Stop/Limit|Line Restraint Time|E-Stop/Limit switch|Yellow|
|7408|Go to angle|Line Restraint Time|GoToAngle = 1|Yellow|
|7410|Communication Error|Failure Time|Comm.status = 0|Red|
|7411|VFD Fault|Failure Time|VFD Fault = 1|Red|
|7412|Motor Fault|Failure Time|Motor warning = 1|Red|
|7413|Main Stop|Failure Time|Main stop = 1|Red|
|7420|Back tracking|Production Time|Backtracking Active = 1|Green|
|7100|No production|Not Scheduled|Irradiation < 5|Gray|
|7101|Preventive Maintenance|Unscheduled Time|Manual input||
|7102|Corrective Maintenance|Failure Time|Manual input||
|7103|Downtime due to utility|Line Restraint Time|Manual input||
|7104|Downtime due to Force Majeure|Line Restraint Time|Manual input||
|7105|Grid down|Line Restraint Time|Grid connection detected down|Gray|
