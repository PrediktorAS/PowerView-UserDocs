# Equipment state registration
In SCADA, currently three equipment types have state logging:
- Inverters
- Grid connection
- Tracker
The state of each of the equipment within these equipment types are continuously logged in a database. When the state is changed, the time of the change is logged together with the new state type.
State is automatically logged based on signals from the plant equipment and instrumentation. E.g. for the inverters, the operation mode and error signals are used to decide what state is set.
State can be manually changed in the database using web input screens in plant web portal (PS: not available in central web portal).
The state codes are classified into state classes:
• Production time
• Failure time (defined as downtime)
• Idle time (defined as downtime)
• Line restraint time
• Not scheduled
Inverter state and grid state should not have down time at same time, so when grid is down, down time is not registered on inverter. This must also be considered when changing states manually, possibly both changing inverter and grid state.
## Inverter state
State of inverters are calculated automatically based on following input signals:
• Operation mode reported by inverter
• Alarms reported by inverter
• Measures irradiation from plant pyranometer sensors
• Grid state
The following main principle will apply for calculation of the downtimes:
• During night (irradiation below 5 W/m2) no downtime is registered. (states not idle time or failure time)
• “Grid down” result in line restraint time.
• All stops on inverter not due to grid down, is “Idle” or “Failure” time resulting in downtime and reduced availability
• All manual codes are grouped as “Idle” time (resulting in downtime), but classified to make it possible to extract and group in special reports if needed
• When moving downtime from plant to grid, “Grid down” state on inverter shall be used (“line restraint” not resulting in plant downtime). At same time, “No operation” must be set on grid for same period to make sure grid availability is used.
• During night, time must be set to one of the “Not scheduled” states if manually corrected. If not, daytime availability will be wrong. Total time to calculate availability is based on states not being “Not scheduled”
## Grid state
State of grid is collected automatically based on following input:
• State of main breakers connecting substation to grid
• Active power measurement from power analysers
• Active power setpoint on PPC (curtailment state)
• Voltage and frequency measurements from power analyser
## Tracker state
State of trackers is collected automatically based on following input:
• State/mode signals from tracker control unit
• Alarm signals from tracker control unit
• Measures irradiation from plant pyranometer sensors
o Average value from incline pyranometers
States and state calculation will vary between tracker suppliers. General rules:
• Tracker is operating when following the sun
• When tracker is in a manual mode and/or in a fixed position, it is defined as idle
• When tracker reports an error, it is in failure mode.
• Night-time is defined as Not Scheduled
• Grid down is defined as Line Restraint.
• Optional states to calculate tracker out of position. Used on some plants.
o Warning as production (small deviation), error as alarm (large deviation)