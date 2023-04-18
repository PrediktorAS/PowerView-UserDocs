# Grid down time production losses

Grid state is classified into following classes:
- Production time
- Failure time
- Idle time
- Line restraint time
- Unscheduled

“Failure time”, “Idle time” and “Line restraint time” is counted as down time resulting in reduced plant availability and thus production loss due to down time.

Following algorithm is implemented to estimate production loss:
- Production Loss Grid = EstimatedProduction * AdjustmentFactor

Factors calculated as follows:
- EstimatedProduction: 
    - Estimated production based on standard plant model (see chapter 5.1.2) and following input:
        - Nominal power of plant (for E/W for inverters with same orientation)
        - Incline Irradiation measurements (SolarGIS data if not present) 
            - (for E/W for inverters with same orientation)
        - Estimated cell temperature together with module temperature coefficient (for E/W for inverters with same orientation)
        - Module efficiency
        - Inverter efficiency
        - Loss factors (DC, inverter, plant)
- AdjustmentFactor
    - Adjustment factor is calculated based on estimated production and measured production 1 hour before grid downtime starts 
        - Adjustment factor is limited to the interval 0,7 - 1,3
        - For E/W for inverters with same orientation

For E/W installations, losses for east and west are calculated separately with incline irradiation and module temperature for each orientation and add together
