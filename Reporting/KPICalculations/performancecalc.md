[//]: # (MBo: Fra KPI Calculations.pdf)

# Performance Calculations

## PR Net

This is the PR basic calculation only considering production and irradiation.  
This formula is only taking into account irradiance and production measurements. It does not take into account the module degradation in the nominal power.  

PR net = E_Meas * Is / Pnom / Iacc

* E_Meas: Measured energy production, manually adjusted if necessary (see 2.1.1)
* Is: Irradiation at standard test conditions, constant 1000 W/m2
* Pnom: nominal DC power of plant. Sum of installed modules.
* Iacc: accumulated incline irradiation in kWh/m2. (See 2.1.3)

## PR Gross

This formula uses PR net as basis. It divides by availability to get a PR only for time when park has produced.  

PR Gross = PR Net / PAd / GAdg

* PR Net: performance ratio net (see 2.4.1)
* PAd: Plant availability daylight (see chapter 2.3.1)
* GAdg: Grid availability daylight gross (see chapter 2.3.2)

## PR Gross Production Loss

Uses PR net as basis, but production is using measured production + production losses due to downtime.

PR Gross Prod Loss = E_Meas_Loss * Is / Pnom / Iacc

* E_Meas_Loss: Measured energy production, manually adjusted if necessary + production loss due to inverters and grid downtime
  * E_Meas_Loss = E_Meas + Production Loss Inverters + Production Loss Grid
    * E_Meas: measured production, see 2.1.1  
    * Production Loss Inverters: see 2.2.2
    * Production Loss Grid: see 2.2.1
* Is: Irradiance at standard test conditions, constant 1000 W/m2
* Pnom: nominal DC power of plant
* Iacc: accumulated irradiation in the module plan, see 2.1.3
  * If data missing, irradiation for same time previous day is used. 30 days back is checked and 5 first day with irradiation is used

## PR Net Temp Adjusted

Temp adjusted PR is calculated as shown below:
PR Net Temp Adjusted = PR Net / (1 - Ptpv)  

* PR Net: see 2.4.1
* Ptpv: Thermal losses factor of Module
  * Ptpv = (Tmda - Tmdb) * ɣ / 100
    * Tmda: Module temperature daylight measured. Average measured module temperature weighted with incline irradiation measured (10 minute intervals) when irradiation is above 5 W/m2
    * Tmdb: Module temperature daylight budget number. Average number for period. Budget value, originally from PVsyst
    * ɣ:  Power temperature coefficient of the Module, as supplied by the Module producer (%/°C)

## PR Gross Temp Adjusted

Temp adjusted PR is calculated as shown below:
PR Gross Temp Adjusted = PR Gross / (1 - Ptpv)  

* PR Gross: see 2.4.2
* Ptpv: See definition in 2.4.4, PR Net Temp Adjusted

## PR Gross Production Loss Temp Adjusted

Temp adjusted PR is calculated as shown below:
PR Gross Production Loss Temp Adjusted = PR Gross Production Loss / (1-Ptpv)  

* PR Gross Production Loss: see 2.4.3
* Ptpv: See definition in 2.4.4, PR Net Temp Adjusted

## PR Contractual

Adjusted per customer / PPA.

## Energy Performance Index

Energy Performance Index (EPI) is calculated as the relation between the production actual vs. budget and the irradiation actual vs budget.
The actual formula is:
EPI = 100 * (100 + (Actual Production - Budget Production ) / Budget Production )) / (100 + (Actual Irradiation- Budget Irradiation) / Budget Irradiation)

* Actual Production: see 2.1.1
* Budget Production: see 2.1.8
* Actual Irradiation: see 2.1.3
* Budget Irradiation: see 2.1.9

## Inverter PR

This is the PR basic calculation only considering production and irradiation.
 Inverter PR = E_Meas_Inverter * Is / Pnom_Inverter / Iacc

* E_Meas: Measured energy productionon inverter taken from inveter energy meter on AC side
* Is: Irradiation at standard test conditions, constant 1000 W/m2
* Pnom: nominal DC power of inverter. Sum of installed modules on inverter.
* Iacc: accumulated incline irradiation in kWh/m2 for plant. (See 2.1.3)
