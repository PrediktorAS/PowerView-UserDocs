# Dim Tables

## DimDateAndHour

Schema name: dbo

Description: Dimension table having time dimension on hour resolution. Used by fact tables together with minute.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|DateAndHourKey|int(4)||Auto increment key|
|StartTime|datetime(8)||Start time, local time|
|EndTime|datetime(8)||End time, local time|
|Date|date(3)||Date, local time|
|Hour|int(4)||Hour of day, local time|
|WeekNo|int(4)||Week number, local time|
|MonthNo|int(4)||Month number, local time|
|MonthName|nvarchar(128)||Month name, local time|
|MonthNameShort|nvarchar(6)||Month name short, local time|
|Quarter|nvarchar(128)||Quarter, local time|
|Year|int(4)||Year, local time|
|ShiftName|nvarchar(128)||Shift name|
|YearWeek|nvarchar(128)||Year of week, local time|
|YearMonth|nvarchar(128)||Year of month, local time|
|DateShift|nvarchar(128)||Date of shift, local time|
|Day|nvarchar(128)||Day number, local time|
|UTCStartTime|datetime(8)||UTC Start Time|
|UTCEndTime|datetime(8)||UTC End Time|
|UTCYear|int(4)||UTC Year Number|
|UTCQuarter|int(4)||UTC Quarter Number|
|UTCMonth|int(4)||UTC Month Number|
|UTCDayInMonth|int(4)||UTC Day in Month|
|UTCHourOfDay|int(4)||UTC Hour of day|
|UTCISOWeekYear|int(4)||UTC ISO Week of Year|
|UTCISOWeekNo|int(4)||UTC Week No|
|UTCISOWeekDay|int(4)||UTC Day of Week|
|UTCEnglishMonthNameLong|nvarchar(128)||UTC English Month Name Long|
|UTCEnglishMonthNameShort|nvarchar(20)||UTC English Month Name Short|
|UTCEnglishWeekDayNameLong|nvarchar(128)||UTC English Week Day Long|
|UTCEnglishWeekDayNameShort|nvarchar(20)||UTC English Week Day Short|
|DayHour|nvarchar(128)|X|UTC Hour of day|


## DimDeliveryPoint

Schema name: dbo

Description: Dimension table defining the grid delivering point for a facility. Used by FactDeliverypoint for fact data. Link to facility.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|DeliveryPointKey|int(4)|||
|DeliveryPointName|nvarchar(510)|||
|DeliveryPointDescription|nvarchar(510)|||
|FacilityKey|int(4)|||


## DimExtForecastType

Schema name: dbo

Description: Dimension table defining external forecast types. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ExtForecastTypeKey|int(4)|||
|ExtForecastTypeName|nvarchar(128)|||
|AutoExtractEnabled|bit(1)|X||
|Description|nvarchar(510)|||
|TagPrefix|nvarchar(128)|X||
|Supplier|nvarchar(510)|X||
|FirstHourTrig|int(4)|X||
|PowerForecastMethod|nvarchar(510)|X||
|Percentiles|nvarchar(510)|X||
|GranularityMinutes|int(4)|X||
|ExtractPeriodMinutes|int(4)|X||
|ForecastStartMinute|int(4)|X||
|ForecastMinutesPeriod|int(4)|X||
|RoundingStrategy|nvarchar(128)|X||
|Active|bit(1)|X||


## DimExtForecastTypeWeights

Schema name: dbo

Description: Dimension table having setup for weighted forecast types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|TargetExtForecastTypeKey|int(4)|||
|SourceExtForecastTypeKey|int(4)|||
|FacilityKey|int(4)|||
|WeightFactor|float(8)|||
|LastUpdated|datetime(8)|X||
|LastChangedTime|datetime(8)|X||
|LastChangedBy|nvarchar(128)|X||
|ChangedComment|nvarchar(max)|X||
|Active|bit(1)|X||


## DimExtWeatherType

Schema name: dbo

Description: Dimension table having setup for external weather data integrations


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ExtWeatherTypeKey|int(4)|||
|ExtWeatherTypeName|nvarchar(128)|||
|Description|nvarchar(510)|||
|TagPrefix|nvarchar(128)|X||
|Supplier|nvarchar(510)|X||
|FirstHourTrig|int(4)|X||
|ForceUpdate|bit(1)|||
|UpdateType|nvarchar(128)|X||
|MaxHistoryDays|int(4)|X||
|FirstDayOfMonthTrig|int(4)|X||
|MaxDaysInRequest|int(4)|X||


## DimFacility

Schema name: dbo

Description: Dimension table having main setup for facility/plant


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|FacilityName|nvarchar(510)|||
|FacilityDescription|nvarchar(510)|||
|FacilityLocation|nvarchar(510)|X||
|Entity|nvarchar(510)|||
|Continent|nvarchar(510)|||
|Country|nvarchar(510)|||
|PowerNominal|float(8)|X||
|GridName|nvarchar(510)|X||
|PowerNominalACGrid|float(8)|X||
|IPP_Gen_ID|nvarchar(128)|X||
|Unit_ID|nvarchar(128)|X||
|IPPID|nvarchar(40)|X||
|GridConnectionVoltage|float(8)|X||
|RegionKey|int(4)|X||
|RegionScreenNo|int(4)|||
|SiteOrder|int(4)|X||
|NumConnectionPoints|int(4)|X||
|BreakersPerConnectionPoint|int(4)|X||
|ViewAreaKey|int(4)|X||
|ViewAreaOrder|int(4)|X||
|CountryCode|nvarchar(20)|X||
|UID|uniqueidentifier(16)|X||


## DimFeeder

Schema name: dbo

Description: Dimension table having definition for PV feeders for facility/plant. Link to facility.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FeederKey|int(4)|||
|FeederName|nvarchar(128)|||
|FacilityKey|int(4)|||
|ZoneName|nvarchar(128)|X||
|SubFacilityKey|int(4)|X||


## DimForecast

Schema name: dbo

Description: Dimension table having definition for different forecast/budgets per facility. Link to facility and forecasttype


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ForecastKey|int(4)|||
|FacilityKey|int(4)|X||
|ForecastPeriod_Minutes|int(4)|X||
|LastExtract_UTC|datetime(8)|X||
|NextUpdateForecastStartTime|datetime(8)|X||
|ForecastTypeKey|int(4)|||
|SubFacilityKey|int(4)|X||


## DimForecastType

Schema name: dbo

Description: Dimension table having definition for different forecast/budget types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ForecastTypeKey|int(4)|||
|ForecastTypeName|nvarchar(510)|X||
|Description|nvarchar(510)|X||
|IsEditable|bit(1)|X||


## DimGridConnectionPoint

Schema name: dbo

Description: Dimension table having defintion for grid connection points for a facility. Link to facility.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|GridConnectionPointKey|int(4)|||
|FacilityKey|int(4)|X||
|GridConnectionPointName|nvarchar(128)|X||
|Description|nvarchar(510)|X||
|GridName|nvarchar(128)|X||
|GridOwner|nvarchar(128)|X||
|SubFacilityKey|int(4)|X||
|PPCKey|int(4)|X||


## DimInverter

Schema name: dbo

Description: Dimension table having defintion for inverters for a facility. Link to facility and invertertype. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|InverterKey|int(4)|||
|InverterTypeKey|int(4)|X||
|InverterName|nvarchar(510)|||
|InverterShortName|nvarchar(128)|X||
|InverterNo|nvarchar(64)|X||
|TrafoNo|nvarchar(64)|X||
|InverterDescription|nvarchar(510)|||
|Supplier|nvarchar(510)|||
|Model|nvarchar(510)|||
|PowerNominal|float(8)|X||
|PowerNominalDC|float(8)|X||
|FacilityKey|int(4)|||
|Inverter_SerialNo|nvarchar(128)|||
|SMC_SerialNo|nvarchar(128)|X||
|SM1_SerialNo|nvarchar(128)|X||
|SM2_SerialNo|nvarchar(128)|X||
|SM3_SerialNo|nvarchar(128)|X||
|SM4_SerialNo|nvarchar(128)|X||
|SM5_SerialNo|nvarchar(128)|X||
|SM6_SerialNo|nvarchar(128)|X||
|SM7_SerialNo|nvarchar(128)|X||
|SM8_SerialNo|nvarchar(128)|X||
|SM9_SerialNo|nvarchar(128)|X||
|SM10_SerialNo|nvarchar(128)|X||
|Sensor_SerialNo|nvarchar(128)|X||
|HasOnlyDCPower|bit(1)|X||
|SM11_SerialNo|nvarchar(128)|X||
|SM12_SerialNo|nvarchar(128)|X||
|ZoneName|nvarchar(32)|X||
|ClosestWeatherKey|int(4)|X||
|ValueScale|float(8)|X||
|SubFacilityKey|int(4)|X||
|GPSLatitude|float(8)|X||
|GPSLongitude|float(8)|X||
|RelativeXPosition|float(8)|X||
|RelativeYPosition|float(8)|X||
|IsEast|bit(1)|X||
|IsWest|bit(1)|X||
|ProcessUnitID|int(4)|X||
|LastLoadEndTime|datetime(8)|X||
|InverterRow|int(4)|X||
|InverterColumn|int(4)|X||
|IsReference|bit(1)|X||


## DimInverterType

Schema name: dbo

Description: Dimension table having setup for inverter types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|InverterTypeKey|int(4)|||
|InverterTypeName|nvarchar(128)|X||
|Description|nvarchar(510)|X||
|IsStringInverter|bit(1)|||
|NominalACPower|float(8)|X||
|MaxEfficiency|float(8)|X||
|MaxDCPower|float(8)|X||


## DimKpiParameters

Schema name: dbo

Description: Dimension table having properties for a facility used for data extraction and KPI calculations.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|FacilityKey|int(4)|||
|FirstInstallationDate|datetime(8)|X||
|LastInstallationDate|datetime(8)|X||
|AvailabilityNominalBonus|float(8)|X||
|YearlyModuleDegradationBonus|float(8)|X||
|InitialModuleDegradationBonus|float(8)|X||
|AvailabilityNominalLD|float(8)|X||
|YearlyModuleDegradationLD|float(8)|X||
|InitialModuleDegradationLD|float(8)|X||
|PerformanceRatioNominal|float(8)|X||
|PerformanceRatioEPC_Bonus|float(8)|X||
|PerformanceRatioOM_Bonus|float(8)|X||
|PerformanceRatioOM_LD|float(8)|X||
|PerformanceRatioOM_P50|float(8)|X||
|PerformanceRatioEstimated|float(8)|X||
|SoilingTarget|float(8)|X||
|IrradiationStandardTestCondition|float(8)|X||
|InverterType|nvarchar(510)|X||
|ModuleType|nvarchar(510)|X||
|ModuleTypeKey|int(4)|X||
|NominalCellTemperature|float(8)|X||
|ModulePowerTemperatureCoefficient|float(8)|X||
|ModuleEfficiency|float(8)|X||
|ModuleTempAdjustmentLimit|float(8)|X||
|InverterDCLosses|float(8)|X||
|InverterMiscLosses|float(8)|X||
|PlantMiscLosses|float(8)|X||
|FlashTestPeakPower|float(8)|X||
|UseTrackers|bit(1)|X||
|TrackerType|nvarchar(510)|X||
|StartProductionDate|datetime(8)|X||
|FinancialCloseDate|date(3)|X||
|ConstructionStartDate|date(3)|X||
|ConstructionFinishDate|date(3)|X||
|CommercialOperationDate|date(3)|X||
|NumberOfInstalledModules|int(4)|X||
|PlaneOfArrayModuleArea|float(8)|X||
|NumberOfInverters|int(4)|X||
|NumberOfMVBreakers|int(4)|X||
|NumberOfHVBreakers|int(4)|X||
|Location|nvarchar(510)|X||
|DrivingInstructions|nvarchar(max)|X||
|Coordinates|nvarchar(510)|X||
|CoordinateLongitude|float(8)|X||
|CoordinateLatitude|float(8)|X||
|Altitude|float(8)|X||
|CoordinateLongitudeHMIOffset|float(8)|X||
|CoordinateLatitudeHMIOffset|float(8)|X||
|ContactPerson|nvarchar(510)|X||
|EmailAddress|nvarchar(510)|X||
|PhoneNumber|nvarchar(510)|X||
|SkypeAddress|nvarchar(510)|X||
|AreaUnderPanels|float(8)|X||
|LocalCurrency|nvarchar(128)|X||
|NominalHouseholdCapacity|float(8)|X||
|AnnualYieldEstimate|float(8)|X||
|GlobalEmmisionFactor|float(8)|X||
|WarrantyStartDate_EPC|date(3)|X||
|WarrantyEndDate_EPC|date(3)|X||
|FirstLD_Bonus_StartDate_OM|date(3)|X||
|WarrantyIntervalMonths_OM|int(4)|X||
|PlantManagerEmail|nvarchar(510)|X||
|DaylightInclineIrradiationLevel|float(8)|||
|SitePortalURL|nvarchar(510)|X||
|NumZones|int(4)|X||
|UseBusBar|bit(1)|X||
|PlantMapWidth|float(8)|X||
|PlantMapHeight|float(8)|X||
|PlantMapXOffset|float(8)|X||
|PlantMapYOffset|float(8)|X||
|PlantMapImageSource|nvarchar(510)|X||
|ProjectTakeOverDate|datetime(8)|X||
|UseSoilingStation|bit(1)|X||
|UseSoilingRefCell|bit(1)|X||
|ModuleWidth|float(8)|X||
|ModuleRowDistance|float(8)|X||
|Slope|float(8)|X||
|ClippingDetectingFactor|float(8)|X||
|NumberOfDaysForCleaning|float(8)|X||
|CostOfCleaningAllModules|float(8)|X||
|SoilingRateEstimate|float(8)|X||
|SoilingCostPerDayAndPercent|float(8)|X||
|RainAmountForClean|float(8)|X||
|ModuleHeight|float(8)|X||
|ModuleCategory|nvarchar(40)|X||
|AutoGenerateDimStringMonitor|bit(1)|X||
|IsEastWest|bit(1)|X||
|PowerNominalDC_East|float(8)|X||
|PowerNominalDC_West|float(8)|X||
|ShadingFactor|float(8)|X||
|ReportStringLosses|bit(1)|X||
|DegradationModelVersion|smallint(2)|X||
|DefaultExportExtForecastKey|int(4)|X||
|OnlyExtWeatherSource|bit(1)|X||
|UseModuleOrientations|bit(1)|X||
|PRBonusDuringEPCPeriod|bit(1)|X||
|TrackerAvailabilityNominal|float(8)|X||
|LastStringUpload|datetime(8)|X||
|LastTrackerUpload|datetime(8)|X||
|LastLossCalculation|datetime(8)|X||
|UseSnowLosses|bit(1)|X||
|ContractDuration|int(4)|X||
|CalculateStringLossesPerChannel|bit(1)|X||
|CalculateTrackerLossesPerTracker|bit(1)|X||
|IncludeCurtailmentLossesInPR|bit(1)|X||
|TrackerLossesUseOutOfPos|bit(1)|X||
|TrackerLossesUseOutOfPosStateSubClass|nvarchar(128)|X||
|StringSet_UnderPerformanceWarningLevel|float(8)|X||
|StringSet_UnderPerformanceErrorLevel|float(8)|X||
|StringSet_DisconnectedLevel|float(8)|X||
|StringSet_IrradiationCheckLevel|float(8)|X||
|Tracker_OutOfPosLimit|float(8)|X||
|Tracker_OutOfPosAlarmTime|float(8)|X||
|Inverter_UnderPerformanceWarningLevel|float(8)|X||
|StringCombiner_TemperatureAlarmLimit|float(8)|X||
|Inverter_StartupLevelIrradiation|float(8)|X||
|StringCombiner_TemperatureOffsetLimit|float(8)|X||
|TransformerStation_TemperatureHighAlarmLimit|float(8)|X||
|SubstationTransformer_TemperatureHighAlarmLimit|float(8)|X||
|DayIrradiationLevelDeadBand|float(8)|X||
|Weather_LowPassFilterSeconds|float(8)|X||
|StringSet_LowPassFilterSeconds|float(8)|X||
|StringSet_PerformanceAlarms_StartHour|float(8)|X||
|StringSet_PerformanceAlarms_EndHour|float(8)|X||
|StringSet_PerformanceAlarms_DeadbandFactor|float(8)|X||
|Inverter_PerformanceAlarms_StartHour|float(8)|X||
|Inverter_PerformanceAlarms_EndHour|float(8)|X||
|Inverter_PerformanceAlarms_DeadbandFactor|float(8)|X||
|Inverter_LowPassFilterSeconds|float(8)|X||
|LastChangedTime|datetime(8)|X||
|LastInverterUpload|datetime(8)|X||


## DimMeter

Schema name: dbo

Description: Dimension table having defintion for power and energy meters for a facility. Link to facility and invertertype. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|MeterKey|int(4)|||
|MeterName|nvarchar(510)|||
|MeterDescription|nvarchar(510)|||
|MeterType|nvarchar(510)|||
|SerialNumber|nvarchar(128)|X||
|DeliveryPointKey|int(4)|||
|FacilityKey|int(4)|||
|IsBackupMeter|nvarchar(20)|||
|ValueScale|float(8)|X||
|Max_FeedInEnergy_Acc_kWh|float(8)|X||
|Active|bit(1)|X||
|Model|nvarchar(510)|X||
|Supplier|nvarchar(510)|X||
|GridConnectionPointKey|int(4)|X||
|FeederKey|int(4)|X||
|SubFacilityKey|int(4)|X||
|ProcessUnitID|int(4)|X||
|MeterGroup|nvarchar(128)|X||
|IsSubFacilityBackupMeter|nvarchar(20)|X||


## DimMinute

Schema name: dbo

Description: Dimension table having time dimension on minute resolution. Used by fact tables together with dateandhour.


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|MinuteKey|int(4)|||
|Minute|smallint(2)|||


## DimModuleOrientation

Schema name: dbo

Description: Dimension table for module orientation. Not in use


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ModuleOrientationKey|int(4)|||
|FacilityKey|int(4)|||
|TiltAngle|float(8)|||
|AzimuthAngle|float(8)|||


## DimModuleType

Schema name: dbo

Description: Dimension table having setup for module types. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ModuleTypeKey|int(4)|||
|ModuleTypeName|nvarchar(128)|X||
|Description|nvarchar(510)|X||
|MaximumPower|float(8)|X||
|ModuleEfficiencySTC|float(8)|X||
|TemperatureCoefficients|float(8)|X||


## DimPPC

Schema name: dbo

Description: Dimension table having defintion for power plant controllers for a facility. Link to facility. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|PPCKey|int(4)|||
|FacilityKey|int(4)|X||
|PPCName|nvarchar(128)|||
|Description|nvarchar(510)|||
|GridConnectionPointKey|int(4)|X||
|Supplier|nvarchar(510)|X||
|Model|nvarchar(510)|X||
|SerialNo|nvarchar(510)|X||
|PowerScale|float(8)|X||
|VoltageScale|float(8)|X||
|CurtailmentFactorLimit|float(8)|X||
|SubFacilityKey|int(4)|X||
|UseForCurtailmentDetection|bit(1)|X||


## DimRegion

Schema name: dbo

Description: Dimension table having setup for regions


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|RegionKey|int(4)|||
|RegionName|nvarchar(510)|||
|Description|nvarchar(510)|||
|RegionTitle|nvarchar(510)|||
|CoordinateLongitude|float(8)|||
|CoordinateLatitude|float(8)|||
|CoordinateLongitude2|float(8)|X||
|CoordinateLatitude2|float(8)|X||


## DimSection

Schema name: dbo

Description: Dimension table having defintion for sections for a facility. Link to facility. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|SectionKey|int(4)|||
|FacilityKey|int(4)|||
|SectionName|nvarchar(510)|||
|SectionDescription|nvarchar(510)|||
|PowerNominal|float(8)|||
|InverterType|nvarchar(510)|||
|ModuleType|nvarchar(510)|||
|UseTrackers|nvarchar(40)|||
|SubFacilityKey|int(4)|X||


## DimStateCodes

Schema name: dbo

Description: Dimension table having state code definitions for equipment


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|StateType|nvarchar(128)|||
|StateCode|int(4)|||
|StateName|nvarchar(128)|||
|StateClass|nvarchar(128)|||
|StateSubClass|nvarchar(128)|X||


## DimString

Schema name: dbo

Description: Dimension table having defintion for strings for a facility. Link to string monitor. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|StringKey|int(4)|||
|StringMonitorKey|int(4)|||
|TrackerKey|int(4)|X||
|StringName|nvarchar(128)|X||
|StringID|nvarchar(128)|X||
|NumberOfModules|int(4)|X||
|NominalPower|float(8)|X||
|GPSLatitude|float(8)|X||
|GPSLongitude|float(8)|X||


## DimStringMonitor

Schema name: dbo

Description: Dimension table having defintion for string channels for a facility. Link to inverter. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|StringMonitorKey|int(4)|||
|InverterKey|int(4)|||
|TrackerKey|int(4)|X||
|StringMonitorName|nvarchar(128)|||
|StringMonitorGroupName|nvarchar(128)|X||
|StringMonitorTagName|nvarchar(510)|||
|StringMonitorNo|nvarchar(20)|X||
|ChannelNo|nvarchar(20)|X||
|Scaling|int(4)|||
|NominalPower|float(8)|||
|NumStrings|int(4)|||
|HasWarning1|bit(1)|X||
|HasWarning2|bit(1)|X||
|HasWarning3|bit(1)|X||
|NumberOfDaysWithWarning1|int(4)|||
|NumberOfDaysWithWarning2|int(4)|||
|NumberOfDaysWithWarning3|int(4)|||
|LastDateWithoutWarning1|datetime(8)|X||
|LastDateWithoutWarning2|datetime(8)|X||
|LastDateWithoutWarning3|datetime(8)|X||
|LastDateWithData|datetime(8)|X||
|Active|bit(1)|||
|StringColumn|int(4)|X||
|StringRow|int(4)|X||
|IsSplitRow|bit(1)|||
|IsSplitColumn|bit(1)|||
|RelXPos|float(8)|X||
|RelYPos|float(8)|X||
|Width|float(8)|X||
|Height|float(8)|X||
|HasWarning1Morning|bit(1)|X||
|HasWarning2Morning|bit(1)|X||
|HasWarning3Morning|bit(1)|X||
|HasWarning1MidDay|bit(1)|X||
|HasWarning2MidDay|bit(1)|X||
|HasWarning3MidDay|bit(1)|X||
|HasWarning1AfterNoon|bit(1)|X||
|HasWarning2AfterNoon|bit(1)|X||
|HasWarning3AfterNoon|bit(1)|X||
|NumberOfDaysWithWarning1Morning|int(4)|X||
|NumberOfDaysWithWarning2Morning|int(4)|X||
|NumberOfDaysWithWarning3Morning|int(4)|X||
|NumberOfDaysWithWarning1MidDay|int(4)|X||
|NumberOfDaysWithWarning2MidDay|int(4)|X||
|NumberOfDaysWithWarning3MidDay|int(4)|X||
|NumberOfDaysWithWarning1AfterNoon|int(4)|X||
|NumberOfDaysWithWarning2AfterNoon|int(4)|X||
|NumberOfDaysWithWarning3AfterNoon|int(4)|X||
|LastDateWithoutWarning1Morning|datetime(8)|X||
|LastDateWithoutWarning2Morning|datetime(8)|X||
|LastDateWithoutWarning3Morning|datetime(8)|X||
|LastDateWithoutWarning1MidDay|datetime(8)|X||
|LastDateWithoutWarning2MidDay|datetime(8)|X||
|LastDateWithoutWarning3MidDay|datetime(8)|X||
|LastDateWithoutWarning1AfterNoon|datetime(8)|X||
|LastDateWithoutWarning2AfterNoon|datetime(8)|X||
|LastDateWithoutWarning3AfterNoon|datetime(8)|X||
|GPSLatitude|float(8)|X||
|GPSLongitude|float(8)|X||
|NumModules|int(4)|X||
|IsEast|bit(1)|X||
|IsWest|bit(1)|X||
|RowDistance|float(8)|X||
|TiltAngle|float(8)|X||
|AzimuthAngle|float(8)|X||
|ManuallyDeactivated|bit(1)|X||
|MaxCurrent|float(8)|X||
|MaxVoltage|float(8)|X||


## DimSubFacility

Schema name: dbo

Description: Dimension table having main setup for sub facility. Link to facility


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|SubFacilityKey|int(4)|||
|SubFacilityName|nvarchar(510)|||
|SubFacilityDescription|nvarchar(510)|||
|FacilityKey|int(4)|X||
|PowerNominalDC|float(8)|X||
|IPP_Gen_ID|nvarchar(128)|X||
|PowerNominalAC|float(8)|X||
|EnableSubFacilityReporting|bit(1)|X||
|CoordinateLongitude|float(8)|X||
|CoordinateLatitude|float(8)|X||


## DimTracker

Schema name: dbo

Description: Dimension table having defintion for trackers for a facility. Link to facility and trackertype. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|TrackerKey|int(4)|||
|TrackerTypeKey|int(4)|X||
|FacilityKey|int(4)|||
|TrackerName|nvarchar(510)|||
|TrackerDescription|nvarchar(510)|||
|Supplier|nvarchar(510)|X||
|Model|nvarchar(510)|X||
|ConnectedInverterKey|int(4)|X||
|AngleOffset|float(8)|X||
|Active|bit(1)|X||
|IsReferenceTracker|bit(1)|X||
|SubFacilityKey|int(4)|X||
|GPSLatitude|float(8)|X||
|GPSLongitude|float(8)|X||
|RelativeXPosition|float(8)|X||
|RelativeYPosition|float(8)|X||
|SerialNo|float(8)|X||
|ProcessUnitID|int(4)|X||
|LastLoadEndTime|datetime(8)|X||
|TrackerGroup|nvarchar(510)|X||
|TrackerRow|int(4)|X||
|TrackerColumn|int(4)|X||
|MinAngle|float(8)|X||
|MaxAngle|float(8)|X||
|TrackerShortName|nvarchar(128)|X||
|StructureRow|int(4)|X||
|StructureColumn|int(4)|X||


## DimTrackerType

Schema name: dbo

Description: Dimension table having setup for tracker types


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|TrackerTypeKey|int(4)|||
|TrackerTypeName|nvarchar(128)|||
|Description|nvarchar(510)|||
|SupplierName|nvarchar(510)|||
|Category|nvarchar(128)|X||
|Model|nvarchar(128)|X||


## DimViewArea

Schema name: dbo

Description: Dimension table for view areas used in old CMC views


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|ViewAreaKey|int(4)|||
|ViewAreaName|nvarchar(128)|||
|ViewAreaTitle|nvarchar(510)|||


## DimWeather

Schema name: dbo

Description: Dimension table having defintion for weather stations for a facility. Link to facility. 


| Column name | Data type | Nullable| Column description |
|---------|---------|---------|---------|
|WeatherKey|int(4)|||
|FacilityKey|int(4)|||
|WeatherStationName|nvarchar(510)|X||
|WeatherStationDescription|nvarchar(510)|X||
|TrackerName|nvarchar(510)|X||
|OverruleBadTracker|bit(1)|X||
|DefaultDataQuality|int(4)|||
|IsExternal|bit(1)|||
|UseRefCellsForSoiling|bit(1)|||
|HasReversedRefCells|bit(1)|||
|RefCellCalibrationDate|date(3)|X||
|RefCellDirtyCleanOffset|float(8)|||
|RefCellDirtyCleanScale|float(8)|||
|SubFacilityKey|int(4)|X||
|GPSLatitude|float(8)|X||
|GPSLongitude|float(8)|X||
|RelativeXPosition|float(8)|X||
|RelativeYPosition|float(8)|X||
|Model|nvarchar(510)|X||
|SerialNo|nvarchar(510)|X||
|Supplier|nvarchar(510)|X||
|WeatherStationCategory|nvarchar(40)|X||
|IsEast|bit(1)|X||
|IsWest|bit(1)|X||
|ProcessUnitID|int(4)|X||
|StationNo|int(4)|X||
|Active|bit(1)|X||
|SoilingIndexOffset|float(8)|X||
|SoilingIndexScale|float(8)|X||
|SoilingReversedPolarity|bit(1)|X||
|LastSoilingCalibrationDate|datetime(8)|X||


