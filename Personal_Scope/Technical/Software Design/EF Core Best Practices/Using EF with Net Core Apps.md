---
up: [[EF Core General]]
---
#### Summary
Review lifecyle of DbContext in web apps
Create an Net Core API Project
Create a template generated controller
Wire up Net Core to PubContext
Learn how to combine entities and DTOs
Learn tips for debugging and logging

##### LifeCycle
Working in a Single DbContext Instance

<mark style="background: transparent;">Retrieve Data (Context starts tracking state of each returned object) -> Modify Objects -> SaveChanges (Context updates state of tracked objects before determining SQL)</mark>
<mark style="background: transparent;">![[Pasted image 20230522143643.png]] ![[Pasted image 20230522143711.png]] ![[Pasted image 20230522143723.png]] ![[Pasted image 20230522143742.png]] ![[Pasted image 20230522143751.png]] ![[Pasted image 20230522143816.png]]</mark>

<mark style="background: transparent;">NET Core APP</mark>
<mark style="background: transparent;">![[Pasted image 20230522144629.png]] ![[Pasted image 20230522145311.png]] ![[Pasted image 20230522145354.png]] ![[Pasted image 20230522145452.png]] ![[Pasted image 20230522145513.png]] ![[Pasted image 20230522145553.png]] ![[Pasted image 20230522145602.png]]
![[Pasted image 20230522145854.png]]</mark>

<mark style="background: transparent;">Update DTOs</mark><mark style="background: transparent;">![[Pasted image 20230522150030.png]]</mark>

##### Practical Mapping
<mark style="background: transparent;"></mark><mark style="background: transparent;">![[Pasted image 20230523221259.png]] ![[Pasted image 20230523221416.png]] ![[Pasted image 20230523221433.png]]</mark>

<mark style="background: transparent;">Conventions</mark><mark style="background: transparent;">![[Pasted image 20230523221612.png]] ![[Pasted image 20230523221805.png]]![[Pasted image 20230523221727.png]] ![[Pasted image 20230523221850.png]]</mark>

<mark style="background: transparent;">Even More EF Core mapping Support</mark>
<mark style="background: transparent;">![[Pasted image 20230523221928.png]]
![[Pasted image 20230523222014.png]]
![[Pasted image 20230523222031.png]]
![[Pasted image 20230523222036.png]]
![[Pasted image 20230523222048.png]]
![[Pasted image 20230523222102.png]]</mark>

Annotations are applied at runtime and ignored by the complier

<mark style="background: transparent;">Persisting Enums with EF Core</mark><mark style="background: transparent;">
![[Pasted image 20230523222211.png]]
![[Pasted image 20230523222224.png]]
![[Pasted image 20230523222236.png]]
![[Pasted image 20230523222310.png]]
![[Pasted image 20230523222333.png]]
![[Pasted image 20230523222340.png]]
![[Pasted image 20230523222437.png]]
![[Pasted image 20230523225714.png]]
![[Pasted image 20230523225740.png]]
![[Pasted image 20230523225744.png]]</mark>

<mark style="background: transparent;">Applying Bulk Configurations and Conversions</mark><mark style="background: transparent;">
![[Pasted image 20230523225838.png]]
![[Pasted image 20230523225941.png]]
![[Pasted image 20230523230008.png]]
![[Pasted image 20230523230029.png]]</mark>

Mapping Complex Types and Value Objects

<mark style="background: transparent;">Not every property is a scalar type or a relationship!</mark><mark style="background: transparent;">
![[Pasted image 20230523230127.png]]
![[Pasted image 20230523230208.png]]
![[Pasted image 20230523230225.png]]
![[Pasted image 20230523230240.png]]</mark>

If you are designing via Domain-Driven Design, owned entities can be used to map value objects
Mapping provide a rich menas of overriding those defaults
EF Core respects project NRT setting
A subset of data annotations are recognized by the model builder 
Enums have been supported for long time 
Map "unmappable" types with value conversions
Define bulk mapping and conversions
Owned entities let you map complex types and value objects

<mark style="background: transparent;">Database Connectivity</mark><mark style="background: transparent;">![[Pasted image 20230523230732.png]]![[Pasted image 20230523230934.png]]![[Pasted image 20230523230943.png]]![[Pasted image 20230523230948.png]]![[Pasted image 20230523231003.png]]![[Pasted image 20230523231014.png]]</mark>

<mark style="background: transparent;">Setting up</mark><mark style="background: transparent;">![[Pasted image 20230523231056.png]]![[Pasted image 20230523231109.png]]</mark>

<mark style="background: transparent;">EF Core's Transaction Support and Concurrency Handling</mark><mark style="background: transparent;">![[Pasted image 20230523231346.png]]![[Pasted image 20230523231403.png]]![[Pasted image 20230523231417.png]]![[Pasted image 20230523231458.png]]![[Pasted image 20230523231535.png]]![[Pasted image 20230523231543.png]]![[Pasted image 20230523231622.png]]![[Pasted image 20230523231800.png]]![[DbContextPool.png]]![[EFCore_Learn.png]]</mark>