# KPI Tables

## KPI_Definition

Schema name: ext

Description: KPI dimension table having definitions for the KPI values aggregated and loaded in KPI_Values (YieldForecast, YieldMeasure, etc.)


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_DefinitionID|int(4)||Primary key ID column|
|KPI_DefinitionName|nvarchar(128)||Name of KPI|
|Description|nvarchar(510)||Description of KPI|
|EngUnit|nvarchar(40)||Engineering unit of KPI value|
|NumDecimals|int(4)||Number of decimals to use for KPI value rendring|
|IsBudget|bit(1)||If KPI is a budget value|
|IsProduction|bit(1)||If KPI is a production measure value|
|TypeCode|int(4)|X|TypeCode to use for KPI calculation algorithm|
|ReportOrder|int(4)|X|Order to report in KPI report|


## KPI_PeriodType

Schema name: ext

Description: KPI dimension table having definitions for the time period types aggregated in KPI_Values (hour, day, week, etc.)


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_PeriodTypeID|int(4)||Primary key ID column|
|PeriodTypeName|nvarchar(128)||Name of period type|
|Description|nvarchar(510)||Description of period type|


## KPI_Plant

Schema name: ext

Description: KPI dimension table having definitions for the facility/plants aggregated in KPI_Values. Linked to DimFacility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_PlantID|int(4)||Primary key ID column|
|FacilityKey|int(4)||Facility key in DimFacility|
|PlantName|nvarchar(510)||Name of plant (same as FacilityName in DimFacility)|
|Entity|nvarchar(510)||Entity of facility, e.g. Asset owner company name|
|Continent|nvarchar(510)||Continent location|
|Country|nvarchar(510)||Country location|
|Coordinates|nvarchar(510)|X||
|FinancialCloseDate|date(3)|X|Financial close date of plant project|
|ConstructionStartDate|date(3)|X|Start date of plant construction|
|CommercialOperationDate|date(3)|X|Commercial operation start date of plant|
|NumberOfInstalledModules|int(4)|X|Number of installed PV modules in plant|
|TypeOfTrackers|nvarchar(510)|X|Type of tracker if in use|
|NumberOfInverters|int(4)|X|Number of inverters in plant|
|ContactPerson|nvarchar(510)|X|Contant person name|
|DrivingInstructions|nvarchar(max)|X|Driving instructions to plant|
|NominalDCCapacity|float(8)|X|Nominal DC capacity of plant (Wp)|
|NominalACGridCapacity|float(8)|X|Nominal AC capacity of plant (W)|
|PlantDescription|nvarchar(510)|X|Description of plant|
|ConstructionFinishDate|datetime(8)|X|End date of plant construction|
|GridConnectionVoltage|float(8)|X|Voltage at point of connection (V)|
|Location|nvarchar(510)|X|Textual description of location|
|AreaUnderPanels|float(8)|X|Area under pv panels (m2)|
|TypeOfInverters|nvarchar(510)|X|Type of inverters used for plant (main type)|
|TypeOfModules|nvarchar(510)|X|Type of PV modules used for plant (main type)|
|TimeZoneID|nvarchar(510)|X|Time zone ID for plant location, can be used to convert UTC to local time|
|NominalHouseholdCapacity|float(8)|X|Number of households supported by plant production|
|AnnualYieldEstimate|float(8)|X|Annual yield estimated production (MWh)|
|Enabled|bit(1)|X|If plant is enabled for data extraction and reporting|


## KPI_SubPlant

Schema name: ext

Description: KPI dimension table having definitions for the subfacility/subplants aggregated in KPI_Values_SubPlant. Linked to DimSubFacility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_SubPlantID|int(4)||Primary key ID column|
|SubFacilityKey|int(4)||Sub-facility key in DimSubFacility|
|PlantName|nvarchar(510)||Name of plant (same as FacilityName in DimFacility)|
|SubPlantName|nvarchar(510)||Name of subplant (same as SubFacilityName in DimSubFacility)|
|Entity|nvarchar(510)||Entity of facility, e.g. Asset owner company name|
|Continent|nvarchar(510)||Continent location|
|Country|nvarchar(510)||Country location|
|Coordinates|nvarchar(510)|X||
|FinancialCloseDate|date(3)|X|Financial close date of plant project|
|ConstructionStartDate|date(3)|X|Start date of plant construction|
|CommercialOperationDate|date(3)|X|Commercial operation start date of plant|
|TypeOfTrackers|nvarchar(510)|X|Type of tracker if in use|
|ContactPerson|nvarchar(510)|X|Contant person name|
|DrivingInstructions|nvarchar(max)|X|Driving instructions to plant|
|NominalDCCapacity|float(8)|X|Nominal DC capacity of subplant (Wp)|
|NominalACGridCapacity|float(8)|X|Nominal AC capacity of subplant (W)|
|PlantDescription|nvarchar(510)|X|Description of plant|
|ConstructionFinishDate|datetime(8)|X|End date of plant construction|
|GridConnectionVoltage|float(8)|X|Voltage at point of connection (V)|
|Location|nvarchar(510)|X|Textual description of location|
|TypeOfInverters|nvarchar(510)|X|Type of inverters used for plant (main type)|
|TypeOfModules|nvarchar(510)|X|Type of PV modules used for plant (main type)|
|TimeZoneID|nvarchar(510)|X|Time zone ID for plant location, can be used to convert UTC to local time|
|Enabled|bit(1)|X|If plant is enabled for data extraction and reporting|


## KPI_Values

Schema name: ext

Description: KPI values aggeragted on the time, plant and kpi-definition dimensions


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_DefinitionID|int(4)||KPI Definition ID linked to ext.KPI_Definition|
|KPI_PlantID|int(4)|X|KPI Plant ID linked to ext.KPI_Plant|
|KPI_PeriodTypeID|int(4)||KPI Periode Type ID linked to ext.KPI_PeriodType|
|Value|float(8)|X|Calculated value of KPI for period|
|Target|float(8)|X|Target value of KPI for period|
|StartTime|datetime(8)|X|Start time for KPI value record (local time)|
|EndTime|datetime(8)|X|End time for KPI value record (local time)|
|ValueToDate|float(8)|X|Value up to end time|
|KPI_ValueID|bigint(8)||Primary key ID column|


## KPI_Values_SubPlant

Schema name: ext

Description: KPI values aggeragted on the time, subplant and kpi-definition dimensions


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_DefinitionID|int(4)||KPI Definition ID linked to ext.KPI_Definition|
|KPI_SubPlantID|int(4)|X|KPI Sub Plant ID linked to ext.KPI_SubPlant|
|KPI_PeriodTypeID|int(4)||KPI Periode Type ID linked to ext.KPI_PeriodType|
|Value|float(8)|X|Calculated value of KPI for period|
|Target|float(8)|X|Target value of KPI for period|
|StartTime|datetime(8)|X|Start time for KPI value record (local time)|
|EndTime|datetime(8)|X|End time for KPI value record (local time)|
|ValueToDate|float(8)|X|Value up to end time|
|KPI_ValueID|bigint(8)||Primary key ID column|


