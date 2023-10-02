---
up: [[EF Core General]]
---
**Summary**
SaveChanges Method is Virtual
You can override SaveChanges in your DbContext class
Add logic just before or just after EF Core call SaveChanges internally
Accessing the ChangeTracker EntityEntries
```C#
DbContext.ChangeTracker.Entries().ToList();
```
EF Core uses the infor in these entries to construct its SQL command ![[Pasted image 20230526100742.png]]

**Updating Shadow Properties During SaveChanges**
Store data that's irrelevant to your business logic
Row Created/update timestamp or user created/modified row
Useful for reports against the database such as auditing
Extraneous to business logic and would be in the way

Why Shadow Properties ![[Pasted image 20230526101409.png]]

Use SaveChanges & Shadow Properties to populate Audit Data![[Pasted image 20230526101156.png]]

**Using EF Core Pipeline Events**

Event Exposed in EF Core API![[Pasted image 20230526101640.png]]

**Implementing Event Handler**
A method to execute custom logic
Declare the method as a handler of the target event

Using SaveChanges & Properties to populate Audit Data![[Pasted image 20230526101704.png]]![[Pasted image 20230526102029.png]]

Lifecycle of SaveChange Events ![[Pasted image 20230526102122.png]]

You could use these events to emit alternate information that isn't tracked by the logger

**Using Interceptors to Inject Logic into EF Core's Pipeline**
EFCore interceptors enable interception, modification, and suppression of EFCore operations. This includes low-level database operations such as executing a command, as well as higher-level operations, such as calls to SaveChanges.

Intercepting Database Operations![[Pasted image 20230526102649.png]]

Setting Up Interception![[Pasted image 20230526102748.png]]

Implement SoftDelete ![[Pasted image 20230526103009.png]]

