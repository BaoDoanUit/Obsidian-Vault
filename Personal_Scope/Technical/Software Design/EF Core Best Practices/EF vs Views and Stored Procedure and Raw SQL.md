---
up: [[EF vs Views and Stored Procedure and Raw SQL]]
---
#### Summary
1) EF Core allows you to work directly with
- Raw SQL 
- Stored Procedures
- View
- Scalar Functions
- Table Value Functions
- Map to Queries in DbContext

##### Querying with SQL raw 
<mark style="background: transparent;"> ![[Pasted image 20230519154829.png]] ![[Pasted image 20230519154900.png]] ![[Pasted image 20230519154917.png]] ![[Pasted image 20230519154923.png]] ![[Pasted image 20230519155009.png]] ![[Pasted image 20230519155037.png]] 
</mark>

- Never use SQL with parameters embedded directly into the string -> Because it easy got injection SQL issues

<mark style="background: transparent;"> Combining String</mark><mark style="background: transparent;">![[Pasted image 20230519155242.png]] ![[Pasted image 20230519155631.png]]![[Pasted image 20230519155829.png]] ![[Pasted image 20230519155835.png]] ![[Pasted image 20230519155950.png]] ![[Pasted image 20230519160001.png]] ![[Pasted image 20230519160045.png]] ![[Pasted image 20230519160057.png]] ![[Pasted image 20230519160110.png]] ![[Pasted image 20230519160149.png]] ![[Pasted image 20230519160328.png]] ![[Pasted image 20230519160341.png]] ![[Pasted image 20230519160356.png]]![[Pasted image 20230519160501.png]] ![[Pasted image 20230519160533.png]] ![[Pasted image 20230519160545.png]]</mark>