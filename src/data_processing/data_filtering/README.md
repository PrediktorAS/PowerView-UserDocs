# Data filtering

Data is filtered in several ways on the way from sensor signal to user presentation:
- Data quality based on sensor connectivity
- Data quality based on data quality attribute from sensor
- Data validation based on valid range on signal (e.g. min/max irradiation values)
- Data validation and outlier detection when loading data in data warehouse
    - [Weather Sensor Filtering](./weather_sensor_filtering.md)
    - [Meter Data Filtering](meter_data_filtering.md)
    - [Inverter Data Filtering](inverter_data_filtering.md)
    - [String Sensor Filtering](string_monitor_data_filtering.md)