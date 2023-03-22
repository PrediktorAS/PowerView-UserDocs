# Inverter data filtering

Obviously wrong inverter energy readings are filtered out and not added to data warehouse database using following algorithm:

- Calculate max possible production from last 10-minute period production was more than 0
    - Use nominal AC power for inverter and time since last energy registration on meter
- Add 50 % as safety margin
- If above this limit, reject value.
- Remove energy values < 0
