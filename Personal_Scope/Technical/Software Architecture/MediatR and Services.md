---
up: [[Architecture 101]]
---

I’ve seen multiple projects: some have it, some just don't understand what should be there and mixed it with others layers, some skip this layer at all. Don't be like the last one 😞. Don't write your application logic inside the controller. Move it somewhere else, for God’s sake.

Application layer is directly responsible for each use case in your system. It goes right after UI. So if you have any logic in your controller, move it to this layer. Your controllers should be thin as possible and only contain routing/mapping and other ASP logic

<mark style="background: transparent;">![[Microservice-1.png]]
![[Microservice-2.png]]
![[Microservice-3.png]]</mark>

Implementing cross-cutting concerns is always a struggle. With service-oriented architecture, the only good way to go is by creating a decorator. Adding something simple like logging performance of the app will have next look:

<mark style="background: transparent;">![[Microservice-4.png]]</mark>

The drawback here that every time you change your original service (add a method, change method signature) it will affect all decorators. There are other approaches, but they heavily rely on reflection, which is not the safest or fastest thing in a word.

With handlers, since every handler implement the same interface, you only need to implement single aspect and do not worry about any changes in handlers.

<mark style="background: transparent;">![[Microservice-5.png]]</mark>

