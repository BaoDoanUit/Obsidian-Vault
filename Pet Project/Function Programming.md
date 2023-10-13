##### Information
Functional programming is not about not having state. It about keeping the functions [referential transparency](http://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) and without side effects. Usually this mean having no state, but that not has to be the case.  

#### Effects
Referential transparency mean that for a given input parameters the >?function will always return the same output.  
No having side effect mean that the function does not change the outer world, for example not changing some global parameter. This also mean that not calling the function wont effect other functions.
One example when there is a state but it still keep referential transparency and no side effects are caching.


```scala
class StatefullCache {
  val remoteRepository = ???
  var map: Map[String,Data] = Map()
  private def fetchFromRemote(id: String) = {
    val data = remoteRepository.get(id)
    map = map + (id -> data)
    data
  }
  def get(id: String) = map.getOrElse(id, fetchFromRemote(id))
}
```

#### Extension
This class have state but it referential transparency, since it always return the same result for any given id. It also does not has side effects (well... it has the memory growing, but that a limitation which does not effect the application flow).  
In practice no application is a "pure functional". printing to the screen, file & network I/O have all size effects (and get to to the extreme, even the CPU heat is a side effect). The idea in functional programming is to keep the side effect to the minimum and isolated. Some languages force you do that. Scala does not force it, but encourage you do so.
Depending on your use case calling 3rd party API/REST/whatever which isn't immutable or has side effect, may be count for practical uses by your application as functional or not. For example if any running of the application is "new world" where the data may be change the class above will work well (Since it will only access the external service once per id).
To summarize it, if you minimize the mutability and the side effect and keep it all in control then you can have the benefits for functional programming in the rest of the app.


##### Combine OOP with FP
Personally, I don't see much value in mixing particular OO constructs with functional programming. OO, at least in practice, is all about managing mutable state in a particular sort of way; functional programming is about managing it in a different sort of way. (Which, I think, is much better.) Contrary to what some people say, there is actually quite a lot of redundancy between the two!
On the other hand, there are a lot of ways to combine high-level OO ideas with functional programming. Apart from managing state, OO gives us a way to organize our programs. We can take some of these organizational ideas without reusing existing OO constructs or carrying over much OO baggage.
Happily, it turns out that many of the core ideas for organizing code from an OO standpoint are supported just as well by existing functional features. The main feature would be the module, which acts quite a bit like an OO class except without state or objects.

#### Practices
One big idea is information hiding. We don't want to expose unnecessary implementation details. Modules are perfect for this: we can choose what we want to and don't want to export. Moreover, they allow us to export abstract types. These are types whose implementation is not given; you can only ever use functions from the same module on them. This sort of abstraction is very neatly captured by [existential types](http://stackoverflow.com/questions/292274/what-is-an-existential-type "stackoverflow.com"). In a sense, existential types make this sort of data-hiding a first-class citizen of the type system. The Haskell [smart constructor](http://www.haskell.org/haskellwiki/Smart_constructors "www.haskell.org") is a great example of using some OO ideas in a distinctly non-OO language.Another idea is programming against interfaces. Many OO languages put a lot of emphasis on this: in Java, `List<A>` is an interface, not a type. This is where modules again step in, especially [module signatures](http://caml.inria.fr/pub/docs/manual-ocaml/moduleexamples.html#sec19 "caml.inria.fr"). A module signature lets you just specify the set of functions you need without a concrete implementation. Just like an interface! One neat trick is that a module can have types as parts of its signature, which allows for interesting sorts of abstraction beyond what you can do with classic OO interfaces.
In general, just apply your OO knowledge to using modules and you'll be in a good position.

### What things can functional programming do better than OOP or OOP cannot do at all?
Many of the answers here are very limited in their concept of "things functional programming can do". They are really talking about the programs which can be built and what those can do. Yes, any Turing-complete language can be used to generate a program to solve any calculable problem. That is a very limited concept.

#### Programming languages do not solve problems. People solve problems. Computers can help. Programming languages are created to enable humans to 
- Think about problems
- Express their thoughts about those problems
- Communicate their thoughts to digital computers, to manipulate the computers so that they will solve the problems.

Those first two points - thought and expression - are handled very differently by the two paradigms. They have different strengths, they each  (as currently understood and implemented) make some modes of thinking about and expressing solutions which OOP cannot do. There is also one particular concept which is absolutely core to OOP and for which FP doesn;t yet have a clear narrative (Although there are, now some very useful concepts to be used).
In answers to this and many other questions on Quora, there are people saying "FP and OP are equivalent ways to do the same thing". That is not true. They differ in their founding principles and their scope.

#### Foundations of Functional Programming
Functional programming has, at its core, the Lambda Calculus.
Many functional programming languages base their semantics and syntax on a version of the calculus.
Those languages mostly compile to intermediate stages which are very direct expressions of the calculus (in some cases, several stages with different refinements).
The compilers use processes from the calculus (e.g. eta conversion) at many steps in the process. For example, to construct the Abstract Syntax Tree (an early stage) and to perform compiler optimisations (later stage).
Humans can use the calculus to reason about and refactor their code. It can, for example, be used to simplify code or to make it more generic and parametrised with confidence that the essential function of the code has not been changed.
Humans can use the calculus to build type systems and to reason about how adding a new type to a program will affect the whole (and whether it is compatible at all).
Humans can use those type systems to build whole hierarchies of abstractions which have logical, provable relationships.
One result is that humans can use the same principles to reason about their code consistently at many levels. At the higher levels of the code they have written or the types which it uses but also at the low level creation of the runtime program and at all points in between (if using a full-on functional language.
Even when applying FP style in a non-FP language, these principles can still be applied to your code (it just requires extra discipline to write referentially transparent code).
I have already described a list of things which FP can do and which OOP does not even attempt, but I haven’t yet explained what the Lambda Calculus is.
It is a complete model for computation. As with the Turing machine, anything which is computable can be expressed in the model. Any computable problem can be solved with it. (OK, both Turing and Church wussed out when it came to properly defining “computable”. We’ve all gotten away with it so far).
It’s also an accessible model. I explained it to my mother in a way that made sense to her. Wouldn’t even attempt that with the Turing machine.
So the concepts which FP offers to help humans think about their code are based on the fundamentals of a computation model. FP provides a consistent way to reason at every level of the solution (um, until you get to the very bottom, where current digital computer design means it has to be translated into something imperative).

##### FP is, if you like, a full-stack paradigm. Computation all the way down.
Foundations of Object Oriented Programming
So what is the origin and basis of OOP?
It’s not the Turing machine. Hell, who bases their language on an infinite paper tape going backwards and forwards? When would that ever help you think about your code and the problem you are trying to solve? The point of the Turing machine, for language design, is that it can solve any computable problem. If it can be shown that your language can create a simulated Turing machine, then it has at least one way to solve any problem because you can always feed simulated tape to the simulated machine.
But if you are interested in simulating machines...
OOP has its origins in Simula 67. Simula was created to provide a way to model “complex man machne systems” and to translate those models into compiled code; one language to do both. Classes, subclasses and objects were created for this.
Interestingly, a serious challenge they faced in a single-threaded language was representing any complex system where multiple processes happen concurrently. So they added concurrency primitives (coroutines, to be precise). It is ironic that the first OOP language had a concurrency solution, given the reputation OOP languages now have for making concurrency difficult (not entirely fair - imperative makes concurrency different. OOP just gave the illusion of making it easy).
The language designers who were influenced by Simula mostly forgot the concurrency issue. Modelling - and mapping models to units of code - became the definition.

#### The core of OOP is
Domain modelling via classes, subclasses and objects.
Encapsulation as a way to model state.
An evaluation strategy which clarifies the domain model and enables compilation into a working program.
That’s it. I’m not belittling the achievement; that’s a lot of very clever, consistent “it”.
OOP is not prescriptive. It provides a flexible framework for domain modelling and then it’s over to you. It provides minimal constraints for the evaluation and organisation of your computational code and the rest is for you to decide. It really doesn’t care if the main body of work is done imperatively, functionally, by a Turing machine or by tap-dancing frogs. Most OO languages are redesigns of imperative languages so that’s what you tend to find filling in the gaps, but it doesn’t have to be that way. Look at the increasing rate at which OO languages are adding FP features.

#### Comparasion
Unlike FP, OOP has no general, underlying model which recursively explains all the parts. It’s a framework; a collection of concepts which seem to work well together.
Beyond that, it’s largely down to your common sense and experience. That’s what the Gang of Four design patterns, SOLID and the rest actually are.
OOP is not a full-stack paradigm. There is a level below which it does not usefully apply (much higher than the point where FP stops). It can’t help you optimise your compiled code or analyse an individual expression.

#### Summary
What doesn’t OOP doesn’t do well? Pick any of the bullet points in the FP Foundations section above.
What can’t it do at all? Recursively define and extend itself from the bottom up. Powerful new concepts regularly emerge in the FP world which are fully, provably consistent with (usually derived from) existing abstractions.
Why do Scala and F# mix paradigms? Well, one thing they do is try to mix FP’s advantages with OO’s familiar domain modelling narrative. Another is make a very large existing set of technologies, tools and libraries available to functional programming.
Hope that helps.














