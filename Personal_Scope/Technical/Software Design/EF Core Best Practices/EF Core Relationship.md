---
up: [[EF Core General]]
---
##### Many to Many Relationship
<mark style="background: transparent;"></mark><mark style="background: transparent;">![[Pasted image 20230519110044.png]] ![[Pasted image 20230519110155.png]]</mark>

<mark style="background: transparent;">Joining Objects in New Many-to-Many Relationships</mark> <mark style="background: transparent;">![[Pasted image 20230519120452.png]]![[Pasted image 20230519120116.png]]![[Pasted image 20230519120216.png]]![[Pasted image 20230519120203.png]]![[Pasted image 20230519120313.png]]</mark>

<mark style="background: transparent;">Querying Across Many-to-Many</mark><mark style="background: transparent;">![[Pasted image 20230519120607.png]]![[Pasted image 20230519120620.png]]![[Pasted image 20230519120629.png]]</mark>

1) Understanding and benefit from curcular references in Graph
- This happens with all relationships, not just many-to-many
- We Keep Pointing to the Same Objects

<mark style="background: transparent;"></mark><mark style="background: transparent;">![[Pasted image 20230519121008.png]]![[Pasted image 20230519121033.png]]![[Pasted image 20230519121153.png]]</mark>

2) Removing Joins in Many-to-Many
- Don't bring back more data than you need! It could be costly for performance! 
- context.ChangeTracker.DetectChanges() -> Check before SaveChanges
- This is List.RemoveAt(), not an EF Core method
- Deleting a Many-to-Many relationships is easier with stored procedures!

<mark style="background: transparent;"></mark><mark style="background: transparent;">![[Pasted image 20230519121412.png]] ![[Pasted image 20230519121540.png]] ![[Pasted image 20230519122117.png]]</mark>

3) Complex Many-to-Many Relationships

<mark style="background: transparent;"></mark><mark style="background: transparent;">![[Pasted image 20230519122423.png]] ![[Pasted image 20230519122633.png]] ![[Pasted image 20230519122907.png]] ![[Pasted image 20230519122939.png]]</mark>
##### One to One Relationship

<mark style="background: transparent;">Which is the Principle?</mark> <mark style="background: transparent;">![[Pasted image 20230519141640.png]]</mark>

<mark style="background: transparent;">Common Ways EF Core Identifies One-to-One</mark><mark style="background: transparent;"> ![[Pasted image 20230519121412.png]]![[Pasted image 20230519141853.png]] </mark>

<mark style="background: transparent;">Dependent by defaults are Optional by Default</mark> <mark style="background: transparent;">![[Pasted image 20230519142016.png]]</mark>

<mark style="background: transparent;">Migration version</mark> <mark style="background: transparent;">![[Pasted image 20230519142355.png]] ![[Pasted image 20230519142430.png]]</mark>

<mark style="background: transparent;">Querying</mark> <mark style="background: transparent;">![[Pasted image 20230519142501.png]] ![[Pasted image 20230519142608.png]] ![[Pasted image 20230519142556.png]] ![[Pasted image 20230519142716.png]]</mark>

<mark style="background: transparent;">Multi-Level query</mark> <mark style="background: transparent;">![[Pasted image 20230519142751.png]] ![[Pasted image 20230519142759.png]] ![[Pasted image 20230519142940.png]] ![[Pasted image 20230519142951.png]] ![[Pasted image 20230519143136.png]]</mark>

<mark style="background: transparent;">Combining Object</mark> <mark style="background: transparent;">![[Pasted image 20230519143315.png]] ![[Pasted image 20230519143321.png]]</mark>

Write code that is smart enough to protect you from expected behaviors

<mark style="background: transparent;">FK examples</mark><mark style="background: transparent;">![[Pasted image 20230519143709.png]] ![[Pasted image 20230519143753.png]]</mark>

<mark style="background: transparent;">Fk conflict</mark> <mark style="background: transparent;">![[Pasted image 20230519143909.png]]</mark>

<mark style="background: transparent;">Removing One-to-One deletes the dependent</mark> <mark style="background: transparent;">![[Pasted image 20230519144034.png]]</mark>

<mark style="background: transparent;">Factors that affect relationship behavior</mark> <mark style="background: transparent;">![[Pasted image 20230519144118.png]]</mark>