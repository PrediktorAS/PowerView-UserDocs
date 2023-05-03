# Production Correction Factor

Production correction factor makes it possible to enter data to calculate a factor from 0 to 1 for each plant and day.

The factor is used to calculate "other losses" in the formula for contractual PR calculation, see [Performance ratio calculation](../../data_processing/kpi/performance/pr_contractual.md).

User selects plant and month and data for each day is presented in a table and can be changed by the user.

Data entered by user is:
- Num inverters down: an average number of inverters with downtime. Can be a decimal number
- Num trackers down: an average number of trackers with downtime. Can be a decimal number
- Comment: a textual comment for the downtime

Other data shown:
- Incline Irradiation (Wh/m2):   measured plant irradiation
- Horizontal Irradiation (Wh/m2): measured horizontal irradiation
- TF: calculated transposition factor
- Irradiation Inverter Losses (Wh/m2): calculated irradiation losses due to inverters down
- Irradiation Tracker Losses (Wh/m2): calculated irradiation losses due to trackers down
- Correction Factor Kd: calculated production adjustment factor (0-1) 

Calculations:
- Irradiation Inverter Losses:
    - Incline Irradiation * Num inverters down / Total inverters
- Irradiation Tracker Losses:
    - (TF - 1) * Incline Irradiation * Num trackers down / Total trackers
    - If TF<1, value is set to 0
- Correction Factor Kd:
    - 1 - (Irradiation Inverter Losses + Irradiation Tracker Losses) / Incline Irradiation