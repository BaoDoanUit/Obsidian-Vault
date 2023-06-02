---
up: [[Using EF Core in your tests]]
---
##### Debugging
<mark style="background: transparent;">For these persistence methods, we will only work with author objects, not relationships</mark><mark style="background: transparent;">
![[Pasted image 20230523090304.png]] 
![[Pasted image 20230523090424.png]]
![[Pasted image 20230523090433.png]]
![[Pasted image 20230523090513.png]]
![[Pasted image 20230523090620.png]]
![[Pasted image 20230523090919.png]]
![[Pasted image 20230523090928.png]] </mark>

<mark style="background: transparent;">If you're testing with a real database, resetting it is important</mark><mark style="background: transparent;">
![[Pasted image 20230523091430.png]]</mark>

<mark style="background: transparent;">Microsoft.EntityFramework.InMemory</mark><mark style="background: transparent;">
![[Pasted image 20230523091503.png]]![[Pasted image 20230523091532.png]]![[Pasted image 20230523091630.png]]![[Pasted image 20230523091609.png]]![[Pasted image 20230523091622.png]] ![[Pasted image 20230523091659.png]]![[Pasted image 20230523091821.png]]</mark>

<mark style="background: transparent;">Example</mark><mark style="background: transparent;">![[Pasted image 20230523091941.png]]![[Pasted image 20230523091956.png]]</mark>

<mark style="background: transparent;">Features</mark><mark style="background: transparent;">![[Pasted image 20230523092011.png]] ![[Pasted image 20230523092023.png]] ![[Pasted image 20230523092236.png]] ![[Pasted image 20230523092505.png]] ![[Pasted image 20230523092816.png]]</mark>

Seed & Test will use the same InMemory db instance

<mark style="background: transparent;">Review</mark><mark style="background: transparent;">![[Pasted image 20230523093008.png]]</mark>