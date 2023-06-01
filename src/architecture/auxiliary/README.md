# User interfaces and Auxiliary Services

Micro services are the foundation of our system beyond the signal collection and the advanced analytics. Developing each individual part of our system as an individual micro service allows us to develop, deploy, and maintain each individual part of our system independently of each other, thus building unique and client specific bundles that are tailored for the specific use case.

## The environment

As described in depth here, we prefer Kubernetes as the foundation of our system. We suggest you read through [the following](running_environment.md) before continuing.

## Examples of auxiliary services

### REST APIs

Both the **OPC UA REST API** and **Twin API** are designed as micro services, and can be deployed as stand-alone, but are designed to be deployed as part of a Kubernetes cluster. They utilize a number of the supporting services in the cluster for caching, routing, logging, and monitoring. They also utilize the authentication and authorization services in the cluster for authentication and authorization. The result is a secure, scalable, and cloud native solution that can be deployed on-premises or in the cloud.

### Building information models

The information models creates structured models based on open standards based on the list of equipment that is present. There are a number of different pieces o information and steps needed to automatically create these models and they are all structured as individual micro services.

* The **Model Builder** is a service that will, if pointed in the direction of a list of information (in this case the Data Warehouse) and a information model, populate the information model with the information from the list of information. The result is a structured information model that can be used to create a digital twin.
* The **Config Repository** Will receive the information from the Model Builder and compare it to previous versions of the information model. If there are any changes, it will create a new version of the information model and store it in the information model repository.
* The **Orchestrator Service** is a service that will schedule the Model Builder to run at a specific time, and also make sure that the Model Builder is run when new information is added to the list of information. It can pull new versions from the Config Repository and deploy them to multiple targets, such as the Signal Collectors.
* The **Model Index** is a key service that will allow for super fast lookups of information in the information model. It is a service that will index the information model and store it in a database that is optimized for fast lookups. It has a number of use cases like being used by the Twin API to quickly find the information needed to create a digital twin.

### Visualizations (Web UIs)

Mostly developed in React and TypeScript, the visualizations are designed to be deployed as part of a Kubernetes cluster. They utilize a number of the supporting services in the cluster for caching, routing, logging, and monitoring and importantly the authentication and authorization services in the cluster for access control. The result is a secure, scalable, and cloud native solution that can be deployed on-premises or in the cloud.

The visualizations, if used for monitoring, will utilize the Twin API to get the information needed to create the visualizations. If used for controlling, they will utilize the Twin API to send commands to the equipment. Subscribing to the information through SignalR, the visualizations will be updated in real time.
