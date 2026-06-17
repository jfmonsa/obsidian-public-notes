---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
---

# Naming Conventions for SQL
1. Singular names for tables
2. Singular names for columns
3. Pascal casing (en postgrest usar mayusculas)

5. **Column Naming**: Use snake_case in PostgreSQL. In JS when you see non-conventional names you know you are dealing with implementation details of the database instead of abstractions. If you want to explicitly separate database and JS models then you'd map the snake_case names onto the camelCase ones and have a clean, obvious, and mostly enforced separation. Though how easy your frameworks make doing this I have no clue. But viewing a writing SQL directly ends up being such a large part of how I operate I would rather live with having unconventional snake_case in JS and clean SQL.
6. Name your **primary keys** using "singularOfTableNameID"
7. **foreign keys _must_ be named consistently** in different tables
8. Fields representing the same kind of data on different tables _should_ be named the same. Don't have Zip on one table and ZipCode on another.
9. Don't artifically shorten or abbreviate words. It is better for a name to be long and clear than short and confusing. Ultra-short names is a holdover from darker, more savage times. Cus_AddRef. What on earth is that? Custodial Addressee Reference? Customer Additional Refund? Custom Address Referral?
## Resources
 + https://stackoverflow.com/questions/7662/database-table-and-column-naming-conventions
 + https://brainstation.io/learn/sql/naming-conventions
 + https://www.reddit.com/r/SQL/comments/1cgszi7/camel_vs_snake_case_db_column_and_variable_naming/
 + https://wiki.postgresql.org/wiki/Don't_Do_This#Don.27t_use_upper_case_table_or_column_names
 + https://courses.cs.washington.edu/courses/cse154/18sp/18sp-data/documents/styleguide/sql/naming-conventions-sql.html
 + https://stackoverflow.com/questions/2878248/postgresql-naming-conventions
