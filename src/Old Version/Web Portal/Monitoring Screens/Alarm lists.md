# Alarm lists

The alarm list is a real time component, showing the state of the active and not acknowledged alarms.

Following information is provided in the list:

Alarm severity:
H: High severity (severtity number 800-900)
M: Medium severity (severity number 500-780)
L: Low severity (severity number 1-400)
Source: Source (equipment/tag) of alarm
Time: timestamp of last event change 
Ack time: acknowledge time (if not acknowledged, it is the event time)
Message: alarm message text of last state 
Color coding are used to show state of alarm:

Not active and acknowledged: not shown in list
Active and acknowledged: green
Not active and not acknowledged: yellow
Active and not acknowledged: red
Sorting of the list can be done clicking the header text in the table. Default sorting is on Severity, showing high severity alarms at top of list.

Filtering alarms can be done in the main list, using input fields above the list:

Alarm area filter: select "All alarms", or one of the other alarm areas/groups
Alarm source filter: enter a filter to get certain alarm sources, using * as wildcard. E.g. *GridFrequency* for all alarm sources containing GridFrequency 
Number of alarms in list: maximum number of alarms to be displayed at one time in the list.
Alarms can be acknowledged using the "Acknowledge" button below the list. Alarms to be acknowledged are selected using the check boxes to the left in the list and then pressing the button. An optional comment can be added before pressing button. This comment is stored in the database, and can be seen in the historical alarm report.

 