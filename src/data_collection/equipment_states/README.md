# Equipment States

Equipment in a solar PV plant is collected and aggregated to calculate down time, availability and production losses.

In PowerView currently three equipment types have state logging:
- [Grid connections](grid.md)
- [Inverters](inverter.md)
- [Trackers](tracker.md)

The state of each of the equipment within these equipment types are continuously logged in a database. When the state is changed, the time of the change is logged together with the new state type. 
State is automatically logged based on signals from the plant equipment and instrumentation. E.g. for the inverters, the operation mode and error signals are used to decide what state is set.
State can be manually changed in the database using [Down Time Correction Screen](../../User%20Interfaces/Manual%20Data%20Registration/Down%20Time%20Correction/Down%20Time%20Correction.md)
The state codes are classified into state classes:
- Production time
- Failure time (defined as downtime)
- Idle time (defined as downtime)
- Line restraint time
- Not scheduled

Inverter state and grid state should not have down time at same time, so when grid is down, down time is not registered on inverter. 
This must also be considered when changing states manually, possibly both changing inverter and grid state.
