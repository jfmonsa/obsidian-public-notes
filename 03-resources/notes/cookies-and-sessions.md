---
mocs:
    - "[[public-notes/03-resources/backend.moc.md|Backend]]"
tags:
    - dev/backend
---


**Why we need them?**
+ API REST is design to be stateless
+ Each request from our browser is treated as an entirely new interaction with no memory of previous requests
# Cookies
+ Are tiny data files that web servers ask web browsers to store on user's browser
+ Whenever the browser fetches an endpoint it sends these cookies back to the server to memorize certain bits of information, like:
	+ store user's preferences
	+ tracking user's browsing patterns
	+ store auth info
	
**The structure of a cookie**
1. name
2. value
3. expires
4. path
5. domain
6. secure
7. HttpOnly: prevent client-side scripts from accessing this cookie, which can help protect against cross-site scripting attacks.

# Sessions
+ Are like temporal Ids
+ It's a way to keep track of your visit to server assist you

It works by:
1. When you first visit a website, the server gives you a unique session ID, which is stored in a cookie on your browser.
2. With every request you make to the server (clicking links, submitting forms, etc.), your browser sends back that session cookie, reminding the server who you are. The server uses this ID to retrieve your session data from its memory or database.
3. This session data can store anything from what items you've added to a shopping cart to whether you're logged in.
4. When you log out, close your browser, or after a period of inactivity, the session ends. 
# Resources
1. https://dev.to/m__mdy__m/understanding-cookies-and-sessions-in-nodejs-3449