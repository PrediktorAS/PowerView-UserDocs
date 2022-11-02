# Idemasun Tracker

Received operating state is derived from status tags for each Tracker.

When it is detected externally that there is no irradiation to generate power on the Trackers (below 5 W/m2), code 7100 is set.

When it is detected grid is down, code 7105 is set.

|State code|State name|State Class|Type|
|---|---|---|---|
|7000|Operation|Production time|From tracker state signal|
|7001|General Error|Failure time|From tracker state signal|
|7002|Out of range|Failure time|From tracker state signal|
|7003|Positioning failed|Failure time|From tracker state signal|
|7004|Failure of Sensor|Failure time|From tracker state signal|
|7005|Wrong turning direction|Failure time|From tracker state signal|
|7007|Manual Mode: Positioning|Line restraint time|From tracker state signal|
|7008|Manual Mode: Reference Position Programming||From tracker state signal|
|7009|Manual Mode: Reset|Idle time|From tracker state signal|
|7010|Reference Position not programmed|Production time|From tracker state signal|
|7011|Tracker locked, no valid license|Failure time|From tracker state signal|
|7020|Tracker Communication Error|Failure time|From tracker state signal|
|7100|No power production|Not scheduled|From irradiation measurements|
|7101|Preventive Maintenance|Unscheduled|Manual input|
|7102|Corrective Maintenance|Failure time|Manual input|
|7103|Downtime due to utility|Line restraint time|Manual input|
|7104|Downtime due to Force Majeure|Line restraint time|Manual input|
|7105|Grid down|Line restraint time|From grid state signal|
 