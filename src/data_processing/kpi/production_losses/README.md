# Production Loss Calculations

Production losses are based on data from plants. Losses are calculated per 10 min periods and stored in the data warehouse.

General rules:
- When grid downtime losses are calculated, other losses are set to the percentage of the 10 minute period having grid down. If whole period has grid down, no other losses are calculated.
- Else when curtailment losses are calculated, other losses than clipping losses are set to the percentage of the 10 minute period having curtailment. If whole period has curtailment, no other losses are calculated.
- Else when clipping losses are calculated, other losses are set to the percentage of the 10 minute period having clipping. If whole period has clipping, no other losses are calculated.

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Production Loss | [Grid down time production losses](grid_down_time_production_losses.md) | Production losses due to down time on grid (reduced grid availability) |
| Production Loss | [Plant down time production losses](plant_down_time_production_losses.md) | Production losses due to down time on inverters (reduced plant availability) |
| Production Loss | [Tracker down time production losses](tracker_down_time_production_losses.md) | Production losses due to non-working trackers (reduced tracker availability) |
| Production Loss | [String down time production losses](string_down_time_production_losses.md) | Production losses due to non-available strings (reduced string availability) |
| Production Loss | [Curtailment production losses](curtailment_production_losses.md) | Production losses due to plant curtailment |
| Production Loss | [Clipping production losses](clipping_production_losses.md) | Production losses due to plant clipping |
| Production Loss | [Soiling production losses](soiling_production_losses.md) | Production losses due to panel soiling |
| Production Loss | [Snow production losses](snow_production_losses.md) | Production losses due to snow on panels. |
| Revenue Loss | [Grid down time revenue loss](grid_down_time_production_losses.md) | Revenue losses due to down time on grid  (reduced grid availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Plant down time revenue loss](plant_down_time_production_losses.md) | Revenue losses due to down time on inverters (reduced plant availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Tracker down time revenue loss](tracker_down_time_production_losses.md) | Revenue losses due to non-working trackers (reduced tracker availability). Energy tariff taken from internal original budget |
| Revenue Loss | [String down time revenue losses](string_down_time_production_losses.md) | Revenue losses due to non-available strings (reduced string availability). Energy tariff taken from internal original budget |
| Revenue Loss | [Curtailment revenue losses](curtailment_production_losses.md) | Revenue losses due to plant clipping. Energy tariff taken from internal original budget |
| Revenue Loss | [Snow production losses](snow_production_losses.md) | Revenue losses due to snow on panels. Price taken from internal original budget |
| Revenue Loss | [Clipping revenue losses](clipping_production_losses.md) | Revenue losses due to panel soiling. Energy tariff taken from internal original budget |
