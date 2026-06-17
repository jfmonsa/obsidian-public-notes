---
mocs:
    - "[[public-notes/03-resources/devops.moc.md|DevOps & Cloud]]"
tags:
    - dev/devops
---

# Fundamentals: ¿What is Cloud computing?

+ Using networks to access remote servers
+ Azure, GCP, AWS
## Benefits
+ Pay for what you consume (Pay-as-you-go) (PAYG) (Cost-effective)
+ Global: choose regions
+ **Scalability**: increase your capacity
	+ ==Horizontal Scaling (Scaling Out)==: Add multiple servers of the same size
	+ ==Vertical Scaling (Scaling Up)==:  Upgrade to a bigger server
+ Security
+ **Reliable**: data backup, disaster re cover
+ **Elasticity**: Automate ==scaling== based on demand
+ **High Availability** Running workload across multiple availability Zones, ensures that  if 1 or 2 server become unavailable your service remains available (A load balancer) distribute traffic to multiple servers.
+ **Fault Tolerant**: no single point of failure
	+ ==Fail-overs==: when you have a plan to shift traffic to redundant system in case the primary fails (Azure traffic manager)
+ **High Durability**: Recover from disaster and prevent data loss (Disaster Recovery): backups
 
![[Pasted image 20250110153819.png]]

## Cloud Services
A Cloud Service Provider (**CSPs**) can have hundreds of cloud services. the main four for IaaS (Cloud computing refers to all the terms):
+ **Compute**: Virtual computer that run applications, programs etc.
	+ **Azure**
		+ Virtual Machines (VMs):Choose OS, RAM, CPU, Storage
		+ Azure Container Instances (CaaS)
		+ Azure Kubernetes Service (AKS)
		+ Azure Service Fabric (microservices)
		+ Azure Functions (FaaS) (Serverless Functions)
		+ Azure Batch: Schedule jobs
		+ Azure App Service
+ **Storage**: Virtual hard-drive (Store files)
+ **Networking**: Virtual network being able to define internet connections or network isolation
+ **Databases**
## Types of cloud computing
![[Pasted image 20250110154919.png]]
+ IaaS (Infrastructure as a Service):
+ CaaS (Container as a Service): Docker
+ PaaS (Platform as a Service): Desarrollador solo responsable de escribir el codigo
+ FaaS (Function as a Service): Automatización de tareas
+ SaaS (Software as a Service)
+ On-premise: local development
![[Pasted image 20250110155212.png]]

## Deployment models
+ Public cloud: Azure, GCP, AWS, subscripción mensual, pago por uso.
+ Private Cloud: Entorno exclusivo gestionado por una organización para su propio uso (In your own infrastructure)
+ Hybrid: Se complementa la nube pública y privada.
+ Cross-Cloud: Using multiple cloud providers: e.g. usign: Amazon EKs, GCP Kubernetes Engine

## Total Cost of Ownership (TCO)
+ **CAPEX (Capital Expenditure)**: On-Premise, expending money on physicall infrastructure
+ **OPEX**: Azure (Subscriptions fees)

## Cloud Architecture Terminologies
+ **Solutions Architect**: Rol, that architects technical solutions using multiple systems via researching, documentation, experimatation
+ **Cloud Architect**: A solution architect that is focused solely on architecting technical solutions for cloud services

## Business Continuity Plan (BCP)
+ Is a document that outlines how a business will continue operating **during unplanned disruption in services**
![[Pasted image 20250110162857.png]]

### Disaster Recovery Options
+ trade cost vs time to recover
![[Pasted image 20250110163214.png]]

## Evolution of Computing
![[Pasted image 20250110163845.png]]

## Regions and Geographies (Azure)
+ A **region** is a grouping of multiple datacenters (Availability zones
	+ each region is paired wih another region 300 miles away
+ A **geography** is discreet market of two or more regions that preserves data residency and compliance boundaries
+ **Availability zone (AZ)** physical location made up of one or more datacenters
	+ Its common practice to run workloads in at least 3 AZs to ensure services remain available
	+ Terms to the exam: Fault Domain (in case of hardware failure), Update Domain (maintenance), Availability Set
![[Pasted image 20250110164227.png]]

## Azure specific Terms
+ Tenant
+ User, user group
+ directory