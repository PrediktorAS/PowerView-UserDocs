# Plant down time production losses

This is plant downtime in kWh.
Production loss is calculated for an inverter based on the state for the inverter at a given time.

Inverter states is classified into following [Equipment States](../../../data_collection/equipment_states/) classes:
- Production time
- Failure time
- Idle time
- Line restraint time
- Not scheduled

“Failure time” and “Idle time” is counted as down time resulting in reduced plant availability and thus production loss due to down time.
For each 10 min time period SCADA calculates the share of the total inverter DC capacity which is experiencing downtime (ShareNomPowerDown). As long as this share is below [80%], Alternative A should be used, while if the share of inverter capacity down is above [80%] – Alternative B should be applied (the same as applied in case of Production Loss on Grid).

- ShareNomPowerDown = TotalNomPowerDown / Pnom
    - Pnom: total nominal DC power of plant
    - TotalNomPowerDown: total nominal DC power of all inverters experiencing down time

Production loss for one inverter is calculated dividing “Production Loss Inverters” with number of inverters down.

## Alternative A:

Following algorithm is implemented in SCADA to estimate production loss on an inverter (as long as the total inverter capacity down is below [80%]):
- Production Loss Inverter = E_meas * NomPowerInverter / (Pnom – NomPowerInverter)

Factors calculated as follows:
- E_meas: measured energy production of the plant during the period
    - For E/W oriented plants, energy is taken from inverters with same orientation
- NomPowerInverter: nominal DC power of the single inverter experiencing down time
- Pnom: total nominal DC power of all inverters
    - For E/W oriented plants, nominal power is summarized from inverters with same orientation

## Alternative B:

Following algorithm is implemented in SCADA to estimate production loss on inverter (when the total inverter capacity down is above [80%]):
- Production Loss Inverter = PR_reference * NomPowerInverter * InclineIrradiation * / Irr_STC	

Factors calculated as follows:
- PR_reference: 
    -Calculate a reference “PR Gross Production Loss” or the reference period of 5 (full) days prior to the day in which the downtime occurs (including the effects of any production loss during that reference period) 
- NomPowerInverter: 
    - Nominal DC power of inverter
- [Incline Irradiation](../yield_and_weather/incline_irradiation.md)
    - Incline pyranometer value for plant
    - If no irradiation exists for 10 minute period:
        - Use irradiation for same time previous day is used. 20 days back is checked. 
    - For E/W oriented plants, use irradiation from inverter orientation.
- Irr_STC
    - Irradiance at standard test conditions
    - Standard 1000 W/m2
