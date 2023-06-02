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
<mark style="background: transparent;">EF Core uses the infor in these entries to construct its SQL command</mark> <mark style="background: transparent;">![[Pasted image 20230526100742.png]]</mark>

**Updating Shadow Properties During SaveChanges**
Store data that's irrelevant to your business logic 
Row Created/update timestamp or user created/modified row
Useful for reports against the database such as auditing
Extraneous to business logic and would be in the way

<mark style="background: transparent;">Why Shadow Properties </mark><mark style="background: transparent;">![[Pasted image 20230526101409.png]]</mark>

<mark style="background: transparent;">Use SaveChanges & Shadow Properties to populate Audit Data</mark><mark style="background: transparent;">![[Pasted image 20230526101156.png]]</mark>

**Using EF Core Pipeline Events**

<mark style="background: transparent;">Event Exposed in EF Core API</mark><mark style="background: transparent;">![[Pasted image 20230526101640.png]]</mark>

**Implementing Event Handler**
A method to execute custom logic
Declare the method as a handler of the target event

<mark style="background: transparent;">Using SaveChanges & Properties to populate Audit Data</mark><mark style="background: transparent;">![[Pasted image 20230526101704.png]]![[Pasted image 20230526102029.png]]</mark>

<mark style="background: transparent;">Lifecycle of SaveChange Events</mark> <mark style="background: transparent;">![[Pasted image 20230526102122.png]]</mark>

You could use these events to emit alternate information that isn't tracked by the logger

**Using Interceptors to Inject Logic into EF Core's Pipeline**
EFCore interceptors enable interception, modification, and suppression of EFCore operations. This includes low-level database operations such as executing a command, as well as higher-level operations, such as calls to SaveChanges.

<mark style="background: transparent;">Intercepting Database Operations</mark><mark style="background: transparent;">![[Pasted image 20230526102649.png]]</mark>

<mark style="background: transparent;">Setting Up Interception</mark><mark style="background: transparent;">![[Pasted image 20230526102748.png]]</mark>

<mark style="background: transparent;">Implement SoftDelete</mark> <mark style="background: transparent;">![[Pasted image 20230526103009.png]]</mark>

