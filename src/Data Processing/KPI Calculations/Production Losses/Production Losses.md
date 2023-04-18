# Production Loss Calculations

Production losses are based on data from plants. Losses are calculated per 10 min periods and stored in the data warehouse.

General rules:
- When grid downtime losses are calculated, other losses are set to the percentage of the 10 minute period having grid down. If whole period has grid down, no other losses are calculated.
- Else when curtailment losses are calculated, other losses than clipping losses are set to the percentage of the 10 minute period having curtailment. If whole period has curtailment, no other losses are calculated.
- Else when clipping losses are calculated, other losses are set to the percentage of the 10 minute period having clipping. If whole period has clipping, no other losses are calculated.
