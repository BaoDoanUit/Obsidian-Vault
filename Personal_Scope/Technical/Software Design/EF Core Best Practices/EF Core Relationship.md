##### Many to Many Relationship
![[Pasted image 20230519110044.png]] ![[Pasted image 20230519110155.png]]

Joining Objects in New Many-to-Many Relationships ![[Pasted image 20230519120452.png]]![[Pasted image 20230519120116.png]]![[Pasted image 20230519120216.png]]![[Pasted image 20230519120203.png]]![[Pasted image 20230519120313.png]]

Querying Across Many-to-Many![[Pasted image 20230519120607.png]]![[Pasted image 20230519120620.png]]![[Pasted image 20230519120629.png]]

1) Understanding and benefit from curcular references in Graph
- This happens with all relationships, not just many-to-many
- We Keep Pointing to the Same Objects

![[Pasted image 20230519121008.png]]![[Pasted image 20230519121033.png]]![[Pasted image 20230519121153.png]]

2) Removing Joins in Many-to-Many
- Don't bring back more data than you need! It could be costly for performance! 
- context.ChangeTracker.DetectChanges() -> Check before SaveChanges
- This is List.RemoveAt(), not an EF Core method
- Deleting a Many-to-Many relationships is easier with stored procedures!

![[Pasted image 20230519121412.png]] ![[Pasted image 20230519121540.png]] ![[Pasted image 20230519122117.png]]

3) Complex Many-to-Many Relationships

![[Pasted image 20230519122423.png]] ![[Pasted image 20230519122633.png]] ![[Pasted image 20230519122907.png]] ![[Pasted image 20230519122939.png]]
##### One to One Relationship

Which is the Principle? ![[Pasted image 20230519141640.png]]

Common Ways EF Core Identifies One-to-One ![[Pasted image 20230519121412.png]]![[Pasted image 20230519141853.png]] 

Dependent by defaults are Optional by Default ![[Pasted image 20230519142016.png]]

Migration version ![[Pasted image 20230519142355.png]] ![[Pasted image 20230519142430.png]]

Querying ![[Pasted image 20230519142501.png]] ![[Pasted image 20230519142608.png]] ![[Pasted image 20230519142556.png]] ![[Pasted image 20230519142716.png]]

Multi-Level query ![[Pasted image 20230519142751.png]] ![[Pasted image 20230519142759.png]] ![[Pasted image 20230519142940.png]] ![[Pasted image 20230519142951.png]] ![[Pasted image 20230519143136.png]]

Combining Object ![[Pasted image 20230519143315.png]] ![[Pasted image 20230519143321.png]]

Write code that is smart enough to protect you from expected behaviors

FK examples![[Pasted image 20230519143709.png]] ![[Pasted image 20230519143753.png]]

Fk conflict ![[Pasted image 20230519143909.png]]

Removing One-to-One deletes the dependent ![[Pasted image 20230519144034.png]]

Factors that affect relationship behavior ![[Pasted image 20230519144118.png]]