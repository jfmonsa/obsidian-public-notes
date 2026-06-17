---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

+ are objects (**Dumb Objects / POJOs**) that carry data between processes
+ is a harcode data model
+ Allow us to implement encapsulation of the serialization’s logic (**Data sanitazion**) e.g. data in api request
+ This is when DTOs are used within the same application but between different layers
## How To Use It
+ are created as POJOS (Flat data structures that contain no business logic)

## Use Cases
+ pass data from http layer to business logic layer
+ defining contract between services in microservices
## Cons
+ Mapping
+ extra complexity
+ bloatware

# DPP - Plain Old Java Objects (POJO)
+ a class that is no tied to a particular framework