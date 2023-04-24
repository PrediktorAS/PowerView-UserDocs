# Performance Calculations

Performance KPI's invcludes different performance Ratio (PR) calculations on plant and inverter level together with energy performance index.

| KPI Type | KPI name | KPI description |
|---------|---------|---------|
| Performance | [PR Contractual](Performance/PR%20Contractual/PR%20Contractual.md) | PR from contract for a given plant |
| Performance | [PR Net](Performance/PR%20Net/PR%20Net.md) | PR basic calculation. Only looking at irradiance and production. Does not adjust for the module degradation in the nominal power. |
| Performance | [PR Gross](Performance/PR%20Gross/PR%20Gross.md) | Uses PR net as basis. Divide by the Plant and Grid Availabilities Daylight to get a rough PR estimate representative for time when park has produced  |
| Performance | [PR Gross Production Loss](Performance/PR%20Gross%20Production%20Loss/PR%20Gross%20Production%20Loss.md) | Uses PR net as basis, but production is using measured production + estimated production  |losses due to Plant and Grid downtime. |
| Performance | [PR Net Temp Adjusted](Performance/PR%20Net%20Temp%20Adjusted/PR%20Net%20Temp%20Adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Net” |
| Performance | [PR Gross Temp Adjusted](Performance/PR%20Gross%20Temp%20Adjusted/PR%20Gross%20Temp%20Adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross” |
| Performance | [PR Gross Production Loss Temp Adjusted](Performance/PR%20Gross%20Production%20Loss%20Temp%20Adjusted/PR%20Gross%20Production%20Loss%20Temp%20Adjusted.md) | Temperature adjusted PR calculation. Basis is “PR Gross Production Loss” |
| Performance | [Energy Performance Index](Performance/Energy%20Performance%20Index/Energy%20Performance%20Index.md) | Performance of production vs. irradiation, related to budget and actual |
