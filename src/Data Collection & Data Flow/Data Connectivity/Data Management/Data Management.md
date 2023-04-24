# Data management

Data management is data filtering, processing and logging the collected data.
Raw data is logged in databases for time series (historian) and alarms&events. 

Data is logged with data quality, filtering out bad signals before used in further processing and data analyses

The data is then structured using an information model implemented using the OPC UA information standard as shown in image below:
- Standard PV information model that puts operational data in context
- Data, parameters and structure for all plants in same semantics context
- Implemented with OPC UA for standard an open access from client tools
- Parameters in model describes plants and equipment, like location, nominal values etc. 
- Variabels is raw signals and [processed signals](../Data%20Processing/Data%20Processing.md)
- Data from information model can be accessed as real time data or historical data in PowerView [user screens](../../../User%20Interfaces/User%20Interfaces.md) or through [standard API's](../../../Accessing%20Data%20%E2%80%93%20API%E2%80%99s/Accessing%20Data%20%E2%80%93%20API%E2%80%99s.md)

![Solar PV information model ](../../../Images/SolarPVInformationModel.png)