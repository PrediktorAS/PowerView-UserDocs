# SAR Tracker

Received operating state is derived from status tags for each Tracker.

When it is detected externally that there is no irradiation to generate power on the Trackers (below 5 W/m2), code 7100 is set.

When it is detected grid is down, code 7105 is set.

|State code|State name|State Class|Type|
|---|---|---|---|
|7000|Operation|Production time|From tracker state signal|
|7001|Operation with warning|Production time|From tracker state signal|
|7002|Park position|Line restraint time|From tracker state signal|
|7003|Stop|Idle time|From tracker state signal|
|7004|Go east|Line restraint time|From tracker state signal|
|7005|Go west|Line restraint time|From tracker state signal|
|7006|Drive to angle|Line restraint time|From tracker state signal|
|7007|Failure|Failure time|From tracker state signal|
|7008|No power production|Not scheduled|From irradiation measurements|
|7009|Local control|Line restraint time|From tracker state signal|
|7010|Preventive Maintenance|Unscheduled|Manual input|
|7011|Corrective Maintenance|Failure time|Manual input|
|7012|Downtime due to Eskom|Line restraint time|Manual input|
|7013|Downtime due to Force Majeure|Line restraint time|Manual input|
|7020|Communication failure|Failure time|From tracker state signal|
 