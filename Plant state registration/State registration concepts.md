# State Registration concepts

Equipment or plant state are registered in the plant database. At any time, the equipment will have one unique state defined by the signals and the equipment state logic. The valid states or stop codes are defined in a web portal system setup page in the plant portal. When state changes on a equipment, the old current state is updated with an end time, and a new state is stored with this time as the start time. In this way, the database contains for all units defined for state registration, a continuous time line with unique states.

The states can be corrected by manual input screens and reported in reports with details and aggregations.

The state data is transferred to the data warehouse and used for availability and performance ratio calculations in the reports.

The following main state classes are used:

* Production time
* Failure time (causes reduced availability)
* Idle time (causes reduced availability)
* Line restraint time
* Unscheduled time
* Not scheduled time