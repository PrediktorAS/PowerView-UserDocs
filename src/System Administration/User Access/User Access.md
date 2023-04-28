# User Access

Users and user access are configured by a system administrator in web portal screens.
- Access groups defines a collection of user pages/screens for the user to access. An access group are connected to one or more user roles.
- User roles defines the logical user groupings in the portal, linking to one or more access groups and one or more users.
- User defines the login user, with user name and password. An user is connected to one or more user roles, and the again one or more access groups, which at the end defines which pages to access.

General access groups and roles used in the portfolio solution is:           
- Portfolio Monitoring: access to monitoring screens
- Portfolio Reports: access to reports
- Portfolio Analysis: access to analysis reports and dashboards
- Portfolio Manual Input: access to manual registration screens
- Portfolio Administration: access to PowerView administration screens

## User Activty Report

User activity is logged in the database for every page access or reload. A user activity report can be found in the "User activity report".

The report can be filtered by user name (default all) and time (default current day).

The content of the report is:
- Activity time: time of page load
- User name: name of user accessing the page
- IP address: address of client PC accessing the portal page
- Portal page: title of page being accessed
- Activity type: initial load or reload
- Login time: time for last login to the portal
- Portal page: title of portal page Activity type: initAc


 