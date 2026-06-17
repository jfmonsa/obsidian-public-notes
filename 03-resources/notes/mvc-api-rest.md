---
mocs:
    - "[[public-notes/03-resources/system-design.moc.md|System Design]]"
tags:
    - dev/system-design
    - lang-es
---

# MVC architecture for Rest API (Focused on express)
+ an API receives a **request** and returns a **response**
+ that request from the point it hits our application, travels through our layers
+ and a response gets returned by the app
+ posibliidad de cambiar implementaciones de una capa sin romper cosas en otras gracias a la abstracción
+ things as modular as possible
+ contract between layers consistant
## Layers Overview
1. Http layer: controllers and routes
2. Business Layer: services (business logic), respositories (data base interaction) and models (representation of data) ( Some frameworks require them in order to interact with data base)
3. View: is the response of the api, can be html or json

**Basic Diagram**

![[Pasted image 20240814133620.png]]

**More complex one**
![[Pasted image 20240817104358.png]]
### Http Logic Layer
+ HTTP logic layer	Routes + Controllers
	+ Routes - handle the HTTP requests that hits the API and route them to appropriate controller(s)
	+ Contollers - take request object, pull out data from request, then send to service(s)

### Business Logic
+ Business logic layer
	+ **Services**:	Contains the business logic, derived from business
	+  **Data Access (repositories)**: can be used by multiple services as well as how we access our data stores
	+ **Models (optional)**: singletone classes for orm's and typescript interfaces (mostly)

## Routes
+ Use index.js file to export routes reading dynamically the folder
## Controllers
+ think of controllers as "orchestrators".
+ They call the services, which contain more "pure" business logic.
+ But by themselves,controllers don't really contain any logic other than handling the request, validate data, calling services and send response.
+ The services do most of the work, while the controllers orchestrate the service calls and decide what to do with the data returned.

> [!IMPORTANT]
> Something I see fairly frequently is the Express req object (which is our HTTP "context") passed through beyond the routes and controllers to the services or even database access layer. But the problem with that is that, now the rest of the application depends on not only the request object, but on Express as well. If you were to swap out frameworks, it would be more work to find all the instances of the req object and remove them.
 >+ It also makes testing more difficult and this does not achieve a separation of concerns that we strive for in designing our applications.
 >+ Instead, if you use destructuring to pull out what pieces of data you need from req, you can simply pass those on to the services. The Express logic "ends" right there in the controllers.
## Services
Services should contain the majority of your business logic:
+ logic that encapsulates your business requirements,
+ calls your data access layer or models
+ calls API's external to the Node application. And in general, contains most of your algorithmic code.


## Data Access Layer / Repositories
If it's not obvious, "Data Access Layer" means the layer that contains your logic for accessing persistent data. This can be something
+ like a database
+ Repository layer, methods and interfaces you can fetch the data
+ a Redis server, Elasticsearch
+ So whenever you need to access such data, put that logic here.
+ raw sql query

## Models?
+ sometimes is required by some orm's or frameworks in order to interact with data
+ model layer defines programming interface of the database

## Other folders
### middlewares
### config
### Utils
The last type of logic we'll cover is that of common logic functions that are not necessarily specific to your business logic or domain,

### tests
+ mimic porject's folder structure
![[Pasted image 20240814135113.png]]


## Resources
+ Project structure for an Express REST API when there is no "standard way" - https://www.coreycleary.me/project-structure-for-an-express-rest-api-when-there-is-no-standard-way
+ MVC Advanced: Service, Controller, and Repository Layers in MVC Architecture - https://youtu.be/NzAgWNaG24s?si=kvwhUTsuGjLMBHcI (Ver obligatoriamente, explica la arquitectura actual del proyecto)
+ https://www.coreycleary.me/why-should-you-separate-controllers-from-services-in-node-rest-apis
