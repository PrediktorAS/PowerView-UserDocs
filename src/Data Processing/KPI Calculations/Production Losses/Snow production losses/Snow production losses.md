# Snow production losses

Snow losses are calculated based on following algorithm:
- Snow losses are detected based on following check:
    - Snow depth>0 for day and PR_snow<65%, means snow losses to be calculated
        - Snow depth retreived from satellite weather data provider 
        - PR_snow is PR Gross Production Loss formula using maximum irradiation value from each signle incline pyranometer value as irradiation source (if no values, use external weather data)

- If snow losses are detected snow losses are calculated as:
    - Production Loss Snow= Estimated_Production_Snow -  E_meas - Production Loss Strings - Production Loss Trackers - Production Loss Inverter 
    - Estimated_Production_Snow: Estimated production formula calculating theoretical production using maximum irradiation value from each single incline pyranometer value as irradiation source
        - E_meas: measured plant energy production for period.  
        - Estimated losses from strings, trackers and inverters
