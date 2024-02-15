# Production Loss Calculations

Production losses are based on data from plants. Losses are calculated per 10 min periods and stored in the data warehouse.

## General rules
- When grid downtime losses are calculated, other losses are set to the percentage of the 10 minute period having grid down. If whole period has grid down, no other losses are calculated.
- Else when curtailment losses are calculated, other losses than clipping losses are set to the percentage of the 10 minute period having curtailment. If whole period has curtailment, no other losses are calculated.
- Else when clipping losses are calculated, other losses are set to the percentage of the 10 minute period having clipping. If whole period has clipping, no other losses are calculated.

## Adjustment Factor
For some production loss calculations, an adjustment factor is used. This is used to adjust the estimated production to the actual production. The adjustment factor is calculated based on estimated production and measured production last 10 minutes before the loss starts and first 10 minutes after loss ends and formula is:

> AdjustmentFactor = [Actual Production](../yield_and_weather/production.md) / [Estimated Production](../yield_and_weather/estimated_production.md)

The result will be clipped [0.95 , 1.05], meaning max +/- 5% adjustment

## Revenue Loss
Revenue Losses are calculated from Production Losses using the actual Energy tariff value for the period as registered in the [budget](../../../data_collection/budget_data.md).

## List of KPIs

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Production Loss | [Grid downtime production losses](grid_down_time_production_losses.md) | Production losses due to downtime on grid (reduced grid availability) |
| Production Loss | [Plant downtime production losses](plant_down_time_production_losses.md) | Production losses due to downtime on inverters (reduced plant availability) |
| Production Loss | [Tracker downtime production losses](tracker_down_time_production_losses.md) | Production losses due to non-working trackers (reduced tracker availability) |
| Production Loss | [String downtime production losses](string_down_time_production_losses.md) | Production losses due to non-available strings (reduced string availability) |
| Production Loss | [Curtailment production losses](curtailment_production_losses.md) | Production losses due to plant curtailment |
| Production Loss | [Clipping production losses](clipping_production_losses.md) | Production losses due to plant clipping |
| Production Loss | [Soiling production losses](soiling_production_losses.md) | Production losses due to panel soiling |
| Production Loss | [Snow production losses](snow_production_losses.md) | Production losses due to snow on panels. |
| Production Loss | [Manually excluded energy losses](manually_excluded_energy_losses.md) | Production losses manually registered. |
| Revenue Loss | [Grid downtime revenue loss](grid_down_time_production_losses.md) | Revenue losses due to downtime on grid  (reduced grid availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Plant downtime revenue loss](plant_down_time_production_losses.md) | Revenue losses due to downtime on inverters (reduced plant availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Tracker downtime revenue loss](tracker_down_time_production_losses.md) | Revenue losses due to non-working trackers (reduced tracker availability). Energy tariff taken from internal original budget |
| Revenue Loss | [String downtime revenue losses](string_down_time_production_losses.md) | Revenue losses due to non-available strings (reduced string availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Curtailment revenue losses](curtailment_production_losses.md) | Revenue losses due to plant clipping. Energy tariff taken from internal original budget |
| Revenue Loss | [Snow production losses](snow_production_losses.md) | Revenue losses due to snow on panels. Price taken from internal original budget |
| Revenue Loss | [Clipping revenue losses](clipping_production_losses.md) | Revenue losses due to panel soiling. Energy tariff taken from internal original budget |
| Revenue Loss | [Manually excluded energy losses](manually_excluded_energy_losses.md) | Revenue losses manually registered. Energy tariff taken from internal original budget |
