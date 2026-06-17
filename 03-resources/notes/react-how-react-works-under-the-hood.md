---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
## Virtual DOM
+ When the app first loads the **virtual DOM** is created, which is a tree representing the **DOM**
+ Then the **Rendering environment** render required nodes (A set of DOM operation which prioritizes the urgent of each node)
+ When a change occurs it creates a new tree called **work-in-progress**
+ The the diff between the current **virtual DOM tree** and the **work-in-progress tree** is calculated, this difference is rendered by the **Rendering environment**
+ Also the **work-in-progress tree** becomes the **current tree**
## References
+ https://www.youtube.com/watch?v=5XnU2cvgw5o
