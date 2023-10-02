#### C# Design Patterns: State
You'll learn a tried and true technique for making your code cleaner, easier to maintain, and extremely extensible. 
You'll learn what it is and various ways it can be managed your application. From there, you'll get a conceptual overview of the state design pattern. You'll learn the principles that make it work, the components that make it up, and the benefits it brings to you as a developer and to all your development projects. With this foundation laid, you'll get hands-on. 
You'll build your own implementation of the pattern in Visual Studio and get to see these benefits firsthand. 
By the end of this course, you'll have the knowledege and understanding required to elegantly manage state in your C# development projects using the state design pattern. I hope you'll join me as we explore these concepts and more in the C# Design Pattern: State here, at PluralSight.

#### The State Design Pattern
State is one of those concepts that's so ubiquitous and intuitive that we seldom have to think about it. So before diving in, let's take a look exactly what we mean when using the term state. At its most basic, state can be defined as the condition of something variable. It's important to note that the term variable here is being used in its common linguistic sense, something changeable, and not referring to variables in computer science or mathematics. At some point early in our educations, we were all introduced to the common states of mater -- solid, liquid, and gas and we learned that the same substance can have different properties and behaviors based on its state, water flows, steam rises. You get the picture. But we don't have to go back that far. You're taking this course on some form of device, and that device needs to be connected to the internet in order for you to access this content. Taking the exact same steps you took to get here on a disconnected device would result in some form of error. Another way to put this is to say that your device can either be in a connected or a disconnected state, and your device will behave differently based on that state all the time. Let's say we're working on an order processing application. Is an order new, processing, canceled, or complete? And we implement behaviors based on these states. Can a user edit a canceled order. or can a completed order be canceled? This is just one example. The types of objects in an application and their behaviors are virtually unlimited. But regardless of the type of application your're developing, you'll invariably face questions of state. During this course, you'll be introduced to and implement a tried and true design pattern to apply to these challenges, the state pattern. The state pattern is one of 23 design patterns documneted by Gang of Four that describes how to solve reoccurring design challenges, Specifically, it addresses how an object can change its behavior when its internal state changes and how state-specific

##### The Naive Approach
Interdependent logic
Time lost managing fields
Difficult to extend
Harder to debug and manage

The State Design Pattern minimizes conditional complexity

##### Benefit of the State Pattern
More modular
Easier to read and maitain
Less difficult to debug
More extensible

##### Elements of the State Pattern
Context
Abstract State
Concrete State 

The State Pattern Approach
A list of posible states
The conditions for transitioning between those states
The state its in when initialized, or its initial state

A State Pattern for the Booking Process
![[../../../../Gallery/Pasted image 20230724184133.png]]

The Abstract State

