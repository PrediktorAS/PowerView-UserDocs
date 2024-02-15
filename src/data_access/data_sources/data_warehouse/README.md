# PowerView Data Warehouse

PowerView data warehouse is a star-shaped relational database structure implemented in Microsoft SQL server. 
Database contains aggreagted and augmented data from multiple data sources in the PowerView solution, being the main data source for [paginated reports](../../../user_interfaces/reports_and_dashboards/paginated_reports.md) and [dashboards](../../../user_interfaces/reports_and_dashboards/dashboards.md), as well as several other applications. 

Data is extracted and filled with data from multiple data sources:
- Plant and equipment parameters from plant setup
- Time series data from plant loggers
- Forecast data from external services/API's
- Satellite weather data from external services/API's
- Manual entered or uploaded budget data
- Manual corrected data
- Operator logs and comments 
- [Equipment state](../../../data_collection/equipment_states) data from event databases
- Calculated [KPI's](../../../data_processing/kpi) 



