# Alarms & Events

Alarms & events are handled in <a href="https://docs.prediktor.com/docs/foundation9/APIS_Chronical/APIS_Chronical.html" target="_blank">Apis Chronical</a>

Alarms are setup in PowerView™ Alarm & Event based on collected signals from equipment and other derived signals. (See also <a href="https://docs.prediktor.com/docs/foundation9/APIS_Chronical/APIS_Chronical.html" target="_blank">Apis Chronical</a>)

Alarms can come directly from equipment devices or be derived from one or more other internal signals and events. 

Alarms are configured with source (e.g. equipment tag), message, group/area, category and severity. Severity is classified into levels:
- High priority level
- Medium priority level
- Low priority level
- No Priority Level

The following alarm types are generated:
- Alarms directly from equipment signals. Alarm text and severity based on information from equipment supplier
    - Inverters
    - Transformer station control
    - Conversion cabinet status
    - PPC
    - Trackers
- Derived alarms
    - Calculated from combination of signals, e.g. Under-performance alarms or string disconnected alarms
- Communication alarms (triggered when communication link to equipment and devices are lost)
- SCADA system condition alarms (triggered from performance metrics on local SCADA servers, e.g. disk/memory/CPU usage, network issues, etc.)

Alarms are acknowledged in PowerView™ web portal by user having right access permissions. Alarm acknowledgement is stored in database together with comment and time, and alarm changed then state in alarm server. Alarm acknowledgement info can be queried in historical reports.

Alarm reporting is done from the <a href="https://docs.prediktor.com/docs/foundation9/APIS_Chronical/APIS_Chronical.html" target="_blank">Apis Chronical</a> data store. A predefined set of reports is available to query alarm history (all event transactions) as well as alarm statistics.

Alarms from equipment is presented in list and graphical views the PowerView™ portal dashboards. The dashboards reflect the current state of the alarms.
The alarm list can be filtered and configured for specific purposes, e.g. to only show active high severity inverter alarms. Colour coding and symbols are used to show severity and alarm state (active/acknowledged). Graphical alarm symbols can be added to visual single or multiple alarms being triggered.

Alarm reports are used to query the history database. All parameters defined on alarm source can be entered in filter, building a powerful alarm query.

Alarms can be sent to a set of mail recipients. Mail submission can be filtered and grouped in different ways, like severity, area, plant, etc. Buffering can also be configured. 
Example can high severity alarms be sent right away while other alarms grouped and sent every 10 min / 1 hour / daily.

Alarm mails can be converted to SMS messages using mail to SMS service providers.
