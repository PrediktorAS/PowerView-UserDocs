[//]: # (MBo: Fra KPI Calculations.pdf)

# Production Loss Calculations

Production loss based on grid and inverter is calculated based on data from plants and stored in separate tables in the data warehouse for easy reporting. Data is updated when inverter state or other parameters are changed manually.
General rule:

* When grid downtime losses are calculated, other losses are set to the percentage of the 10 minute period having grid down. If whole period has grid down, no other losses are calculated.
* Else when curtailment losses are calculated, other losses than clipping losses are set to the percentage of the 10 minute period having curtailment. If whole period has curtailment, no other losses are calculated.
* Else when clipping losses are calculated, other losses are set to the percentage of the 10 minute period having clipping. If whole period has clipping, no other losses are calculated.

## Grid down time production losses

Grid downtime is classified into following classes:

* Production time
* Failure time
* Idle time
* Line restraint time
* Unscheduled  

“Failure time”, “Idle time” and “Line restraint time” is counted as down time resulting in reduced plant availability and thus production loss due to down time.  

Following algorithm is implemented in SCADA to estimate production loss:

* Production Loss Grid = EstimatedProduction * AdjustmentFactor  Factors calculated as follows:
* EstimatedProduction:  
  * Estimated production based on standard plant model (see chapter 2.1.2) and following input:
    * Nominal power of plant (for E/W for inverters with same orientation)
    * Incline Irradiation measurements (SolarGIS data if not present)  
      * (for E/W for inverters with same orientation)
    * Estimated cell temperature together with module temperature coefficient (for E/W for inverters with same orientation)
    * Module efficiency ▪ Inverter efficiency
    * Loss factors (DC, inverter, plant)
  * AdjustmentFactor
    * Adjustment factor is calculated based on estimated production and measured production 1 hour before grid downtime starts  
      * Adjustment factor is limited to the interval 0,7 - 1,3
      * For E/W for inverters with same orientation  

For E/W installations, losses for east and west are calculated separately with incline irradiation and module temperature for each orientation and add together  

## Plant down time production losses

This is plant downtime in kWh.

Production loss is calculated for an inverter based on the state for the inverter at a given time (see chapter 3.1.1)

Inverter downtime is classified into following classes:

* Production time • Failure time
* Idle time
* Line restraint time
* Not scheduled

“Failure time” and “Idle time” is counted as down time resulting in reduced plant availability and thus production loss due to down time.

For each 10 min time period SCADA calculates the share of the total inverter DC capacity which is experiencing downtime (ShareNomPowerDown). As long as this share is below [80%], Alternative A should be used, while if the share of inverter capacity down is above [80%] – Alternative B should be applied (the same as applied in case of Production Loss on Grid).

* ShareNomPowerDown = TotalNomPowerDown / Pnom

Factors calculated as follows:

* Pnom: total nominal DC power of plant
* TotalNomPowerDown: total nominal DC power of all inverters experiencing down time

Production loss for one inverter is calculated dividing “Production Loss Inverters” with number of inverters down.

**Alternative A:**
Following algorithm is implemented in SCADA to estimate production loss on an inverter (as long as the total inverter capacity down is below [80%]):

* Production Loss Inverter = E_meas * NomPowerInverter / (Pnom – NomPowerInverter)

Factors calculated as follows:

* E_meas: measured energy production (see 2.1.1) of the plant during the period
  * For E/W oriented plants, energy is taken from inverters with same orientation
* NomPowerInverter: nominal DC power of the single inverter experiencing down time
* Pnom: total nominal DC power of all inverters o For E/W oriented plants, nominal power is summarized from inverters with same orientation  

**Alternative B:**

Following algorithm is implemented in SCADA to estimate production loss on inverter (when the total inverter capacity down is above [80%]):

* Production Loss Inverter = PR_reference *NomPowerInverter* InclineIrradiation * / Irr_STC  

Factors calculated as follows:

* PR_reference:  
  * Calculate a reference “PR Gross Production Loss” (see 2.4.3) for the reference period of 5 (full) days prior to the day in which the downtime occurs (including the effects of any production loss during that reference period)  
* NomPowerInverter:  
  * Nominal DC power of inverter
* InclineIrradiation
  * Incline pyranometer value for plant (see 2.1.3)
  * If no irradiation exists for 10 minute period:
    * Use irradiation for same time previous day is used. 20 days back is checked.  
  * For E/W oriented plants, use irradiation from inverter orientation.
* Irr_STC
  * Irradiance at standard test conditions
  * Standard 1000 W/m2  

## Tracker down time production losses

Following algorithm is implemented in SCADA to estimate production loss on trackers:

* Production Loss Trackers = E_meas *(1 – TA_ForProdLoss)* (TF - 1)  

Factors calculated as follows:

* E_meas: measured actual production for plant (see 2.1.1)
* TAprodloss: Tracker availability (0-1) for plant (see 2.3.3) taking into account available power on tracker for the time period. Removing power due to unavailable strings and inverters
* TF: Transposition Factor = Incline Irradiation / Horizontal Irradiation (see 2.1.5)  

## String down time production losses

String availability losses are calculated based on string availability for plant as described in chapter 2.3.4.

* Production Loss Strings = E_meas * (1-SA) / SA  

Factors calculated as follows:

* E_meas: measured actual production for plant (see 2.1.1)
* SA: String availability (0-1) for plant  

## Soiling production losses

Soiling losses are calculated as soiling index related to measured energy production:

* Soiling losses = (E_meas / (1-(SoilingIndex/100))) - E_meas
  * E_meas: measured plant energy production for period. (see 2.1.1)
  * SoilingIndex: average soiling index for plant (see 1)  

## Curtailment production losses

Curtailment losses are calculated for each 10 minute period based on registered curtailment periods. Curtailment is registered as state 6006 on grid as explained in chapter 3.1.2.
For each period, estimated production is calculated based on measured irradiation and available nominal power. The difference between estimated and measured value is defined as the losses.  

Curtailment losses = (E_est * AdjustmentFactor) - E_meas  

* E_meas:  
  * measured plant energy production for period of curtailment (see 2.1.1)
* E_est:  
  * Estimated production based on standard plant model (see 2.1.2)
  * Cut on max nominal AC power on plant. Estimated production above nominal power is classified as clipping losses
* AdjustmentFactor
  * Adjustment factor is calculated based on estimated production and measured production last 30 minutes before curtailment starts
    * AdjustmentFactor = E_meas / E_est
      * E_meas and E_est as above  

If measured power is not close to the curtailment limit, the losses are set to 0. Detection limit is 98%, meaning measured power on PPC (or PPC power analyser) must be more than 98% of PPC active power setpoint value to calculate losses.

## Clipping production losses

Clipping is detected based on detection of output power close to maximum nominal output power. Detecting is done based on measured power on PPC vs. nominal dc power on plant and a per plant adjustment limit. If measured value is above nominal and no curtailment is active, clipping is detected.

Losses are calculated for each 10 minute period the same way as for curtailment:
Clipping losses = (E_est * AdjustmentFactor) - E_meas  

* E_meas:
  * measured plant energy production for period of curtailment (see 2.1.1)
* E_est:  
  * Estimated production based on standard plant model (see 2.1.2)
* AdjustmentFactor
  * Adjustment factor is calculated based on estimated production and measured production last 30 minutes before clipping starts
    * AdjustmentFactor = E_meas / E_est
      * E_meas and E_est as above  

Clipping losses are also detected for period of curtailment, when estimated production is above nominal output on plant. The energy estimated above nominal max output is classified as clipping losses.
