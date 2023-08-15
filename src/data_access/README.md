# Accessing data - API's

PowerView has muliple access methods and API's for data access to the data sources.
Following list up the available API's.

Detailed description can be found in user guides and references:
- OPC UA DA/HA/AC
    - Real time data, historical data and alarms&events
    - All data in flat namespace and information model available. Real time and historical data.
- OPC UA Rest API
    - Rest API to access OPC UA data.
    - Same data as for OPC UA DA/HA/AC
    - In addition access to model structure and references in domain information models (like IEC 61400-25 model for wind and Solar PV information model)
- ModelIndex REST API: 
    - REST API to access model structure and references from index. Working with indexed structure rather than traversing the model allows for a drastic increase in speed.
- Python library - pyPrediktorMapClient
    - Python library to access real time and historical data in OPC UA information model. Model structure and references in the domain information models can be used to get asset structure, and then combined with APIs to extract relevant variables and parameters for the assets. 
- SQL Interface: 
    - Data collected in the [Data Warehouse](data_sources/data_warehouse.md) can be accessed through SQL
- Grafana Plug-in	
    - Grafana OPC UA plug-in for accessing data from the UA information model and historian and make dashboards.


