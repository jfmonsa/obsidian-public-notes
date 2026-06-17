---
mocs:
    - "[[public-notes/03-resources/backend.moc.md|Backend]]"
tags:
    - dev/backend
---



![[Pasted image 20240826233806.png]]

# 1. Session-based Authetication
2. To keep the user looged, you have to have db table named sessions and map users with its user id
3. you stored in sessions the temprary `sessionId`
4. you send the `sessionId` to the web site or app and every time they make a api request you know who the user is

![[Pasted image 20240826222304.png]]
**Benefits**:
+ You can revoke any access any-time by deleting the session in the data base
**Cons**
+ For every time the user makes an api request you have to make a db retrieval just to see who the user is
	+ One solution to this is instead of using a db table to store sessions you can use something like redis 
# 2. [[jwt-authentication]] (Recommended)

# Resources
1. How to Roll Your Own Auth - https://youtu.be/CcrgG5MjGOk?si=Rei36szUSnh097GG (This video is ultra-amazing)
