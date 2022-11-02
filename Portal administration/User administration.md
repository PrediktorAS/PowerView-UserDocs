# User Administration

Users and user access are configured by a system administrator user under the menu Portal admin -> User access.

Computer and network setup is not used in this solution.

__Access groups__ defines a collection of user pages/screens for the user to access. An access group are connected to one or more user roles.

__User roles__ defines the logical user groupings in the portal, linking to one or more access groups and one or more users.

__User__ defines the login user, with user name and password. A user is connected to one or more user roles, and then again to one or more access groups, which at the end defines which pages to access.

General roles used in the central solution are:           

* System Administration: access to monitoring screens, plant reports, central reports, setup screens and administration screens        
* System Configuration: access to all, including system configuration screens
* Enterprise manual input: access to enterprise manual input screens
* Enterprise view: access to all enterprise reports
* Plant view: access to specific plant reports and screens
* App user administration: access to app user setup

General roles used in the plant solutions are:

* Plant monitoring: access to monitoring screens and plant reports
* Plant monitoring and control: access to monitoring screens and plant reports, also with control functions and alarm acknowledge access
* Plant reporting: access to plant reports
* Plant supervisor: access to monitoring screens and plant reports, as well as system setup and manual registrations  
* System Administration: access to monitoring screens, plant reports, setup screens and administration screens       
* System Configuration: access to all, including system configuration screens

See role setup for each plant solution to check for deviations.