---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

+ Use a logger like pino or wiston when dealing with apps used by real people

##  Type of Errors

### Programmer (bugs) - just solved it
+ mistake in logic or sintax
+ implemente unit tests
### Operational
+ expected errors
+ when operation has the pontential to fail
+ Handled by determining what should happen if it fails
+ eg. "User not found", "Not authorized"
### Unexpected / Unstrusted
+ Could crash the app if uncorrectly handled
+ don't give specific information to the user about this errors

## Strategies
+ Dictionary with common http error codes
+ handle errors in middleware (filter in the case of nestjs) instance of and return proper response to the user (case of an api)
+ throw errors only in services where you handle the Business Logic
+ Think about where you should throw the error: ==who is resposible to handle it?== in the function itself? in the service that calls the function? (usually correct)