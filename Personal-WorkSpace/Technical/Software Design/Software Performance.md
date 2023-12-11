>##### Optimizing for the Developer
Here's why we don't care about memory (much)
The most expensive thing is your people's time
Sometimes, it's the only expense
Two options
> - Do all of the human work to improve it
> - Throw hardware at the problem

>##### The Long Term
You can only hardware-patch over bad code for so long
You begin by having good habits
So good deal with practice
There are different dimension of quality in software
Sometimes the -ilities conflict with each other
You must choose your -ilities wisely
And you can make architectural choice that enable hardware solutions
> 1. When Not to Optimize
> - Smart engineer always want to optimize
> - Maintainability is always key
> 2. When Optimization is Premature
> - Optimization should be just-in-time
> - There should be no standing optimization phase (for most projects)

>[!quote]
One of the biggest traps for smart engineers is optimizing something that shouldn't exist.

>#### Benchmark Dotnet
There's no such thing as fast or slow, except compared to something else
We'll create a benchmark and compare results
A stopwatch
You wrap this is a utility function
Resource volatility affects your numbers
The role of performance among the quality Ilities
What we mean by performance in this course
Two optimization anti-patterns
>- Premature optimization
>- Goldplating
A look at BenchmarkDotNet
Our benchmarker of choice
An Important Principle That BenchmarkDotNet Teches Us
>- It executes the function over and over again
>- Otherwise, short-term resource volatility can swamp the measure

>[!quote]
You should care one thousand times as much about code that gets executed one thousand times as often

![[Pasted image 20230612162157.png]]
![[Pasted image 20230612162319.png]]

#### Optimize Code Linebyline
1. String
- StringBuilder is Imuatble Class
- Why Not Just Make Strings Mutable?
	- This would make everything worse
	- Changing a value type to a reference type
	- This is unlikely to change
- One Last Point
	- We're not going to optimize fully
	- The further you optimize, the more you trade -ilities
Look at a very common string problem
Look at the naive way to work with it
Look at a slightly more intuitive way to work with it.
Learn a new-ish way to work with strings

2. Loops and Foreach
- It seem like the same performance not too different
3. Classes, Structs, and Records
- Key aspects in choosing between structs and classes
- It logically represents a single value, similar to primitive type (int, double, etc.)
- It has an instance size under 16 bytes
- It is immutable
- It will not have to be boxed frequently
4. Properties
- For properties simple enough to be represented as fields, representing them as fields makes no performance difference
- Check properties permission is fastest way.
5. LINQ
- Know exactly what's going on under the covers
- That code will always pass unit testing
- Should be execute remote?

8. Async
- This was a problem general enough that Microsoft created a framework to solve it
- Async creates a call and return delegate under the covers
- The sum of operations is probably longer
- But the user experience is better
- The execution time is the maximum execution time of the set of operations

7. Fan Out, Fan In
![[Pasted image 20230612191815.png]]

8. Using Queuing to Time-shift
- We'll do it later
- A shopping cart app in the Paleozoic era of the nineties
- The partner recommended expensive bandwidth that wouldn't really solve the problem
- But how often does validation fail? Not very often
- We executed that validation later on and circled back with the user if it failed.

Message Queuing ![[Pasted image 20230612192133.png]]

Planetary Scale Architecture ![[Pasted image 20230612192333.png]] ![[Pasted image 20230612192351.png]] ![[Pasted image 20230612192423.png]] ![[Pasted image 20230612192443.png]] ![[Pasted image 20230612192503.png]]


OpenAI Key
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