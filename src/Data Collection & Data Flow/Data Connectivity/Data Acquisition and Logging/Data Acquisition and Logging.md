# Data Acquisition and Logging

Data can be collected and logged from plant equipment and devices using the <a href="https://docs.prediktor.com/docs/foundation9/APIS_Hive/APIS_Hive.html" target="_blank">APIS Hive</a> data integration platform
Data can be collected in different ways:

- Collect data using [PowerView plant connector](PowerView%20Plant%20Connector/PowerView%20Plant%20Connector.md) directly from Equipment
    - PowerView plant connector PC/Server is installed on site with PowerView data collection software
    - PowerView software reads data directly from equipment (inverters, meters, etc.) store and forward to PowerView portfolio solution
- Collect data using [PowerView plant connector](PowerView%20Plant%20Connector/PowerView%20Plant%20Connector.md) through local SCADA or data hub on site
    - PowerView plant connector PC/Server is installed on site with PowerView data collection software
    - PowerView software reads data from local SCADA/data hub and store and forward to PowerView portfolio solution
- Collect data using existing data stores in cloud from [3rd-party supplier API](Third%20Party%20API's/Third%20Party%20API's.md)
    - Data is already stored in a cloud database (e.g. from Isotrol) and have access to data from 3rd-party using an API access
    - PowerView gets access to the data (authentication credentials) and documentation on API format
    - PowerView implements data read from the API and store data in PowerView portfolio solution
- Collect data from FTP file push from inverter data loggers on plant (no cloud data store)
    - Data logger (e.g. Smartlogger from Huawei) pushes periodically data files from site to PowerView portfolio server using FTP protocol
    - PowerView parses files and store data in PowerView portfolio solution

In all cases, the data is stored in PowerView databases in a well structured way:
- [Signals & Trends](../../Signals%20&%20Trends/Signals&Trends.md)
- [Alarms & Events](../../Alarms%20&%20Events/Alarms&Events.md)