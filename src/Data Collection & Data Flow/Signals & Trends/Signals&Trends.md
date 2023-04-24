# Signals & trends

Measured and calculated signals are stored in <a href="https://docs.prediktor.com/docs/foundation9/APIS_HoneyStore/APIS_HoneyStore.html" target="_blank">APIS Honeystore</a> time series database.
This is a high performance time series database with standard data access methods (API's) including OPC HA and Rest API's.
Data can be sampled with different sampling rate and resolution.
Typical setup is:
- Average 1 minute data stored for 20 years
- Data averaged based on 1-10 sec data from data source (based on possible sampling source from equipment)

Both resolution and data storage length can be configured based on customer requirements.