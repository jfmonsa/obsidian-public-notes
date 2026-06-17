---
mocs:
    - "[[public-notes/03-resources/system-design.moc.md|System Design]]"
tags:
    - dev/system-design
---

+ Created by Facebook
+ A Query Language for APIs and a runtime for executing those queries on your existing data
+ Allow clients to request exactly the data that they need, solving **over-fetching**
+ Make APIs more flexible
+ All interactions occurs over a single endpoint
+ strongly typed
+ also support mutations and subscriptions
---
**Concepts**
+ Types: Define the existing data
+ Queries: how to retrieve that data
+ Mutation:
+ Resolvers
---
**Pros**
+ Resolvers over-fetching, different endpoints
**Cons**
+ Needs tooling on frontend (apollo) and server side
+ more difficutl to cache
	+ while REST is handled by: CDNs proxies, webservers...
	+ Graphql has single point of entry which prevent full use of caching
+ Danger 
**Not that clear**
+ N+1 queries ?

## Schemas
basic schema:

Frontend
```json
schema {
	query: Query
	mutation: Mutation
}

// used for fetching / reading
type Query {
	getAllUsers: [User]!
	getUser(id: ID!)
}

// used for creating / updating / deleting
type Mutation {
	createUser(input: CreateUserInput): User
	updateUser(input: UpdateUserInput): User
	deleteUser(input: DeleteUserInput): User
}

type User {
	id: ID!
	firstName: String
	lastName: String
	email: String
	age: Int
	job: Job
}

type Job {
	id: ID!
	company: String
	position: String
	salary: Int
}

input CreateUserInput {
	firstName: String!
	lastName: String!
	email: String!
	age: Int!
	job: Job!
}
```

Backend
+ You have to write the resolvers on backend
```json
Mutation {
	createuser: (parent, args, context, info) => {
		
	}
}
```
