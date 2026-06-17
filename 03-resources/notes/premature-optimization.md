---
mocs:
    - "[[public-notes/03-resources/practices.moc.md|Practices]]"
tags:
    - dev/practices
---

# Premature Optimization

> I truly do believe that premature optimization is the root of all evils - Donald Knuth

Tradeoff triangle:
![[Pasted image 20241005140332.png]]

+ **Velocity**: How fast a new feature is added
	+ If you go only for velocity, you will created a lot of techical debt (eg.:not following SOLID)
+ **Adaptability**: How well the system can change to new , reusable, extensible components
+ **Peformance**
	+ Macro performance: At design level
	+ Micro performance: at a module or function
---
+ where to focus depends on the stage of your project
+ For performance issues:
	+ Measure
	+ Try something ,analysis of: 
		+ ==data structures==
		+ Profiling
		+ Think about how your code works under the hood
		+ think about memory: allocating memory

## Resources
+ https://youtu.be/tKbV6BpH-C8?si=AU9Nqp8TskevQpaI  - Premature Optimization