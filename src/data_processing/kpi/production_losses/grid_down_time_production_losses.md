# Production Losses due to Grid downtime

As explained in [Equipment States](../../../data_collection/equipment_states/) grid state is classified into the following classes, where only the middle three are considered as grid downtime and thus production loss:
- Production time
- __Failure time__
- __Idle time__
- __Line restraint time__
- Unscheduled

## Formula
> Grid downtime production loss = [Estimated Production](../yield_and_weather/estimated_production.md) * [AdjustmentFactor](./#adjustment-factor)

## East/West installations
For E/W installations, losses for east and west are calculated separately with incline irradiation and module temperature for each orientation and add together
