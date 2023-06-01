# Interface Architecture

Each part of our architecture have their distinct methods of exchanging information, sometimes tied together by libraries.

## Signal Collection Interfaces

Our edge software is centered around OPC UA for communication, both external and internal. OPC UA, an open protocol for industrial communication, is made for interoperability, and as such is the best way to interface our edge/signal collection. It allows you to retrieve both historical and current signals and trends, as well as alarms and events. As our edge also supports the Information Model part of the OPC UA standard, you'll be able to query the data in a modeled structure, rather than knowing the individual names and addresses of your equipment. Our choice of a proper industrial protocol for edge communication shows our commitment to open standards and our efforts to guarantee interconnectedness through industries, also beyond the energy sector.

Most developers not used to working with industrial protocols will find the OPC UA protocol a bit of a threshold. To mitigate this, we have developed two RESTful APIs:

* OPC UA Values REST API
* Twin API

In addition, to allow for faster interaction with the model, we supply a dedicated index in the form of a REST API, the **Model Index**.

You can also check out our [Python SDK](https://github.com/PrediktorAS/pyPrediktorMapClient) for the OPC UA Values REST API and Model Index.

## Storage Interfaces

For most use cases, directly accessing the data warehouse that is part of our [advanced analytics](../advanced_analytics/) architecture through SQL is the best way to access the data. This is the most flexible way to access the data, and allows for the most complex queries. However, for some use cases, time series data with even higher resolution is needed. For this, we recommend communicating through OPC UA, potentially through the REST APIs.

We do not allow direct write access to the data warehouse, as this would compromise the integrity of the data. All data is written to other databases, and then transferred to the data warehouse through a process that ensures the integrity of the data.

A set of APIs have been developed to allow for a more flexible access to the data warehouse through Python, called the **Data Engineering Suite**. This suite of APIs structures the read from both sources (SQL and OPC UA) in a similar way, as well as providing a set of functions to write to the data warehouse through other databases.

## Subscribing to Data

If you want to subscribe to data, e.g. for a front end visualization React app, you can use the OPC UA Values REST API or Twin API. These APIs allows you to subscribe to data through SignalR, and then receive updates as they happen. This is a very efficient way to get data, as you don't have to poll the server for updates. The API is also very flexible, and allows you to subscribe to data from multiple sources at the same time, and to filter the data you receive.
