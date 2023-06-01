# Environment and Infrastructure

Most of our micro services can be deployed as stand-alone but are designed to be deployed as part of a Kubernetes cluster. As the Kubernetes cluster is the foundation of our system, we will start by describing the Kubernetes cluster, and then we will describe how micro services are deployed as part of the Kubernetes cluster.

## Kubernetes cluster

Kubernetes has a number of advantages over more traditional deployment methods, such as virtual machines. The main advantages are:

* Scales easily
* Cloud native
* Supports DevOps, CI/CD and automation
* Can be deployed on-premises or in the cloud

The process of developing for micro services is different from traditional development. The main difference is that the micro services are developed independently of each other, and that the micro services are deployed independently of each other. This means that the micro services are developed and deployed in a continuous fashion, and that the micro services are deployed in a distributed fashion. Our process consists of the following steps:

### Development, DevOps and SysOps

For us, DevOps is a set of routines, solutions, procedures, and software that makes sure that we have a well-defined and coherent process leading from idea to deployable solution in tracked versions. To mention some of the highlights, the process goes from scoping and planning, peer-reviewed coding, automated testing and building process and potentially automatic deployment into environments. Separating the configuration from the code is a key element in this process, as it allows us to have a single code base that can be deployed in different environments. This means that we can have a development environment, a test environment, a staging environment, and a production environment, and that we can deploy the same code base in all of these environments. The configuration will determine the behavior of the code base, and thus the environment.

Utilizing different software projects and methods, such as ArgoCD, and Helm, we can automate the deployment process, and thus have a continuous deployment process. This means that we can have a continuous integration process, where the code base is continuously tested and built, and a continuous deployment process, where the code base is continuously deployed into the different environments. The continuous deployment process is triggered by a change in the code base, and the process is fully automated.

Using Terraform, we can automate the creation of the infrastructure, and thus have a continuous infrastructure process. This means that we can have a continuous integration process, where the infrastructure is continuously tested and built, and a continuous deployment process, where the infrastructure is continuously deployed into the different environments. The continuous deployment process is triggered by a change in the infrastructure, and the process is fully automated.

As a result, we potentially have a fully automated process from idea to deployable solution in tracked versions. It is important to note that this does not cover the signal collection or the advanced analytics, but only the micro services.

### Where to deploy the cluster

As mentioned, Kubernetes can be deployed on-premises or in the cloud. We prefer to deploy the Kubernetes cluster in the cloud, provided by a number of different cloud vendors, such as Microsoft Azure, Amazon Web Services, and Google Cloud Platform. The main reason for this is that we want to focus on the micro services, and not on the infrastructure. It also enables easy scaling, and it is easy to deploy the same code base in different environments.

### Overhead and supporting services

The Kubernetes cluster is the foundation of our system, but it is not the only service that we need. We also need a number of supporting services, such as a database, a message queue, and a logging service. These services are deployed as part of the Kubernetes cluster. In order for one services to be deployed, most of these services needs to be in place, creating a substantial overhead in the beginning. However, as the services are deployed independently of each other, the overhead is reduced over time. The following is a list of the services that we use, though not exhaustive:

* PostgreSQL (for storing data and configuration)
* REDIS (for caching)
* NGINX (for routing)
* Cert-Manager (for certificates)
* Grafana Loki (for logging)
* Grafana (for visualization)
* Prometheus (for monitoring)
* ORY Oathkeeper (for authentication and authorization)
* ORY Hydra (for authentication and authorization)
* ORY Keto (for authorization)
* ORY Kratos (for authentication)

### Security and access

Both on the infrastructure level and on the micro service level, we have a number of security measures in place. On the infrastructure level, we need connection between the cluster and signal collection as well as the advanced analytics. On the micro service level, we need to make sure that the micro services are only accessible by the services that are supposed to access them. Depending on the hosting environment chosen for the cluster, we have different options for securing the cluster and the micro services. For example, if we deploy the cluster in Microsoft Azure, we can use Azure Active Directory for authentication and authorization. If we deploy the cluster in Amazon Web Services, we can use AWS IAM for authentication and authorization. If we deploy the cluster in Google Cloud Platform, we can use Google Cloud IAM for authentication and authorization. If we deploy the cluster on-premises, we can use ORY Oathkeeper, ORY Hydra, and ORY Keto for authentication and authorization.