---
mocs:
    - "[[public-notes/03-resources/simulation.moc.md|Computational Simulation]]"
tags:
    - cs/simulation
---

+ Discrete-event simulation (DES) is a modeling technique used to simulate the operation of a **system as a sequence of individual events in time**.
+ Each event occurs at a specific **instant** and marks a **change of state in the system**.
+ DES is widely used in fields such as operations research, manufacturing, computer networks, and logistics to analyze complex systems' behavior and performance.

Key concepts in discrete-event simulation include:
- **Events**: Discrete occurrences that change the state of the system.
- **State Variables**: Variables that represent the state of the system at any given time. (discrete values). depends on time, (Queues)
- **Event List**: A list of all events scheduled to occur, ordered by the time of occurrence.
- **Clock**: Tracks the current simulation time.
- **Simulation Run**: The process of executing the simulation model over time to observe the system's behavior.
- **Actividad**: ?

---
+ **SimPy** is a process-based discrete-event simulation framework based on standard Python.