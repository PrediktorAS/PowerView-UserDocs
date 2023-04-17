# Grid availability

Grid availability is calculated in three ways:
1.	Grid availability daylight (GAd) = (Sum daylight time - Sum downtime grid at daylight) / Sum daylight time
2.	Grid availability full day (GAt) = (Sum time full day - Sum downtime grid full day) / Sum time full day
3.	Grid availability production loss = (E_meas_gross – Production Loss Grid) / E_meas_gross

Definition of factors:
-	Sum daylight time:
    - Calculated based on all states not having class “Not scheduled” (E.g. “No power production”)
-	Sum downtime grid at daylight
    - Total down time 
    - Down time is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint”
-	Sum time full day
    - Total time for period
-	Sum downtime grid full day 
    - Total down time 24/7 
    - Down time full day is calculated as sum of periods when grid state is in state classes “Idle time”, “Failure time” or “Line restraint” or when state code>10000 (e.g. No power production, grid down)
-	E_meas_gross = [Actual production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) + [Grid Downtime Production Losses](../../Production%20Losses/Grid%20down%20time%20production%20losses/Grid%20down%20time%20production%20losses.md) + [Plant Downtime Production Losses](../../Production%20Losses/Plant%20down%20time%20production%20losses/Plant%20down%20time%20production%20losses.md) + [Curtailment Production Losses](../../Production%20Losses/Curtailment%20production%20losses/Curtailment%20production%20losses.md)

For PR Gross calculation, a special formula is used: “Grid availability daylight gross” (GAdg)

When grid is down, it might be that there is no irradiation measurement present. This will result in grid down time is already counted for in PR by having a reduced accumulated irradiation value for day and thus a higher PR. For the PR Gross, down time and daylight time is therefore only counted when there exist incline irradiation data and when this is above 5 W/m2 (this is taken from 10 minute average values in data warehouse).

For state definitions, see [states](../../../../Data%20Collection%20&%20Data%20Flow/Equipment%20States/Equipment%20States.md)