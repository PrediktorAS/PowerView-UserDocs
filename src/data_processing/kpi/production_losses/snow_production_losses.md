# Snow production losses

Snow losses are calculated based on following algorithm:
- Snow losses are detected based on following check:
    - Snow depth > 0 for day and PR_snow<65%, means snow losses to be calculated
        - Snow depth retreived from satellite weather data provider 
        - PR_snow is PR Gross Production Loss formula using maximum irradiation value from each single incline pyranometer value as irradiation source (if no values, use external weather data)

- If snow losses are detected snow losses are calculated as:
    - Production Loss Snow = Estimated_Production_Snow - [Actual Production](../yield_and_weather/actual_production.md) - [String downtime production loss](string_down_time_production_losses.md) - [Trackers Downtime Production Loss](tracker_down_time_production_losses) - [Plant Downtime Production Loss](plant_down_time_production_losses) 
    - Estimated_Production_Snow: Estimated production formula calculating [Estimated Production](../yield_and_weather/estimated_production.md) using maximum irradiation value from each single incline pyranometer value as irradiation source
    
