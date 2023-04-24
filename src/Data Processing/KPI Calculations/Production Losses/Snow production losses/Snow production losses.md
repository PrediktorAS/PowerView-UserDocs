# Snow production losses

Snow losses are calculated based on following algorithm:
- Snow losses are detected based on following check:
    - Snow depth > 0 for day and PR_snow<65%, means snow losses to be calculated
        - Snow depth retreived from satellite weather data provider 
        - PR_snow is PR Gross Production Loss formula using maximum irradiation value from each single incline pyranometer value as irradiation source (if no values, use external weather data)

- If snow losses are detected snow losses are calculated as:
    - Production Loss Snow = Estimated_Production_Snow - [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) - [String downtime production loss](../String%20down%20time%20production%20losses/String%20down%20time%20production%20losses.md) - [Trackers Downtime Production Loss](../Tracker%20down%20time%20production%20losses/Tracker%20down%20time%20production%20losses.md) - [Plant Downtime Production Loss](../Plant%20down%20time%20production%20losses/Plant%20down%20time%20production%20losses.md) 
    - Estimated_Production_Snow: Estimated production formula calculating [Estimated Production](../../Yield%20and%20Weather/Estimated%20Production/Estimated%20Production.md) using maximum irradiation value from each single incline pyranometer value as irradiation source
    
