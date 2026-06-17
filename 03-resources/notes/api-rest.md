---
mocs:
    - "[[public-notes/03-resources/system-design.moc.md|System Design]]"
tags:
    - dev/system-design
---

- API REST (Representational State Transfer) is an architectural style for designing web services.
+ It uses HTTP methods (GET, POST, PUT and DELETE) to perform CRUD (Create, Read, Update, Delete) operations on resources.

+ **API**: Application Programming Interface
+ client / server model thought HTTP 
+ Coined in Roy Fielding's 2000 PhD dissertion
+ organizes API entities or resources into unique (URIs)

# HTTP
+ Internet protocol
+ define the mechanism through clients and servers can share resources

![[Pasted image 20240912143633.png]]
## Parts of HTTP Request / Response
- **Request Line**: HTTP method (GET, POST, PUT, DELETE) + URL.
- **Headers**: Metadata such as Content-Type, Authorization.
- **Body**: Data sent in the request (usually in POST and PUT).

# Resource
- An identifiable element that can be accessed via a URI (e.g., a user, an order).
- Represented in different formats, commonly JSON or XML.

# Representation
- The way a resource is presented (JSON, XML, HTML).
- Contains the resource data and may include metadata.

# API REST restrictions
+ Clientes (consumidores) están desacoplados del servidor (proveedor) permitiendo su evolución independiente
+ toda información dentro de la solicitud debe ser cacheable
+ solo se emplea HTTP
## Stateless
+ Each client request to the server must contain all the information needed to understand and process the request, with no server-side session state between requests.
+ Any requirement about state persistence must be handled by client and sent to server (e.g. Auth token)


# Versioning API Rest
+ In order to update API and not break compatibility with clients which uses legacy API
+ Change is inevitable
+ Can be implemented via URL paths (e.g., `/v1/resource`), HTTP headers, or query parameters.

