---
up: [[Using EF Core in your tests]]
---
##### Debugging
For these persistence methods, we will only work with author objects, not relationships
![[Pasted image 20230523090304.png]]
![[Pasted image 20230523090424.png]]
![[Pasted image 20230523090433.png]]
![[Pasted image 20230523090513.png]]
![[Pasted image 20230523090620.png]]
![[Pasted image 20230523090919.png]]
![[Pasted image 20230523090928.png]]

If you're testing with a real database, resetting it is important
![[Pasted image 20230523091430.png]]

Microsoft.EntityFramework.InMemory
![[Pasted image 20230523091503.png]]![[Pasted image 20230523091532.png]]![[Pasted image 20230523091630.png]]![[Pasted image 20230523091609.png]]![[Pasted image 20230523091622.png]] ![[Pasted image 20230523091659.png]]![[Pasted image 20230523091821.png]]

Example![[Pasted image 20230523091941.png]]![[Pasted image 20230523091956.png]]

Features![[Pasted image 20230523092011.png]] ![[Pasted image 20230523092023.png]] ![[Pasted image 20230523092236.png]] ![[Pasted image 20230523092505.png]] ![[Pasted image 20230523092816.png]]

Seed & Test will use the same InMemory db instance

Review![[Pasted image 20230523093008.png]]