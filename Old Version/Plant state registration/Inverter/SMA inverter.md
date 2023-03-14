# SMA Inverter

Algorithm for define the state as below:

```
if (Incline Irradiation < 5 W/m2)
(
If Inverter Mode = 381 or 1392 or 1560 or 2383
    State code = 10000 + Inverter Mode  [error/idle no power production]
else
    State code = 1500        [No power production]
)
else if (Grid off)
    State code = 1501  [Grid down]
else if (State code = 1393 AND Incline Irradiation > 90 W/m2)
    State code = 1693  [Wait for PV grid, Idle time reducing plant availability]
else if (State code = 1394 AND Grid on)
    State code = 1694  [Wait for AC grid, Idle time reducing plant availability]
else if (State code = 1480 AND Grid on)
    State code = 1680  [Wait for electricity supplier, Idle time reducing plant availability]
else if ((Event_ID = 3504 OR Event_ID = 3505 OR Event_ID = 3515 OR Event_ID =
               3601 OR Event_ID = 6004 OR Event_ID = 6005) AND State code = 1392)
    State code = 455  [Warning]
else 
    State code = Inverter Mode
```

General states as follows:

|State code|State name|State Class|Type|
|---|---|---|---|
|309|Operation|Production time|From inverter mode|
|381|Stop|Idle time|From inverter mode|
|455|Warning|Production time|From inverter mode and Event ID|
|1392|Error|Failure time|From inverter mode|
|1393|Wait for PV voltage|Line restraint time|From inverter mode|
|1394|Wait for AC grid|Line restraint time|From inverter mode|
|1480|Wait for electricity supplier|Line restraint time|From inverter mode|
|1500|No power production|Not scheduled|From irradiation values, irradiation below 5 W/m2|
|1501|Grid down|Line restraint time|From grid state|
|1560|Event Remote Stop|Idle time|From inverter mode|
|1693|Wait for PV voltage, idle|Idle time|From inverter mode and irradiation values|
|1694|Wait for AC grid, idle|Idle time|From inverter mode and grid state|
|1680|Wait for electricity supplier, idle|Idle time|From inverter mode and grid state|
|2000|Preventive Maintenance|Line restraint time|Manual input|
|2001|Corrective Maintenance|Failure time|Manual input|
|2002|Downtime due to Utility|Line restraint time|Manual input|
|2003|Downtime due to Force Majeure|Line restraint time|Manual input|
|2383|Manual resume|Idle time|From inverter mode|
|- - - | | |
|10381|Stop, no power production|Not scheduled|From inverter mode + “No power production”|
|11392|Error, no power production|Not scheduled|From inverter mode + “No power production”|
|11560|Event Remote Stop, no power production|Not scheduled|From inverter mode+ “No power production”|
|12383|Manual resume, no power production|Not scheduled|From inverter mode+ “No power production”|
