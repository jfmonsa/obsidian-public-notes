---
mocs:
    - "[[public-notes/03-resources/tools.moc.md|Tools & Environment]]"
tags:
    - dev/tools
---

+ Learn vim motions before using vim as editor
+ Motion is anything that move the cursor 
## Modes
+ Normal mode
+ Insert mode: i, a, A, o
+ Visual mode
+ Command mode `:` e.g. `:wq!`

## Motions
+ h,j,k,l
+ w, b
## Commands + count + motions
+ d, dd, d3j, db
+ u
+ ctrl + r

## Visual mode
+ v to enter in
	+ `shif + v` to visual line mode
### Copy and paste
+ y to copy something selected
You don't need to select something, you can also do this in normal mode:
+ yy - copy the whole current line
+ y5jp - copy and paste the last 5 lines
+ p to paste, you can paste over a highlighted region
+ if you p over something (a selected region) if you press p again you'll have what you deleted in the previous p

> [!NOTE]
> Copy and delete share the same buffer, when you delete something it is save in the buffer