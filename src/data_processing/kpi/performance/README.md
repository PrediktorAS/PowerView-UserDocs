# Performance Calculations

### Performance Ratio (PR)
Performance Ratio is the ratio of measured/actual output to expected output for a given reporting period and is probably the most important measure of the efficiency of a solar power plant. 

### KPI Reports
Performance KPI's includes different performance Ratio (PR) calculations on plant and inverter level together with energy performance index.

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Performance | [PR Net](pr_net.md) | PR basic calculation. It is only looking at irradiance and production and __*does not adjust*__ for the module degradation in the nominal power |
| Performance | [PR Contractual](pr_contractual.md) | PR from contract for a given plant |
| Performance | [PR Gross](pr_gross.md) | Uses PR net as basis, we divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced  |
| Performance | [PR Gross Production Loss](pr_gross_production_loss.md) | Uses PR net as basis, but production is using measured production + estimated production  |losses due to Plant and Grid downtime. |
| Performance | [PR Net Temp Adjusted](pr_temperature_adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Net” |
| Performance | [PR Gross Temp Adjusted](pr_temperature_adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross” |
| Performance | [PR Gross Production Loss Temp Adjusted](pr_temperature_adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross Production Loss” |
| Performance | [Energy Performance Index](energy_performance_index.md) | Performance of production vs. irradiation, related to budget and actual |
