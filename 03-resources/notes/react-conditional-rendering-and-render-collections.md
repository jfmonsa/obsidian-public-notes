---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
## 5. Conditional Rendering
+ avoid nesting (guard clauses: return null, skeletons, loaders, etc.)
+ `? :` , `&&`, or `if`
## 6. Loops: (Render a collection of Items)
+ `map()`, `filter()` for structured data
### Key prop
+  ==don't use index from map, you should include them in your data== or use crypto.randomUUID()
+ Key must be unique among siblings

> [!WARNING]
> You might be tempted to use an item’s index in the array as its key. In fact, that’s what React will use if you don’t specify a `key` at all. But the order in which you render items will change over time if an item is inserted, deleted, or if the array gets reordered. Index as a key often leads to subtle and confusing bugs.

> [!WARNING]
> Similarly, do not generate keys on the fly, e.g. with `key={Math.random()}`. This will cause keys to never match up between renders, leading to all your components and DOM being recreated every time. Not only is this slow, but it will also lose any user input inside the list items. Instead, use a stable ID based on the data.
