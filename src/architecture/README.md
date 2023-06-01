# Architecture

We have three different types of architecture in PowerView:

* [Architecture that enables direct equipment signal collection](signals/)
* [Architecture to enable storage and advanced analytics capabilities](advanced_analytics/)
* [Architecture to enable the user interface and auxiliary services](auxiliary/)

The versatility of such an architecture is that it can be deployed in a variety of ways, depending on the use case. For example, the architecture can be deployed in a single server, or it can be deployed in a distributed fashion, with each component in a different server or in different environments. The architecture can also be deployed in a cloud environment, such as Azure, or in an on-premises environment.

## Infrastructure concerns

Depending on the demands of the use case, and in cooperation with our clients, we can dimension the solution to run from everything from a singel server to complex multi-environment depoyments. The following illustrates points that should be part of the discussion and will form the requirements for the infrastructure:

### Separation of environments

Moderns software has a release frequency that is much higher than the traditional industrial software. This means that the environments where the software is deployed should be separated, so that the development environment does not interfere with the production environment. Also, because of the complexity of the solution, it is important to have a test environment where the solution can be tested before it is deployed to production. Whereas we as part of our development process have several layers of environments, we recommend that our clients have a staging environment, where the solution can be tested before it is deployed to production.

### Availability

We recommend that you ask yourself two questions when it comes to availability:

* How much data can you afford to lose?
* How long can you afford to be without the fully operative solution?

The reason why these questions are important is that they will determine the type of infrastructure that is needed. For example, if you can afford to lose data, then you can use a single server, potentially with a stocked spare. If you cannot afford to lose data, then you need to have a redundant solution, where the fail-over process to another server is "hot" and automated. The same thing goes for the operative solution, where any demands for high availability will require redundant solutions.

Picture a scenario where you can afford to lose an hour of data and you can afford to be without main parts of the functionality of the system for 12 hours. In this case, you can have a single server for signal collection, with a stocked spare. The data replication functionality will make sure that any collected data is replicated out, and also potentially backfill your stocked spare with the historical data once operative. The process of backfilling data will allow more functionality to be available, influencing the time to fully operative solution.

#### Dependency on Internet connection

Obviously, signal collection from equipment needs to happen close to the equipment, and the same goes for the short term storage of the data. However, the user interface and auxiliary services can be located anywhere, as long as there is a connection between the two. This means that the user interface and auxiliary services can be located in a cloud environment, such as Azure, or in an on-premises environment. Your dependency on the Internet connection will increase dramatically if you want to have the user interface and auxiliary services in the cloud, but this is a trade-off that you may want to make.

#### Evaluating the need for stand-alone solutions

Different sites have different needs, and it is important to evaluate the need for stand-alone solutions. For example, if you have a site that is located in a remote area, with a poor Internet connection, then you may want to have a stand-alone solution for that site. This means that you will have a separate solution for that site, with its own signal collection and storage capabilities, and its own user interface and auxiliary services. The stand-alone solution will be able to operate independently of the other solutions, but it will also be able to replicate data to the other solutions. The main reason for our clients to have a stand-alone solution is to be able to operate independently of the other solutions, and thus maintaining a high level of flexibility. This can be because of complex ownership structures or because the asset is part of a temporary commercial strategy. If this is the case, we strongly suggest that we together set up a plan for how to extract data and functionality from the cloud environment rather than having a permanent stand-alone solution. This will allow a minimum requirement for infrastructure at the site to keep the cost down, and also allow for a more flexible solution.

