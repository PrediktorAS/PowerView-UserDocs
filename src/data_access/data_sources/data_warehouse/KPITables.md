# KPI Tables

## KPI_Definition

Schema name: ext

Description: KPI dimension table having definitions for the KPI values aggregated and loaded in KPI_Values (YieldForecast, YieldMeasure, etc.)


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_DefinitionID|int(4)|||
|KPI_DefinitionName|nvarchar(128)|||
|Description|nvarchar(510)|||
|EngUnit|nvarchar(40)|||
|NumDecimals|int(4)|||
|IsBudget|bit(1)|||
|IsProduction|bit(1)|||
|TypeCode|int(4)|X||
|ReportOrder|int(4)|X||


## KPI_PeriodType

Schema name: ext

Description: KPI dimension table having definitions for the time period types aggregated in KPI_Values (hour, day, week, etc.)


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_PeriodTypeID|int(4)|||
|PeriodTypeName|nvarchar(128)|||
|Description|nvarchar(510)|||


## KPI_Plant

Schema name: ext

Description: KPI dimension table having definitions for the facility/plants aggregated in KPI_Values. Linked to DimFacility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_PlantID|int(4)|||
|FacilityKey|int(4)|||
|PlantName|nvarchar(510)|||
|Entity|nvarchar(510)|||
|Continent|nvarchar(510)|||
|Country|nvarchar(510)|||
|Coordinates|nvarchar(510)|X||
|FinancialCloseDate|date(3)|X||
|ConstructionStartDate|date(3)|X||
|CommercialOperationDate|date(3)|X||
|NumberOfInstalledModules|int(4)|X||
|TypeOfTrackers|nvarchar(510)|X||
|NumberOfInverters|int(4)|X||
|ContactPerson|nvarchar(510)|X||
|DrivingInstructions|nvarchar(max)|X||
|NominalDCCapacity|float(8)|X||
|NominalACGridCapacity|float(8)|X||
|PlantDescription|nvarchar(510)|X||
|ConstructionFinishDate|datetime(8)|X||
|GridConnectionVoltage|float(8)|X||
|Location|nvarchar(510)|X||
|AreaUnderPanels|float(8)|X||
|TypeOfInverters|nvarchar(510)|X||
|TypeOfModules|nvarchar(510)|X||
|TimeZoneID|nvarchar(510)|X||
|NominalHouseholdCapacity|float(8)|X||
|AnnualYieldEstimate|float(8)|X||
|Enabled|bit(1)|X||


## KPI_SubPlant

Schema name: ext

Description: KPI dimension table having definitions for the subfacility/subplants aggregated in KPI_Values_SubPlant. Linked to DimSubFacility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_SubPlantID|int(4)|||
|SubFacilityKey|int(4)|||
|PlantName|nvarchar(510)|||
|SubPlantName|nvarchar(510)|||
|Entity|nvarchar(510)|||
|Continent|nvarchar(510)|||
|Country|nvarchar(510)|||
|Coordinates|nvarchar(510)|X||
|FinancialCloseDate|date(3)|X||
|ConstructionStartDate|date(3)|X||
|CommercialOperationDate|date(3)|X||
|TypeOfTrackers|nvarchar(510)|X||
|ContactPerson|nvarchar(510)|X||
|DrivingInstructions|nvarchar(max)|X||
|NominalDCCapacity|float(8)|X||
|NominalACGridCapacity|float(8)|X||
|PlantDescription|nvarchar(510)|X||
|ConstructionFinishDate|datetime(8)|X||
|GridConnectionVoltage|float(8)|X||
|Location|nvarchar(510)|X||
|TypeOfInverters|nvarchar(510)|X||
|TypeOfModules|nvarchar(510)|X||
|TimeZoneID|nvarchar(510)|X||
|Enabled|bit(1)|X||


## KPI_Values

Schema name: ext

Description: KPI values aggeragted on the time, plant and kpi-definition dimensions


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_DefinitionID|int(4)|||
|KPI_PlantID|int(4)|X||
|KPI_PeriodTypeID|int(4)|||
|Value|float(8)|X||
|Target|float(8)|X||
|StartTime|datetime(8)|X||
|EndTime|datetime(8)|X||
|ValueToDate|float(8)|X||
|KPI_ValueID|bigint(8)|||


## KPI_Values_SubPlant

Schema name: ext

Description: KPI values aggeragted on the time, subplant and kpi-definition dimensions


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|KPI_DefinitionID|int(4)|||
|KPI_SubPlantID|int(4)|X||
|KPI_PeriodTypeID|int(4)|||
|Value|float(8)|X||
|Target|float(8)|X||
|StartTime|datetime(8)|X||
|EndTime|datetime(8)|X||
|ValueToDate|float(8)|X||
|KPI_ValueID|bigint(8)|||


