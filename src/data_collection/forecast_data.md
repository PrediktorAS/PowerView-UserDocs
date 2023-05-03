# Forecast data

Weather and production forecast data is collected from 3. party providers (like SolarGIS, Meteologica and Enercast).
These services is integrated with standards API's and data is retreived with wanted resolution and update rate and stored in PowerView databases.
Update rates down to 5 minutes can be achieved. 
Typical setup for day ahead forecasts is every day, and for intra day forecast every 15min/hour.
Typical resolution is 15 min.

Availability forecast is added manually by user in PowerView web portal in [Planned Power Reduction](../user_interfaces/forecasting/planned_power_reduction.md) screen. 

See also [Forecasting](../user_interfaces/forecasting/)