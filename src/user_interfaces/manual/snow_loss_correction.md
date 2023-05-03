# Snow Loss Correction

[Snow losses](../../data_processing/kpi/production_losses/snow_production_losses.md) are automatically detected based on snow level from external weather providers.
This can be overridden by day and plant using this screen.

Input:
- Plant
- Day
- New override: 
    - No override: automatic detection used
    - Override, has snow: automatics detection overridden with snow detection. [Snow losses](../../data_processing/kpi/production_losses/snow_production_losses.md) are calculated 
    - Override, has no snow: automatics detection overridden with no snow detection. No [Snow losses](../../data_processing/kpi/production_losses/snow_production_losses.md) are calculated 
- Comment for override

Press "Store new override" to store new settings and recalculate data

Corrected data log can be seen in report "Production Change Log"