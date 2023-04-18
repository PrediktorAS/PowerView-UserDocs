# Grid State

The grid state is normally calculated based on switch status.

In addition, manual codes can be entered.

The calculation might vary from plant to plant, so look in each plant section for specific rules. Main rules are:

```
    if (All grid breakers open)   
    (
    if (Incline Irradiation <5W/m2)
        State code = 16500   [No power production, grid down]
    else
        State code = 6004   [No Operation]
    )
    else if (Frequency outside alarm limits)
    (
    if (Incline Irradiation < 5W/m2)
        State code = 16500   [No power production, grid down]
    else
            State code = 6003   [Failure on grid frequency]
    )
    else if (Voltage outside alarm limits)
    (
    if (Incline Irradiation < 5W/m2)
        State code = 16500   [No power production, grid down]
    else
        State code = 6005   [Failure on grid voltage]
    )
    else if (Incline Irradiation < 5W/m2)
            State code = 6500        [No power production]
    else if (All grid breakers closed AND Grid Power >0)   
        State code = 6000   [Full Operation]
    else if ((One or more grid breakers closed)  AND Grid Power >0)   
            State code = 6001   [Half Operation]
    else if ((One or more grid breakers closed)  AND Grid Power = 0)   
            State code = 6002   [Operation, no power]
```

General states are:

|State code|State name|State Class|Type|
|---|---|---|---|
|6000|Full Operation|Production time|From breaker signals|
|6001|Half Operation|Production time|From breaker signals|
|6002|Operation, no power|Production time|From breaker signals and active power measurements|
|6003|Failure on grid frequency|Failure time|From frequency signal on power analyzer meters|
|6004|No Operation|Idle time|From breaker signals|
|6005|Failure on grid voltage|Failure time|From voltage signal on power analyzer meters|
|6010|Preventive Maintenance|Unscheduled|Manual input|
|6011|Corrective Maintenance|Failure time|Manual input|
|6012|Downtime due to Utility|Line restraint time|Manual input|
|6013|Downtime due to Force Majeure|Line restraint time|Manual input|
|6014|Downtime due plant failure|Unscheduled time|Manual input|
|6500|No power production|Not scheduled|From irradiation values|
|16500|No power production, grid down|Not scheduled|From irradiation values + grid down|

