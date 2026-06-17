---
mocs:
    - "[[public-notes/03-resources/practices.moc.md|Practices]]"
tags:
    - dev/practices
---

## Piramide de los tests
+ Diferentes capas
![[Pasted image 20240908103402.png]]

+ https://kentcdodds.com/blog/the-testing-trophy-and-testing-classifications
# Types of Testing
### Unit Tests
+ Test small pieces of your app
Se hacen aserciones sobre todos los posibles casos (throws, returns) que puede tener una unidad aislada de codigo (funcion, clase), se mockean las dependencias externas
### Integration Tests
Comprueba la logica de como se unen varias unidades de codigo aisladas. es posible concetarse con servicios externos api, db etc.
### Tests e2e (pruebas funcionales)
Test how the end user use the app, run in a navigator
### Regression Tests
Used to verify if recent changes in the code base like refactors or bug fixes have broken functionalities
### A/B Tests

# Herramientas de Testing
+ **Vitest >>> Jest** - Test unitarios backend: objetos de domino, controladores y servicios
+ **Supertest** - para test de integración en backend y frontend. Permite hacer las pruebas de llamadas HTTP
+ **Cypress o Playwright**: para pruebas e2e que simulen las acciones de los usuarios

# Resources
+ https://blog.serverlessadvocate.com/comprehensive-testing-of-serverless-solutions-exploring-integration-e2e-and-unit-testing-with-e55d56eb09bd Brilliant article for testing with aws and good architecture
+ https://www.benmvp.com/blog/end-to-end-testing-firebase-emulator-github-actions/