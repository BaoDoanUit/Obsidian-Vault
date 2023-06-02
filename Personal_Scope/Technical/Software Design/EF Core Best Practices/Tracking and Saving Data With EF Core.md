---
up: [[EF Core General]]
---

#### Summary
DbContext and Entity roles in tracking
Tracking and saving workflow
Inserting, updating and deleting objects
Tracking and saving multiple objects
Bulk operation support
How persistence differs in disconnected apps

##### Getting a better understand DbContext and Entity Tracking Components
<mark style="background: transparent;">Entity and the DbContext </mark><mark style="background: transparent;">![[Components_EF.png]]</mark>

<mark style="background: transparent;">Tracking and Saving Workflow</mark><mark style="background: transparent;">![[DbContext_Entities.png]]</mark>

<mark style="background: transparent;">Add from DbSet or DbContext</mark> <mark style="background: transparent;">![[Tracking_Workflow.png]] ![[EFCore-15.png]]</mark>

```ad-quote
When you call SaveChanges, the context will take one last look at the objects it's tracking
Roles of DbContext and entities when tracking and saving
Inserting, updating and deleting data
Explicit updates for untracked objects
Tracking and saving multiple objects with the Range method
Batching support
```
<mark style="background: transparent;">How DbContext Discovers About Changes</mark><mark style="background: transparent;">![[DbContext_Tracking_Changes.png]]</mark>

The entities are just plain objects and don't communicate their changes to the DbContext.
Updating Untracked Objects

<mark style="background: transparent;">Begin Tracking and Set State to Modified</mark><mark style="background: transparent;">![[EFCore_Tracking_and_set_state_to_Modified.png]]</mark>

<mark style="background: transparent;">Both of these get disposed at the end of the method that instantiated them - because of the "using"</mark><mark style="background: transparent;">![[EFCore-16.png]]</mark>

So, if the context is no longer exits, there is nothing tracking that author.
It's not tracking anything, it doesn't know anything about this author.

<mark style="background: transparent;">Which would think the author need to be inserted into the database. But this Update command is updating the LastName as well</mark><mark style="background: transparent;">![[Pasted image 20230518144054.png]]</mark>

<mark style="background: transparent;">The Update command has no way to know what got updated, so it tells the ChangeTracker that every field is modified</mark><mark style="background: transparent;">![[Pasted image 20230518144254.png]]</mark>

1) More Pointers for Disconnected Data
- Update is not typically needed when object is tracked
- Update adn Add and Remove are important for untracked objects.

2) Deleting May Seem a Little Weird
- Context needs to track to the entity
- Then you Delete )"Remove" the entity
- EF Core send relevant SQL to database on SaveChanges

<mark style="background: transparent;">Deleting without Querying for a Tracked Entity</mark><mark style="background: transparent;">![[Pasted image 20230518144906.png]]</mark>

##### Tracking Multiple Objects and Bulk Update

<mark style="background: transparent;">AddRange and other Range methods are for convienience only Tracking Multiple Entities</mark><mark style="background: transparent;">![[Pasted image 20230518145114.png]]</mark>

<mark style="background: transparent;">Combined EF Core + SQL Server Effort</mark><mark style="background: transparent;">![[Pasted image 20230518145235.png]]![[Pasted image 20230518145252.png]]</mark>

#### Controlling Database
```ad-quote
Overview of EF Core Migrations API
Workflow of how EF Core determines database schema
Where Migration API adn tool fit in
Used migration commnads to generate script
Reverse engineer existing database into classes and DbContext
```

<mark style="background: transparent;"></mark><mark style="background: transparent;">![[Pasted image 20230518145712.png]]
![[Pasted image 20230518145716.png]]
![[Pasted image 20230518145830.png]]</mark>
##### EF Core migrations are source-control friendly
<mark style="background: transparent;"></mark><mark style="background: transparent;">![[Pasted image 20230518150123.png]]
![[Pasted image 20230518150737.png]]
![[Pasted image 20230518150854.png]]
![[Pasted image 20230518150903.png]]
![[Pasted image 20230518150919.png]]
![[Pasted image 20230518150929.png]]
![[Pasted image 20230518151044.png]]
![[Pasted image 20230518151347.png]]
![[Pasted image 20230518151453.png]]
![[Pasted image 20230518151725.png]]</mark>

##### Reverse Engineering and Existing Database

<mark style="background: transparent;">Configuration One to many </mark><mark style="background: transparent;">![[Pasted image 20230518151753.png]]
![[Pasted image 20230518151759.png]]
![[Pasted image 20230518152058.png]]
![[Pasted image 20230518152205.png]]
![[Pasted image 20230518155241.png]]
![[Pasted image 20230518155252.png]]![[Pasted image 20230518155346.png]]![[Pasted image 20230518155529.png]]</mark>


<mark style="background: transparent;">Benefit from Foreign Key </mark> <mark style="background: transparent;">![[Pasted image 20230518155635.png]]![[Pasted image 20230518155721.png]]![[Pasted image 20230518155843.png]]</mark>

<mark style="background: transparent;">Mapping Unconvential FK</mark><mark style="background: transparent;">![[Pasted image 20230518160054.png]]</mark>

<mark style="background: transparent;">Allow Nullable</mark>
<mark style="background: transparent;">![[Pasted image 20230518160307.png]]</mark>

##### Logging EF Core Activity and SQL
EF Core extends .NET Logging
EF Core logs provide more than just SQL
You'll probaly want to use Simple Logging API(LogTo)

<mark style="background: transparent;">Customize and modifiled output log</mark><mark style="background: transparent;">![[Pasted image 20230518160528.png]]</mark>

<mark style="background: transparent;">Add logging </mark><mark style="background: transparent;">![[Pasted image 20230518160608.png]]</mark>

<mark style="background: transparent;">Filtering Log Output with Log Level</mark>
<mark style="background: transparent;">![[Pasted image 20230518160711.png]]
![[Pasted image 20230518160827.png]]
![[Pasted image 20230518160905.png]]</mark>

<mark style="background: transparent;">Even more Logging</mark>
<mark style="background: transparent;">![[Pasted image 20230518160948.png]]
![[Pasted image 20230518161008.png]]
![[Pasted image 20230518161038.png]]</mark>

<mark style="background: transparent;">Log Target Output</mark><mark style="background: transparent;">![[Pasted image 20230518161155.png]]</mark>

<mark style="background: transparent;">Interacting with Related Data </mark><mark style="background: transparent;">![[Pasted image 20230519084652.png]]</mark>

<mark style="background: transparent;">Graph Object</mark><mark style="background: transparent;"> ![[Pasted image 20230519084749.png]]</mark>

<mark style="background: transparent;">Change Tracker Response to New Child of Existing Parent</mark>
<mark style="background: transparent;">![[Pasted image 20230519084847.png]]
![[Pasted image 20230519084859.png]]
![[Pasted image 20230519084932.png]]
![[Pasted image 20230519084954.png]]
![[Pasted image 20230519085019.png]]
![[Pasted image 20230519085129.png]]
![[Pasted image 20230519085155.png]]
![[Pasted image 20230519085203.png]]</mark>

<mark style="background: transparent;">Eager Loading Related Data in Queries</mark>
<mark style="background: transparent;">![[Pasted image 20230519085215.png]]
![[Pasted image 20230519085307.png]]
![[Pasted image 20230519085318.png]]
![[Pasted image 20230519085505.png]]
![[Pasted image 20230519085548.png]]</mark>

<mark style="background: transparent;">Performance Issues</mark><mark style="background: transparent;">![[Pasted image 20230519085624.png]]![[Pasted image 20230519101817.png]]![[Pasted image 20230519101830.png]]</mark>

<mark style="background: transparent;">Only Track Entities Recognized by DbContext</mark><mark style="background: transparent;">![[Pasted image 20230519102018.png]]</mark>

<mark style="background: transparent;">Loading Related Data for Objects Already in Memory</mark>
<mark style="background: transparent;">![[Pasted image 20230519102131.png]]</mark>

<mark style="background: transparent;">Explicit Loading
DbContext.Entry(object).Collection().Load()
DbContext.Entry(object).Reference().Load()
</mark><mark style="background: transparent;">![[Pasted image 20230519102601.png]]
![[Pasted image 20230519103942.png]]</mark>

##### Use Lazing Loading to Retrieve 
<mark style="background: transparent;">Enable Lazy Loading</mark><mark style="background: transparent;">![[Pasted image 20230519104042.png]]</mark>

<mark style="background: transparent;">Good and not so good lazy loading</mark><mark style="background: transparent;">![[Pasted image 20230519104155.png]]</mark>

Use Related Data to Filter Objects

<mark style="background: transparent;">Modified Related Data</mark><mark style="background: transparent;">![[Pasted image 20230519104621.png]]
![[Pasted image 20230519104716.png]]
![[Pasted image 20230519104743.png]]
![[Pasted image 20230519104814.png]]
![[Pasted image 20230519104842.png]]
![[Pasted image 20230519104907.png]]</mark>

<mark style="background: transparent;">Reminder: DbContext/DbSet Tracking Methods</mark><mark style="background: transparent;">![[Pasted image 20230519104934.png]]</mark>

##### Challenges

<mark style="background: transparent;">DbContext.Entry gives you a lot of fine-grained control over the cahnge tracker</mark><mark style="background: transparent;">![[Pasted image 20230519105031.png]]</mark>

<mark style="background: transparent;">Understanding Deleting with Graphs</mark> <mark style="background: transparent;">![[Pasted image 20230519105210.png]]![[Pasted image 20230519105336.png]]</mark>

<mark style="background: transparent;">Using an EF Core method Add/Update/Remove/Attach will trigger DetectChanges</mark><mark style="background: transparent;">![[Pasted image 20230519105550.png]]</mark>

<mark style="background: transparent;">Questions</mark>
<mark style="background: transparent;">![[Pasted image 20230519105623.png]]
![[Pasted image 20230519105736.png]]</mark>
