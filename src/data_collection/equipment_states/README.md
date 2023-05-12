# Understanding Equipment State

Whether data is collected directly from equipment with our Plant Connector or from a SCADA system, some equipment types are capable of reporting a state. This state generally is related to whether the equipment is producing power or not, but given the complexity of the equipment, there are many different states that can be reported. Also, as renewable energy generation often are dependant on external conditions, the lack of production is not always related to a failure of the equipment. The logged state is amongst other things used to calculate downtime and availability.

The following equipment types can hold state in PowerView:
- [Grid connections](grid.md)
- [Inverters](inverter.md)
- [Trackers](tracker.md)

Any change in state for equipment within these equipment types are logged (the time of the change is logged together with the new state type). The changes originates from signals from the plant equipment and instrumentation. E.g. for the inverters, the operation mode and error signals are used to decide what state is set. State can be manually changed/overridden in the database using [Down Time Correction Screen](../../user_interfaces/manual/down_time_correction.md)

## State codes

State is set using a code in the form of a whole number. The state codes can be found on the equipment pages linked above. The state codes are defined in the following way:

|StateType|StateCode|StateName|
|------------|---------|---------|
|Tracker|	**402**	|Stopped	|

## State classes
The state codes are classified into state classes:
- **Production time**
- **Failure time**
- **Idle time**
- **Line restraint time**
- **Unscheduled**
- **Not scheduled**

Inverter state and grid state should not have down time at same time, so when grid is down, down time is not registered on inverter. This must also be considered when changing states manually, possibly both changing inverter and grid state.

The state code above with a state class would look like this:

|StateType|StateCode|StateName|StateClass|
|------------|---------|---------|---------|
|Tracker|	402	|Stopped	|**Idle time**|

##### Production time

The equipment is functioning and producing power as expected. This is the default state class for all equipment types. Please note that functioning does not equal producing power. E.g. an inverter can be functioning but not producing power due to a lack of irradiation. Also, a warning of some kind on the equipment does not necessarily mean that the equipment is not functioning. E.g. a warning on an inverter can be that the DC voltage is too high, but the inverter is still producing power.

##### Failure time

There is a technical failure on the equipment. This can be a failure that prevents the equipment from producing power, but it can also be a failure that does not prevent the equipment from producing power. It is counted as a state where the equipment is down.

##### Idle time

The equipment is not producing power, but it is not due to a technical failure. It is waiting for something else but counted as a state where the equipment is down.

##### Line restraint time

Refering to the "production line", the equipment is reporting restraints either above or below in the hierarchy. This is not counted as a state where the equipment is down.

##### Unscheduled

The equipment is scheduled out of the total operations time for reasons beyond the scope of the production team.

##### Not scheduled

Time where there are no operations going on at all.

## Understanding Downtime

Whenever a piece of equipment or a level in the plant hierarchy is not producing power but should, it is considered to be in downtime. Each state code, either through its state class or through the down time flag, is classified as either downtime or not downtime. There are a number of principles that apply to the calculation of downtime, stated on each equipment type, but it especially important to understand the relationship between grid, plant and inverters. Any downtime on the grid level will be logged at that level, but also the inverter level as grid downtime. This means the inverter will not be in downtime, but the grid will. This is important to understand when manually changing states. 

The downtime/availability of plants are calculated based on the downtime of the inverters, as plants do not hold a state. As this is the case, any availability KPI will in fact be the availability of all the inverters in that park. This is important to understand when manually changing states.

## Understanding Availability

Availability is the time a piece of equipment or level in the plant hierarchy is functioning as expected. This means that the equipment is producing power when it should. The availability is calculated as the time in production divided by the total time. The total time is the time in production plus the downtime. The availability is calculated for each equipment type and for the plant as a whole. The availability of the plant is calculated as the weighted average of the availability of the equipment types. The weighting is based on the nominal power of the equipment type. This means that the availability of the equipment type with the highest nominal power will have the largest impact on the plant availability.
