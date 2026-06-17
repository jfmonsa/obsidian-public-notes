---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
---

## Trade-offs in DB Design
![[Pasted image 20250619123059.png]]
![[Pasted image 20250619124130.png]]

## Trade-offs in Transactions
- One transaction might read data that another is about to update. 
- Two users might try to reserve the same inventory slot. 
- A background job might lock a record moments before a customer clicks "Confirm." 
Such scenarios can result in conflicts, race conditions, and deadlocks that stall the system entirely.
# Notes
## 1 -  [[relational-data-bases]]
+ SQL, Relational DB Design, indexes, etc.

# Firebase
+ auth
+ databases
+ file storage
+ security rules
+ analytics


# Mongo DB
## Data Modeling
+ The key idea of MongoDB is to identify your access (query) patterns **then** design data model to support it
+ ==Data access together shoud be stored together==
---
+ entities stored in documents and collections
+ JSON-like format
---
+ Polymorphism: store documents with different structures or fields within the same collection
+ Embedding: store documents with other documents (sub-documents)
+ Normalize data: referencing other documents from a main document

---
+ Schema validation: Defines rules and constraints
+ Executed on the database layer
---
**For modelling**
+ Identify entities
+ Identify read and write operations and what entities are involved for business needs (functional requirements)
	+ quantify on-average read and writes operations
---
### Use referencing or embedding

Relationship should be implemente using one of these strategies
+ **Reference**: Separate doucments linked using a key
+ **Embbeding**: subdocuments / things stored in the same document:
	+ ==Data access together shoud be stored together==


##### Guidelines to decide if embed or reference
 https://learn.mongodb.com/learn/course/relational-to-document-model/relational-to-document-model/design-relationships?page=2
+ simplicity? is more simple to store both entities together? -> If yes embed
+ are the same documents updated together?
+ are the same documents written at a different times in write-heavy workload?
+ Document size? would the combined size of the piece of information take too much memory or transfer bandwidth? If not -> embed
+ Document Growth? If we embend would the document possibly growth without boundary? If not -> embed
+ Individuality? For the child side of the relationship can the parent pieces exist by themselves without a parent? If not -> embed (e.g an author could not exits in the app without a book)
+ query atomicity? both entities are query together?
+ Data duplication would be very difficult to manage?

> [!IMPORTANT]
> if there is a possibility of and un-bounded array in a document then avoid embeddings

## Implementation of relationships

### One-to-one relationships
two strategies:

**1. Embed**
1. embed the as a subdocument
```json
// publishers
{
	"name": "Publisher Inc."
	// embedded sub-document
	"headquarters": {
		"zip": 23402948,
		"street": "St bla bla"
	}
}
```

**2. Reference**
1. a has a reference to b
2. b has a reference to a
3. bi-directional reference
Choose depending of access-patterns of your app

### One-to-many relationship

Two strategies
**1. embed**
1. embed the "many" side as an array of sub-documents in the "one" side (prefered)
2. create a sub-document within the parent document
```json
{
"books": {
	// sub-document for the many side
	"reviews": {
		"user-123": {
			"rating": 3.0,
			"content": "Mid book"
		},
		"user-236": {
			"rating": 4.0,
			"content": "dfajfal jfadl"
		},
		// ....
	}
}
```

**2. references**
(Use this if the array is un-bounded or very-large)

1. Use an array of references (ids) within the parent document 
2. bi-directional references

### Many-to-Many relationship

**1. embed**
1. embed the document in the parent side, this means duplicate for each new parent -> **Data duplication**
![[Pasted image 20250622225429.png]]
duplication is a matter of trade-offs   


 **2. Reference**
 + array of references 
+ Don't use bi-directional references

## Validate Schemas
+ Validations rules
+ Validations levels
+ validations actions
---
+ Ensures there are no un-intented or mal-formed fields once you know your schema
+ is a contract
---
+ Validations rules are implemented using $jsonSchema standard
+ there are two options when define schema validation rules, validation level options:
	+ strict
	+ moderated: only apply rules for new documents


# SQL Performance
Good question. If you already know basic SQL + joins, you are close.  
Use this **practical learning route** (4–6 weeks) to avoid “server-blowup” queries.

## 1) SQL fundamentals for performance (Week 1)

Focus only on what affects memory/rows:

- Join cardinality: `1:1`, `1:N`, `N:M`
- Why `N:M + N:M + N:M` in one query causes row multiplication
- `GROUP BY`, `COUNT`, `EXISTS` vs `IN`
- Pagination (`LIMIT/OFFSET`, keyset basics)
- Index basics (PK, FK, composite index order)

Practice:

- Predict row count before running query.
- Then run and compare prediction.

## 2) Query plan reading (Week 2)

Learn to use `EXPLAIN` / `EXPLAIN ANALYZE` (or MySQL equivalent):

- Detect full table scans
- Detect bad join order
- Detect huge intermediate row counts
- Detect missing indexes

Goal:

- For every non-trivial query, read plan once before merge.

## 3) ORM-to-SQL mapping (Sequelize) (Week 3)

You must know how Sequelize generates SQL:

- [include](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html) eager loading
- `belongsToMany` and through-table joins
- `separate: true` (**only HasMany**)
- [required](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html), `duplicating`, `subQuery` behavior
- Lazy loading (`instance.getX()`) when safer than mega-join

Sequelize docs:

- Eager loading:  
    [https://sequelize.org/docs/v6/advanced-association-concepts/eager-loading/](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
- Separate queries:  
    [https://sequelize.org/docs/v6/advanced-association-concepts/eager-loading/#separate-queries](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
- Associations:  
    [https://sequelize.org/docs/v6/core-concepts/assocs/](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html)

## 4) Production safety habits (Week 4)

Before shipping any endpoint:

1. Estimate cardinality:
    - “max parents × max children per include”
2. Log generated SQL locally.
3. Run query against realistic data volume.
4. Measure:
    - query time
    - returned row count
    - response payload size
5. Check memory during endpoint execution.

If include has multiple to-many relations, default to:

- Base entity query + separate child queries (like your current fix), or
- Controlled pagination per child relation.

## 5) PR checklist you can copy

Use this in every backend PR:

- [ ]  Any [include](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html) with more than one to-many relation?
- [ ]  Estimated worst-case row multiplication documented?
- [ ]  Query plan checked?
- [ ]  Proper indexes on join/filter columns?
- [ ]  Response payload size tested with realistic data?
- [ ]  Pagination / limits applied where needed?
- [ ]  Fallback strategy (split query) considered?

## 6) Fast mental rule

If one query joins:

- parent
- plus 2+ collections (`hasMany` / `belongsToMany`)

Assume danger until proven otherwise.


## Sequelize Query Safety Cheat Sheet (for your API)

### 1) Red flags (stop and review)

- [include](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html) with **2+ to-many** relations (`hasMany` / `belongsToMany`) in one query.
- Nested includes with to-many at multiple levels.
- No `limit`/pagination on list endpoints.
- Returning full model attributes by default.
- `findAll` used when endpoint returns one item.

---

### 2) Cardinality quick test (30 seconds)

Before merge, estimate worst-case rows:

`base_rows × childA_avg × childB_avg × childC_avg`

If result is large, split query.

Example: `1 application × 20 languages × 30 skills × 10 courses = 6000 rows` duplicated in SQL result.

---

### 3) Safe include strategy

- Keep main query to:
    - base record
    - `belongsTo` / `hasOne` includes
    - minimal attributes
- Load heavy to-many relations separately (`instance.getX()`), then attach.

Your current endpoint follows this pattern correctly for:

- [job.getLanguages(...)](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
- [job.getCourses(...)](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
- [job.getSkills(...)](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html)

---

### 4) `separate: true` rule

- ✅ Use on `hasMany`
- ❌ Do **not** use on `belongsToMany` (throws error)

---

### 5) Attribute discipline

Always whitelist:

- model [attributes: [...]](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
- join-table fields only when needed ([joinTableAttributes](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html))

Avoid returning unneeded text/blob/json columns.

---

### 6) Existence/count patterns

Prefer:

- `EXISTS (...)` for boolean flags (`isFavorite`)
- Aggregation/count in subquery for counters (`unreadMessagesCount`)

Avoid joining large tables only to compute booleans/counters.

---

### 7) Pagination defaults (list endpoints)

- Always set `limit`
- Add deterministic `order`
- Add filters on indexed columns
- Consider keyset pagination for large datasets

---

### 8) Index sanity checks

Ensure indexes on:

- FK columns used in joins (`jobId`, [userId](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html), `chatRoomId`, etc.)
- Common filter columns
- Composite indexes matching query filters ([(userId, jobId)](vscode-file://vscode-app/opt/visual-studio-code/resources/app/out/vs/code/electron-browser/workbench/workbench.html) where relevant)

---

### 9) PR performance checklist

- [ ]  Any multi-to-many include?
- [ ]  Estimated worst-case row multiplication?
- [ ]  Generated SQL reviewed?
- [ ]  Query plan checked (`EXPLAIN`)?
- [ ]  Response payload size measured?
- [ ]  Memory behavior tested with realistic data?
- [ ]  Split-query fallback considered?

---

### 10) One-line rule

If query joins one entity with multiple collections, assume it is unsafe until proven with row estimates and test data.