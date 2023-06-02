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

<mark style="background: transparent;">Select Many</mark><mark style="background: transparent;">![[Pasted image 20230529152321.png]] ![[Pasted image 20230529152945.png]]</mark>

<mark style="background: transparent;">Group By</mark><mark style="background: transparent;">![[Pasted image 20230529153039.png]]</mark>

If something can't be executed on the database, our choice is often between accepting degraded performance or rewriting our query

<mark style="background: transparent;">Group Join</mark> <mark style="background: transparent;">![[Pasted image 20230529154400.png]] ![[Pasted image 20230529155530.png]]</mark>

![[Pasted image 20230529161242.png]]

```ad-quote
Asynchronous programing does not make the individual task run faster, but instead allow more than one thing to take place at the same time.
```

<mark style="background: transparent;">Temporal Tables in the IDE</mark> <mark style="background: transparent;">![[Pasted image 20230529173637.png]] ![[Pasted image 20230529173802.png]]</mark>

<mark style="background: transparent;">Configurable Temporable</mark> <mark style="background: transparent;">![[Pasted image 20230529173904.png]]</mark>