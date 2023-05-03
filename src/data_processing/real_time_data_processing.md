# Real Time Data Processing

Data processing on collected data is done using calculation platform in PowerView real time data hub <a href="https://docs.prediktor.com/docs/foundation9/APIS_Hive/APIS_Hive.html" target="_blank">APIS Hive</a>.
- Custom function item calculations
    - [Function item expressions](https://docs.prediktor.com/docs/foundation9/APIS_Hive_Modules/Shared/ItemTypes/65568.html?highlight=function#item-type-function-item) using logic and arithmetric calculations
    - Inputs are other signals (measurements and alarms) from equipment
    - Output logged in historian or used to trigger alarms 
- Standard calculations in OPC UA information model
    - Using variables and parameters from signals and alarms to calculate standard new variables and alarms
    - Example relative power measurements, performance indications and general alarms