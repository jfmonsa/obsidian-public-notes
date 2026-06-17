---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

## About Abstraction ![[Pasted image 20241104221850.png]]

+ **DRY**: Don't Repite Yourself Principle
+ **WET**: Write Evrething Twice
+ **AHA**: Avoid Hasty Abstractions (Avoid Premature Optimization, Prefer duplication over wrong abstraction, Don't abstract for the sake of abstracting, but don't do the opposite either! Manage complexity by aiming for simplicity), you shouldn't be dogmatic about when you start writing abstractions but instead write the abstraction when it _feels_ right and don't be afraid to duplicate code until you get there.
---
### Testing
+ AHA is about a sweet spot between DRY and WET (OR ANA), its quite used in testing
+ **WET / ANA**: e.g Repeating everytime the arrange step (set mock dependencies that are almost equal) for each test-case. Harder to read, producing long test files
+ **DRY**: Abstracting too much. overuse of describe and it nesting + beforeEach
---
+ Simple abstraction such as test object factory, or jest-in-case, a collection of test cases iterated by a function which executes each one
#### References
+ https://kentcdodds.com/blog/aha-testing