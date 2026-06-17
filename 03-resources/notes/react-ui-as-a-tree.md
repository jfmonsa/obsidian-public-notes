---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
+ React uses tree structures to manage and model the relationship between components in a React app

## The Render Tree
+ The tree is composed of nodes, each of which represents a component
+ HTML tags are not part of the render tree, render tree is only composed of React components
+ Render trees help identify what the top-level and leaf components are. Top-level components affect the rendering performance of all components beneath them and leaf components are often re-rendered frequently. Identifying them is useful for understanding and debugging rendering performance.
+ With conditional rendering, the render tree may change across different renders. With different prop values, components may render different children components.
