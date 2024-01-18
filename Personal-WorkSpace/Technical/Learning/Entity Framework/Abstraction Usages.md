## How to use abstraction in EF 6
Generate some abstraction in the code
Feedback for new coming

Both generic and non-generic versions of the repository may exist at the same time

No need to wonder which form the repository exist
Helps to explicitly enumerable all repository

![[../../../../Gallery/Screen Shot 2023-10-07 at 15.02.28.png]]

Both approaches are valid in different situations
- Repository is an abstraction that builds upon DbSet
- All abstractions must contain complexity
- No complexity - no need for a custom repository

Repository usage example
- Used plain DbSet to retrieve a student
- Introduced StudentRepository to abstract the retriveval logic
- Used EF Core 6's auto-including feature and switched back to the plain DbSet
- New sport enrollment collection; had to use the repository again
- Use repositories to abstract persistence logic

#### Avoiding Common Anti-Patterns that Break Encapsulating

Common Anti-patterns:
- Partially-initialized entities
- Cust unit of work

##### Partially-initialized Entities Anti-pattern
Retrieving only a part of an entity
- Breach of encapsulation

Aggregates in Our Project
![[../../../../Gallery/Screen Shot 2023-10-07 at 15.12.11.png]]

Performance Implications of Loading Entitites in Full
- Performance impact: Does loading of related data slow the application down?
- Where to stop: What if the related data has related data of its own?
![[../../../../Gallery/Screen Shot 2023-10-07 at 15.17.29.png]]
Stop at aggregate boundaries
![[../../../../Gallery/Screen Shot 2023-10-07 at 15.18.04.png]]
Restrict the loading to aggregate boundaries if Coures and Sports become more complex

Use Lazy Loading
- Can use navigation properties for all relationship

Loading aggregates in-full does lead to performance drawbacks

Tackling Performance Implications in Reads
- Read-write mismatch
- Modify the student : Enroll & EditPersonalInfo
- Read the student 
![[../../../../Gallery/Screen Shot 2023-10-07 at 15.28.46.png]]
![[../../../../Gallery/Screen Shot 2023-10-07 at 23.01.18.png]]


Custom Unit of Work Class
- Not necessarily an anti-pattern
- Still a red flag

![[../../../../Gallery/Screen Shot 2023-10-07 at 23.08.19.png]]
![[../../../../Gallery/Screen Shot 2023-10-07 at 23.09.34.png]]

Repositories know about UoW
UoW doesn't know about repositories

![[../../../../Gallery/Screen Shot 2023-10-07 at 23.10.29.png]]
![[../../../../Gallery/Screen Shot 2023-10-07 at 23.13.56.png]]
![[../../../../Gallery/Screen Shot 2023-10-07 at 23.17.12.png]]

Not execute condition below  
![[../../../../Gallery/Screen Shot 2023-10-07 at 23.18.04.png]]
![[../../../../Gallery/Screen Shot 2023-10-07 at 23.19.58.png]]

Don't use IQueryable as part of the public API
- Can still use it intenally
- Leaky abstraction


IEnumerable and Lazy Evaluation

![[../../../../Gallery/Screen Shot 2023-10-15 at 22.07.10.png]]