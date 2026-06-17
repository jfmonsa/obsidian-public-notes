---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
    - dev/backend
---

+ variant of API Gateway
+ additional layer between microservices and each client separately
+ In modern application architecture, the BFF pattern acts as a middleware layer that handles data aggregation, enhances performance through caching, and hides unnecessary data to improve security and efficiency
+ you can have a tailored API that targets the needs of each client (mobile, web, desktop, voice assistant, etc.)
![[Pasted image 20250218101226.png]]
+ you can create endpoints for specific screens or features, hiding de complexity for client
+ The BFF can benefit from hiding unnecessary or sensitive data before transferring it to the frontend application interface, so keys and tokens for 3rd party services can be stored and used from BFF.
+ Apply data transformation (adapters layer) in the BFF simplifying client logic
+ Give us possibilities to develop specific server logic for each type of client, for example queue for notifications on mobile apps client
## Tips
+ Use _particular feature first over generic usage_ strategy

## When to use?
+ Multiple frontends consuming one backend or future plans to use multiple frontends
## Alternatives
+ alternative solutions like API Gateway or GraphQL might be more appropriate.
# BFF Patterns

# Resources
+ https://medium.com/mobilepeople/backend-for-frontend-pattern-why-you-need-to-know-it-46f94ce420b0
+ https://bff-patterns.com/patterns/ Recurso muy completo con patrones especificos para BFF