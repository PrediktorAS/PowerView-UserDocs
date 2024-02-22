# Meter data filtering

Obviously wrong energy meter readings are filtered out and not added to data warehouse database using following general algorithm.

- Calculate max possible active energy production for period based on nominal AC power for plant:
    - MaxEnergy (kWh) = ACNominalPower * MinuteInPeriod / 60
        - ACNominalPower: nominal max AC output for plant

- Set values to NULL for period for meter values if:
    - FeedInPower_kW: rejected if > 1,5 * ACNominalPower
    - FeedInEnergy_kWh: rejected if > 1,5 * MaxEnergy
    - FeedInReactivePower_kVAr: rejected if > 1,5 * ACNominalPower
    - FeedInReactiveEnergy_kVArh: rejected if > MaxEnergy	
    - ConsumptionPower_kW: rejected if > 1,5 * ACNominalPower
    - ConsumptionEnergy_kWh: rejected if > MaxEnergy	
    - ConsumptionReactivePower_kVAr: rejected if > 1,5 * ACNominalPower	
    - ConsumptionReactiveEnergy_kVArh: rejected if > MaxEnergy	

## Meter data filtering reporting 
Weekly mail can sent to stakeholder, summarizing rejected meter values.
