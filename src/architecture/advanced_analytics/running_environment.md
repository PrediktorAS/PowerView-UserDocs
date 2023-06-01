# Environment and Infrastructure

Most of the advanced analytics functionality is centered around Microsoft SQL Server. This includes the data storage, the data processing, and the data presentation. The advanced analytics functionality is built on top of the SQL Server platform, and it is designed to take advantage of the built-in functionality of SQL Server. This includes the built-in functionality for high availability, scalability, and security.

## On-prem or Cloud

The advanced analytics functionality can be deployed in an on-premises environment, in a cloud environment, or in a hybrid environment. The choice of environment is based on your demands for availability, functionality, and security.

With MS SQL Server being a requirement and some of the more advanced functionality not available as a managed service in Azure, the most common scenario is to deploy the advanced analytics functionality on a virtual machine in Azure. This is a good choice, as it provides a good balance between availability, functionality, and security.

## High Availability

Analytics is a mission critical functionality for many of our customers, and as such, high availability is a key requirement. The advanced analytics functionality is designed to be highly available, and it is built on top of the built-in high availability functionality of SQL Server. We usually design the solution together with the customer, and the discussion is centered around the following principles:

* What is the criticality of the solution?
* KPIs and predictions are usually not mission critical, but they are important for the business. Are there any KPIs or predictions that are mission critical? E.g. reporting to third parties?
* What is the acceptable downtime?

The answers to these questions will dictate the choice of high availability solution.

## Auxiliary Services

Quite a few auxiliary services are required for the advanced analytics functionality. These are usually deployed as micro services in the appropriate environment, and they need access to the virtual machine running the advanced analytics functionality.