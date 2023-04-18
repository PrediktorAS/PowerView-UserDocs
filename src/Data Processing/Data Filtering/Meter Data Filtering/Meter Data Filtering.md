# Meter data filtering

Obviously wrong active energy meter readings are filtered out and not added to data warehouse database using following algorithm:

- Calculate max possible production from last 10-minute period production was more than 0
    - Use nominal AC power for plant and time since last energy registration on meter
- Add 50 % as safety margin
- If above this limit, reject value.

## Meter data filtering reporting 
Weekly mail can sent to stakeholder, summarizing rejected meter values.
