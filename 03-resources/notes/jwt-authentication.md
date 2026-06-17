---
mocs:
    - "[[public-notes/03-resources/backend.moc.md|Backend]]"
tags:
    - dev/backend
---

## What is JWT?
It's a special type of token that is created with three inputs:
	1. Payload: Data you want to store
	2. JWT_SECRET (criptographically sign the token)
	3. expiration date
## Validation

+ Any data in a JWT is public, anyone can decode it: jwt.io even if they dont have the secret string
+ Validation it's the reason to sign the token
---
+ use the JWT_SECRET to validate you made the token
+ part of validation is making sure the token is not expired
+ It's convenient to don't have to make a db call every time you want to validate the token (==solving session auth problem==)

## Problems of JWT
**You can't invalidate token early...**
+ but the downside it's you can't invalidate that token early if you want to.
+ For exmpale: If you have a button that the user can press to logout in all devices, you need to terminate tokens early to implement that 

**A trick to overcome this problem...** **Second token: Refresh token**
+ It's having your JWT short-lived: eg 1h, 5min, depending on your needs (short-lived = refresh token)
+ Refresh (short-lived) + access (long-lived)
![[Pasted image 20240826225014.png]]
1. When user logs-in: create two tokens (access + refresh) and track refresh tokens in-memory (array, map, or db (redis, relational db))
2. When a request is made, check if refresh token is the collection of tokens you're tracking in the server, if yes, then verify both tokens, if all is correct sign a new access token and keep going
3. Always remove refresh token from the collection whenever user logs-out

**Auth management across multiple devices from the same user**
+ Store a refresh token version in session (or tokens) (related to userId in users table) table in db and whenever you create a refereshToken save it there
+ each time access token gets invalid, the server will check the user version with the version stored in the db, if is valid, the it will create a new access token and keep going
![[Pasted image 20240826230013.png]]

+ But when the user presses the logout button in all devices, you increment the referesh token version field and inmediatly all tokens get invalidated
![[Pasted image 20240826230419.png]]

# Frontend side auth: Save auth data in client
+ Whether you use sessions or jwts you still need to decide wheter you want to store it on the client, to keep them logged-in

+ solution its simple, you make an api call to your server every time the user comes to your website every time the user comes to your website and you ==let the server decide who the user is==

## React native
+ use secure storage

## Browsers
+ You have to decide between **cookies** or **local storage** 

**Cookies trick...**
+ If set ==credentials to true== whenever you make a fetch requests from the client the browser will automatically send any cookies stored on that domain up to the server without needing to send an auth header or anything 
+ It can get tricky if you're using cookies instead of local storage and you have property (you should) `httpOnly: true` that means you cannot access your cookies through javascript, only send it to  the server
**Local storage**
+ If you use local storage you have to set the auth header by yourself (usign and interceptor e.g with axios to set Bearer header)


![[Pasted image 20240826233449.png]]

+ Server will read the cookie (if there is one) and the it wil validate it and return your data, if there is not user the server will reply with null and usually redirect them back to Home screm

![[Pasted image 20240827215933.png]]

And in frontend
![[Pasted image 20240827220318.png]]

# References
+ https://stackabuse.com/authentication-and-authorization-with-jwts-in-express-js/