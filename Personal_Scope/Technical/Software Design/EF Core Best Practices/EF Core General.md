##### Summary
[[EF Core Relationship]]
[[EF vs Views and Stored Procedure and Raw SQL]]
[[Using EF with Net Core Apps]]
[[Using EF Core in your tests]]
[[Tapping into EF Core's Pipeline]]

##### EF Core began as an ORM (Object Relational Mapper)
High Level ORM Benefit/ Developer productivity

Coding consistency![[EFCore-1.png]]

##### Summary Project
Publisher of Solo Author Book
Using EF Core to Query a Db

##### EF query workflow
(1)Express and execute query -> (2)EF Core reads model, works with provider to work out SQL -> (3)Send SQL DB -> (4)Receives tabular results -> (5)Materializes results as objects -> (6)Add tracking details to DbContext instance

Query Workflow![[Query Workflow]]

Two Ways to Express LINQ Queries
LINQ Method (context.Authors.ToList())
LINQ Operator ((from a in context.Authors select a).ToList())
Should choose LINQ Method

##### Basics of querying EF Core and Linq

Don't define the query variable via Enumeration for read the data  ![[EFCore-2.png]]

To get the variable if manipulate data. ![[EFCore-3.png]]

##### Filtering, sorting and aggregating in queries

Filtering Partial Text in Queries ![[EFCore-4.png]]

1) Finding an Entity Using its Key Value
- DbSet.Find(keyvalue)
- This is the only task that Find can be used fo
	- Not a LINQ method
	- Executes immediately
	- If key is found in change tracker, avoids unneeded database query
2) Skip and Take for Paging
- Skip(0).Take(10) -- Get First 10 rows
- Skip(10).Take(10) -- Get Next 10 rows

Example: ![[EFCore-5.png]]

Sorting ![[EFCore-9.png]]

Wrong Example ![[EFCore-6.png]]

##### Aggregating Results in Queries
First() - FirstAsync()
FirstOrDefault()  - FirstOrDefaultAsync()
Single() - SingleAsync()
SingleOrDefault() - SingleOrDefaultAsync()
Last() - LastAsync()
LastOrDefault() - LastOrDefaultAsync()
Count() - CountAsync()
LongCount() - LongCountAsync()
Min(), Max()
Average(), Sum()

No Aggregation: ToList(),AsEnumerable() ![[EFCore-11.png]]

Explore the SQL queries that EF Core is building to you
Improve query performance by deactivating tracking when not needed.

Enhancing Query Performance When tracking is needed  ![[EFCore-13.png]]

| Name | Age | Sex |
| ---- | --- | --- |
| Bao  | 10  | Male    |
