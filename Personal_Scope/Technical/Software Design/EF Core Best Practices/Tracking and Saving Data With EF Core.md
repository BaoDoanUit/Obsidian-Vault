#### Summary
DbContext and Entity roles in tracking
Tracking and saving workflow
Inserting, updating and deleting objects
Tracking and saving multiple objects
Bulk operation support
How persistence differs in disconnected apps

##### Getting a better understand DbContext and Entity Tracking Components
Entity and the DbContext ![[Components_EF.png]]
Tracking and Saving Workflow![[DbContext_Entities.png]]
Add from DbSet or DbContext ![[Tracking_Workflow.png]] ![[EFCore-15.png]]

> [!quote]
When you call SaveChanges, the context will take one last look at the objects it's tracking
Roles of DbContext and entities when tracking and saving
Inserting, updating and deleting data
Explicit updates for untracked objects
Tracking and saving multiple objects with the Range method
Batching support
>

How DbContext Discovers About Changes![[DbContext_Tracking_Changes.png]]

The entities are just plain objects and don't communicate their changes to the DbContext.
Updating Untracked Objects

Begin Tracking and Set State to Modified![[EFCore_Tracking_and_set_state_to_Modified.png]]

Both of these get disposed at the end of the method that instantiated them - because of the "using"![[EFCore-16.png]]

So, if the context is no longer exits, there is nothing tracking that author.
It's not tracking anything, it doesn't know anything about this author.

Which would think the author need to be inserted into the database. But this Update command is updating the LastName as well![[Pasted image 20230518144054.png]]

The Update command has no way to know what got updated, so it tells the ChangeTracker that every field is modified![[Pasted image 20230518144254.png]]

1) More Pointers for Disconnected Data
- Update is not typically needed when object is tracked
- Update adn Add and Remove are important for untracked objects.

2) Deleting May Seem a Little Weird
- Context needs to track to the entity
- Then you Delete )"Remove" the entity
- EF Core send relevant SQL to database on SaveChanges

Deleting without Querying for a Tracked Entity![[Pasted image 20230518144906.png]]

##### Tracking Multiple Objects and Bulk Update

AddRange and other Range methods are for convienience only Tracking Multiple Entities![[Pasted image 20230518145114.png]]

Combined EF Core + SQL Server Effort![[Pasted image 20230518145235.png]]![[Pasted image 20230518145252.png]]

#### Controlling Database
> [!quote]
> Overview of EF Core Migrations API
> Workflow of how EF Core determines database schema
> Where Migration API adn tool fit in
> Used migration commnads to generate script
> Reverse engineer existing database into classes and DbContext

![[Pasted image 20230518145712.png]]
![[Pasted image 20230518145716.png]]
![[Pasted image 20230518145830.png]]
##### EF Core migrations are source-control friendly
![[Pasted image 20230518150123.png]]
![[Pasted image 20230518150737.png]]
![[Pasted image 20230518150854.png]]
![[Pasted image 20230518150903.png]]
![[Pasted image 20230518150919.png]]
![[Pasted image 20230518150929.png]]
![[Pasted image 20230518151044.png]]
![[Pasted image 20230518151347.png]]
![[Pasted image 20230518151453.png]]
![[Pasted image 20230518151725.png]]

##### Reverse Engineering and Existing Database

Configuration One to many ![[Pasted image 20230518151753.png]]
![[Pasted image 20230518151759.png]]
![[Pasted image 20230518152058.png]]
![[Pasted image 20230518152205.png]]
![[Pasted image 20230518155241.png]]
![[Pasted image 20230518155252.png]]![[Pasted image 20230518155346.png]]![[Pasted image 20230518155529.png]]


Benefit from Foreign Key  ![[Pasted image 20230518155635.png]]![[Pasted image 20230518155721.png]]![[Pasted image 20230518155843.png]]

Mapping Unconvential FK![[Pasted image 20230518160054.png]]

Allow Nullable
![[Pasted image 20230518160307.png]]

##### Logging EF Core Activity and SQL
EF Core extends .NET Logging
EF Core logs provide more than just SQL
You'll probaly want to use Simple Logging API(LogTo)

Customize and modifiled output log![[Pasted image 20230518160528.png]]

Add logging ![[Pasted image 20230518160608.png]]

Filtering Log Output with Log Level
![[Pasted image 20230518160711.png]]
![[Pasted image 20230518160827.png]]
![[Pasted image 20230518160905.png]]

Even more Logging
![[Pasted image 20230518160948.png]]
![[Pasted image 20230518161008.png]]
![[Pasted image 20230518161038.png]]

Log Target Output![[Pasted image 20230518161155.png]]

Interacting with Related Data ![[Pasted image 20230519084652.png]]

Graph Object ![[Pasted image 20230519084749.png]]

Change Tracker Response to New Child of Existing Parent
![[Pasted image 20230519084847.png]]
![[Pasted image 20230519084859.png]]
![[Pasted image 20230519084932.png]]
![[Pasted image 20230519084954.png]]
![[Pasted image 20230519085019.png]]
![[Pasted image 20230519085129.png]]
![[Pasted image 20230519085155.png]]
![[Pasted image 20230519085203.png]]

Eager Loading Related Data in Queries
![[Pasted image 20230519085215.png]]
![[Pasted image 20230519085307.png]]
![[Pasted image 20230519085318.png]]
![[Pasted image 20230519085505.png]]
![[Pasted image 20230519085548.png]]

Performance Issues![[Pasted image 20230519085624.png]]![[Pasted image 20230519101817.png]]![[Pasted image 20230519101830.png]]

Only Track Entities Recognized by DbContext![[Pasted image 20230519102018.png]]

Loading Related Data for Objects Already in Memory
![[Pasted image 20230519102131.png]]

Explicit Loading
DbContext.Entry(object).Collection().Load()
DbContext.Entry(object).Reference().Load()
![[Pasted image 20230519102601.png]]
![[Pasted image 20230519103942.png]]

##### Use Lazing Loading to Retrieve 
Enable Lazy Loading![[Pasted image 20230519104042.png]]

Good and not so good lazy loading![[Pasted image 20230519104155.png]]

Use Related Data to Filter Objects

Modified Related Data![[Pasted image 20230519104621.png]]
![[Pasted image 20230519104716.png]]
![[Pasted image 20230519104743.png]]
![[Pasted image 20230519104814.png]]
![[Pasted image 20230519104842.png]]
![[Pasted image 20230519104907.png]]

Reminder: DbContext/DbSet Tracking Methods![[Pasted image 20230519104934.png]]

##### Challenges

DbContext.Entry gives you a lot of fine-grained control over the cahnge tracker![[Pasted image 20230519105031.png]]

Understanding Deleting with Graphs ![[Pasted image 20230519105210.png]]![[Pasted image 20230519105336.png]]

Using an EF Core method Add/Update/Remove/Attach will trigger DetectChanges![[Pasted image 20230519105550.png]]

Questions
![[Pasted image 20230519105623.png]]
![[Pasted image 20230519105736.png]]
