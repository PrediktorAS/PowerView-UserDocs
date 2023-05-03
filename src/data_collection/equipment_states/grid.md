# Grid states

State of grid is collected automatically based on following input:
- State of main breakers connecting substation to grid
- Active power measurement from power analysers
- Active power setpoint on PPC (curtailment state)
- Voltage and frequency measurements from power analyser

Standard state codes shown below:

|StateType|StateCode|StateName|StateClass|
|------------|---------|---------|---------|
|Grid|	6000	|Full Operation	|Production time|
|Grid|	6001	|Partly Operation	|Production time|
|Grid|	6002	|Operation, no power	|Production time|
|Grid|	6003	|Failure on grid frequency	|Failure time|
|Grid|	6004	|No Operation	|Idle time|
|Grid|	6005	|Failure on grid voltage	|Failure time|
|Grid|	6006	|Operation, power curtailment	|Production time|
|Grid|	6010	|Preventive Maintenance	|Unscheduled|
|Grid|	6011	|Corrective Maintenance	|Failure time|
|Grid|	6012	|Downtime due to utility	|Line restraint time|
|Grid|	6013	|Downtime due to Force Majeure	|Line restraint time|
|Grid|	6500	|No power production	|Unscheduled|
|Grid|	16500	|No power production, grid down	|Unscheduled|

