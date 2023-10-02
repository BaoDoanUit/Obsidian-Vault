#### Summary
Advance query operators
Asynchronous queries
Temporal tables
Stored procedures
Optimizing query performance

##### Advance query operators
1) AsNoTracking
- No tracking information stored
- Improves performance
- Use if not updating entities
- Tracking can be enabled later

Select Many![[Pasted image 20230529152321.png]] ![[Pasted image 20230529152945.png]]

Group By![[Pasted image 20230529153039.png]]

If something can't be executed on the database, our choice is often between accepting degraded performance or rewriting our query

Group Join ![[Pasted image 20230529154400.png]] ![[Pasted image 20230529155530.png]]

![[Pasted image 20230529161242.png]]

> [!quote]
> Asynchronous programing does not make the individual task run faster, but instead allow more than one thing to take place at the same time.

Temporal Tables in the IDE ![[Pasted image 20230529173637.png]] ![[Pasted image 20230529173802.png]]

Configurable Temporable ![[Pasted image 20230529173904.png]]