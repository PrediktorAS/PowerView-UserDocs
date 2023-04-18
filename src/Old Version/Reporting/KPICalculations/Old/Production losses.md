# Production Losses

Production losses are calculated based on down time registrations.

__Inverter losses__

Following algorithm is implemented in SCADA to estimate production lost on inverters (as long as the total inverter capacity down is below [80%]):

* Production Lost Inverters = EAdj * TotalNomPowerDown / (Pnom – TotalNomPowerDown)
  * EAdj: measured energy production of the plant during the period, adjusted in necessary
  * NomPowerDown: nominal DC power of the single inverter experiencing down time
  * Pnom: total nominal DC power of plant
  * TotalNomPowerDown: total nominal DC power of all inverters experiencing down time. Sum of all NomPowerDown.

Following algorithm is implemented in SCADA to estimate production lost on inverters (when the total inverter capacity down is above [80%]):

* Production Lost Inverters = PR_reference *TotalNomPowerDown* InclineIrradiation * / Irr_STC
  * PR_reference: Calculate a reference PR Gross Prod Lost for the reference period of 30 (full) days prior to the day in which the downtime occurs (including the effects of any production lost during that reference period)
  * TotalNomPowerDown: Total nominal DC power of all inverters experiencing down time. Sum of all NomPowerDown.
  * InclineIrradiation: Incline pyranometer value. If no irradiation exists for 10 minute period, irradiation for same time previous day is used. 30 days back is checked. Average for first 5 days with measurments is used.
  * Irr_STC: Irradiance at standard test conditions. Standard 1000 W/m2

__Grid losses__

Grid downtime is classified into following classes:

* Production time
* Failure time
* Idle time
* Line restraint time
* Unscheduled

“Failure time”, “Idle time” and “Line restraint time” is counted as down time resulting in reduced plant availability and thus production lost due to down time.

Following algorithm is implemented in SCADA to estimate production lost:

* Production Lost Grid = PR_reference *Pnom* InclineIrradiation * / Irr_STC

Factors calculated as follows:

* PR_reference:
  * Calculate a reference PR Gross Prod Lost for the reference period of 30 (full) days prior to the day in which the downtime occurs (including the effects of any production lost during that reference period)
* Pnom:
  * Nominal DC power of the plant
* InclineIrradiation
  * Incline pyranometer value
  * If no irradiation exists for 10 minute period, irradiation for same time previous day is used. 30 days back is checked and 5 first day with irradiation is used.
* Irr_STC
  * Irradiance at standard test conditions
  * Standard 1000 W/m2

__Tracker losses__

* Tracker downtime loss [MWh]: Actual production in MWh*(1-Tracker availability in %)*(Transposition Factor in %-1)
  * Where Transposition Factor = Global Incline Irradiation/Global Horizontal Irradiation

__Soiling losses:__

* Actual Production / (1-Soiling rate) – Actual Production

__Curtailment losses:__

For periods with curtailment:

* Estimated production – Actual Production
