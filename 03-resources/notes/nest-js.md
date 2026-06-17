---
mocs:
    - "[[public-notes/03-resources/backend.moc.md|Backend]]"
tags:
    - dev/backend
---

# Intro
+ Nest provides a level of abstraction above these common Node.js frameworks (Express/Fastify). But also exposes their APIS directly to the developer
+ Nest provides an out-of-the-box application architecture, heavily inspired by Angular Architecture (MVC)

## Create a Project
Use nest CLI
```bash
$ npm i -g @nestjs/cli
$ nest new project-name
```

# Architecture
+ Principios SOLID
+ Heavily tied to Dependency Injection Pattern

![[Pasted image 20240907081845.png]]

## 1. Modules
+ Is the heart of an API entity, connects controller, service and models of an API REST entity
+ Primero se debe crear el modulo antes de crear servicios o controladores, etc.
+ are used to organize related code into cohesive units
+ a way to encapsulate related components, controllers, and services within a single module
+ From a technical perspective, ==the sole purpose of a module is to configure the dependency injection mechanism== of NestJS

```
nest g mo users
```

+ The root module is the starting point Nest uses to build the application graph - the internal data structure Nest uses to resolve module and provider relationships and dependencies

### Each Module
- **Providers** – In this array, we can define what will be injected in places as they are indicated by injection tokens. The injection token can be, for example, a class definition, so in most cases you will see an array of classes here.
- **Controllers** – NestJS treats controllers a little bit different than any other providers so they have their own definitions. However, they can also be injected like any other providers.

**In the second group we have:**

- **Imports** – We define a list of modules that we want to use in our module. We will be able to inject providers they exported into our own providers.
- **Exports** – We define a list of providers that we want to make accessible for other modules.
### @Module() decorator
+ **providers** -> the providers that will be instantiated by the Nest injector and that may be shared at least across this module (services)
+ controllers
+ **imports** -> the list of imported modules that export the providers which are required in this module
+ **exports** -> the subset of `providers` that are provided by this module and should be available in other modules which import this module.
### Shared Modules
+ Every module is automatically a **shared module**. Once created it can be reused by any module
+ In order to shared a service with put it in export array of a module
### Dynamic Modules
### Resources
+ Intro to Modules
+ https://medium.com/@briankworld/creating-a-shared-module-in-nestjs-benefits-and-use-cases-6292a1dcd200 - Shared modules
+ https://youtu.be/jOytv6PQxN0?si=u46mscGTPySauHYj How a Large Scale NestJS App Should ACTUALLY Look (Hierarchical Modules, multiple apps in the same project)

## Scalling Nestjs App
### Hierarchical Modules
+ Group related modules in a higher order module

e.g.
![[Pasted image 20241003001403.png]]

You should group modules by
+ Business Logic
+ Team Organization

### Several applications in same nest js project
+ Serves as a high level abstraction layer reusing modules in different contexts
e.g
![[Pasted image 20241003001735.png]]

+ apps created are parts of the same ecosystem, they shared several components
+ To share things acrross apps you can create libraries where you can share: entire modules, decorators, exceptions, middlewares, filters etc.

![[Pasted image 20241003002041.png]]

### Microservices
+ Using the several apps approach you can have multiple apps where each other are microservices that can be deploy independently

## 2. Controllers
+ Controllers are responsible for handling incoming **requests** and returning **responses** to the client.
+ In order to create a basic controller, we use ==classes and decorators==. Decorators associate classes with required metadata and enable Nest to create a routing map

### Routing
+ Use `@Controller('cats')` to specify a route prefix
+  The route path for a handler is determined by concatenating the (optional) prefix declared for the controller, and any path specified in the method's decorator

```typescript

import { Controller, Get } from '@nestjs/common';

@Controller('cats')
export class CatsController {
  @Get()
  findAll(): string {
    return 'This action returns all cats';
  }
}
```

> [!HINT]
> To create a controller `$ nest g controller [name]`

### Request Object
+ use `@Req()`decorator but in most cases we can use dedicated decorators such as:
	+ `@Body()`, `@Query()`, `@Params`, `@Headers`
+ you can use `@types/express`

## 3. Services
+ usamos DTOs y class validator para validar datos

> `nest g s [name]`

Si queremos crear servicios anidados en una carpeta
> `nest g s users/services/users --flat`
+ Uses `@Injectable` Decorator

### DTO: Data Transfer Object
+ Una clase intermediaria entre los datos de la request y las entidades del backend

## 4. Providers and Dependency Injection
+ Many of the basic Nest classes may be treated as a provider – services, repositories, factories, helpers, and so on
+ The main idea of a provider is that it can be **injected** as a dependency
+ Controllers should handle HTTP requests and delegate more complex tasks to **providers**.
+ Providers are plain JavaScript classes that are declared as `providers` in a [module](https://docs.nestjs.com/modules).

## 5. Basic Setup of a project
+ configure .env
+ configure api versioning3
+ swagger documentation
+ interceptor to format api responses
	+ https://youtu.be/NhBblxY9zzo?si=Kz3mghxQ72LWczTR
	+ https://blog.stackademic.com/crafting-a-uniform-response-structure-in-nestjs-a-guide-to-mastering-interceptors-706820b5aa0b

## 6. Pipes
Transformar la data recibida en requests, para asegurar un tipo, valor o instancia de un objeto

## 7. Interceptors
### Before Interceptor
Interceptan la solicitud (request) y la pueden transformar completamente
+ Cache
+ Logs

### After Interceptor
Intercepta la respuesta que emitirá el controlador y la puede transformar completamente basado en las necesidades.
+ Alamcenar cache de la response
+ formatear la response

## 8. Guards
+ Permitir o prevenir acceso a una ruta

## 9. Exception filter
+ Maneja los errores de código en mensajes de https://youtu.be/KfvCXO3zPCk?si=ntVdEcpSFV_SlJlarespuesta http
# Recursos
+ https://youtube.com/playlist?list=PLergODdA95kfcSoXqZZ-IDImO6YaQLYlG&si=fOTcjd_e1d1sdUPB - Playlist super recomendada
+ https://youtube.com/playlist?list=PL2cV4xVnwFlmhwJwbUOchUZMJEEh_9wAQ&si=OAPcGrID0iQma_vy - Lista de reproduccion de nest
+ https://www.youtube.com/watch?v=wsqcg5ZtUMM - Curso de nest Fatz
# Ciclo de vida nestjs
![[Pasted image 20240913094441.png]]