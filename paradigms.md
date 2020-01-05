### Paradigms

- Imperative
    - Procedural
    - Object oriented

- Declarative
    - Logic
    - Functional
    - Mathematical
    
  

1. Imperative: tell how to do step by step, lower level of abstraction, modifies the state

1.1 Procedural programming: action centered design
1.2 OO: data centered design, associate behavior with data structures


2. Declarative: describe what you want to be done, higher level of abstraction

2.1 Functional: evaluate an expression and use the resulting value for something. (Lambda calculus)

2.2 Logic: computation in terms of mathematical logic. (Predicate Calculus)


- Functional Programming 
  ```
  Functional programming is the process of building software by composing pure functions, avoiding shared state, 
  mutable data, and side-effects.
  
  A pure function is a function which:
  Given the same inputs, always returns the same output, and
  Has no side-effects
  
  A side effect is any application state change that is observable outside the called function other than its return value.
  Side effects include:
    Modifying any external variable or object property (e.g., a global variable, or a variable in the parent function scope chain)
    Logging to the console
    Writing to the screen
    Writing to a file
    Writing to the network
    Triggering any external process
    Calling any other functions with side-effects

  Pure functions have lots of properties that are important in functional programming, including referential transparency 
  (you can replace a function call with its resulting value without changing the meaning of the program).

  Function composition is the process of combining two or more functions in order to produce a new function or 
  perform some computation. 
  For example, the composition f . g is equivalent to f(g(x))

  Higher order function is any function which takes a function as an argument, returns a function, or both.

  A closure is the combination of a function bundled together (enclosed) with references to its surrounding state 
  (the lexical environment). 
  In other words, a closure gives you access to an outer function’s scope from an inner function. 
  To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to 
  another function.
  The inner function will have access to the variables in the outer function scope, even after the outer function has returned.

  A functor is something that can be mapped over. In other words, it’s a container which has an interface which can be 
  used to apply a function to the values inside it. When you see the word functor, you should think “mappable”.
  
  A shared scope can include global scope or closure scopes. 
  A list expressed over time is a stream.
  ```
  
- OOP Limitations
 ```
 There are two hard things in computer science: cache invalidation, naming things, and off-by-one errors.

    The key in making great and growable systems is much more to design how its modules communicate rather than 
    what their internal properties and behaviors should be.

    He literally said that the very term “object” was misleading and a more appropriate one would be “messaging.” 
    Here is what I think.

    there are two orthogonal means of interaction between objects: messaging and composition

    Precious time and brainpower are being spent thinking about ‘abstractions’ and ‘design patterns’ instead of 
    solving real-world problems

    OOP to me means only messaging, local retention and protection and hiding of state-process, and extreme 
    late-binding of all things.”
    ~ Alan Kay

    In other words, according to Alan Kay, the essential ingredients of OOP are:

        Message passing
        Encapsulation
        Dynamic binding

    Notably, inheritance and subclass polymorphism were NOT considered essential ingredients of OOP by Alan Kay,


    the whole point of OOP is not to have to worry about what is inside an object. Objects made on different machines and 
    with different languages should be able to talk to each other

    Alan Kay’s big idea was to have independent programs (cells) communicate by sending messages to each other. 
    The state of the independent programs would never be shared with the outside world (encapsulation).

    That’s it. OOP was never intended to have things like inheritance, polymorphism, the “new” keyword, and 
    the myriad of design patterns.

    Erlang is OOP in its purest form. Unlike more mainstream languages, it focuses on the core idea of OOP — messaging. 
    In Erlang, objects communicate by passing immutable messages between objects.


    Lambda calculus and Turing machines are functionally equivalent — that anything that can be computed using 
    a Turing machine can be computed using lambda calculus, and vice versa.


    Lambda calculus represents a top-down, function application approach to computation, while the ticker 
    tape/register machine formulation of the Turing machine represents a bottom-up, imperative (step-by-step) 
    approach to computation

    Both imperative programming and functional programming have their roots in the mathematics of computation theory, 
    predating digital computers.

  
OOP as if now is exceptionally bad.
Mixing code and data is not always good idea.

Single Inheritance & Multiple Inheritance are Syntatic relationship between 2 or more objects.

Polymorphism (subtyping) (is-a relationship) and Object composition (has-a relationship) are semantic relationship between 2 or more objects.

Avoid Implementation Inheritance (the extends relationship)
Use Interface Inheritance (the implements relationship)

Generalization: a-kind-of
Specialization: is-a
Aggregation: has-a


I have personally seen OOP projects fail because they become too complex to maintain.

OOP falls flat once the complexity of the application starts increasing.
 Instead of reducing complexity, it encourages promiscuous sharing of mutable state and introduces additional complexity with its numerous design patterns. OOP makes common development practices, like refactoring and testing, needlessly hard.

 but the truth is that modern Java/C# OOP has never been properly designed. It never came out of a proper research institution (in contrast with Haskell/FP). Lambda calculus offers a complete theoretical foundation for Functional Programming. OOP has nothing to match that.

Using OOP is seemingly innocent in the short-term, especially on greenfield projects. But what are the long-term consequences of using OOP? OOP is a time bomb, set to explode sometime in the future when the codebase gets big enough.

OOP is not natural for the human brain, our thought process is centered around “doing” things — go for a walk, talk to a friend, eat pizza. Our brains have evolved to do things, not to organize the world into complex hierarchies of abstract objects.


C++ is a horrible [object-oriented] language… And limiting your project to C means that people don’t screw things up with any idiotic “object model” c&@p.
— Linus Torvalds, the creator of Linux


A good programming framework helps us to write reliable code. First and foremost, it should help reduce complexity by providing the following things:

    Modularity and reusability
    Proper state isolation
    High signal-to-noise ratio

Unfortunately, OOP provides developers too many tools and choices, without imposing the right kinds of limitations. Even though OOP promises to address modularity and improve reusability, it fails to deliver on its promises (more on this later). OOP code encourages the use of shared mutable state, which has been proven to be unsafe time and time again. OOP typically requires a lot of boilerplate code (low signal-to-noise ratio).


I’m sorry that I long ago coined the term “objects” for this topic because it gets many people to focus on the lesser idea. The big idea is messaging.
- Alan Kay, the inventor of OOP

Alan Kay’s big idea was to have independent programs (cells) communicate by sending messages to each other. The state of the independent programs would never be shared with the outside world (encapsulation).

That’s it. OOP was never intended to have things like inheritance, polymorphism, the “new” keyword, and the myriad of design patterns.

Erlang is OOP in its purest form. Unlike more mainstream languages, it focuses on the core idea of OOP — messaging. In Erlang, objects communicate by passing immutable messages between objects.

Is there proof that immutable messages are a superior approach compared to method calls?

Hell yes! Erlang is probably the most reliable language in the world.

The most important aspect of software development is keeping the code complexity down. Period. None of the fancy features matter if the codebase becomes impossible to maintain. 


Limitations of the Human Brain

Why is mutable state such a big problem? The human brain is the most powerful machine in the known universe. However, our brains are really bad at working with state since we can only hold about 5 items at a time in our working memory. It is much easier to reason about a piece of code if you only think about what the code does, not what variables it changes around the codebase.

Programming with mutable state is an act of mental juggling️. I don’t know about you, but I could probably juggle two balls. Give me three or more balls and I will certainly drop all of them. Why are we then trying to perform this act of mental juggling every single day at work

Unfortunately, the mental juggling of mutable state is at the very core of OOP . The sole purpose for the existence of methods on an object is to mutate that same object.

In Functional Programming, state typically is being isolated. You always know where some state is coming from. State is never scattered across your different functions. In OOP, every object has its own state, and when building a program , you have to keep in mind the state of all of the objects that you currently are working with.

Is all state evil? No, Alan Kay state is not evil! State mutation probably is fine if it is truly isolated (not the “OOP-way” isolated).

It is also completely fine to have immutable data-transfer-objects. The key here is “immutable”. Such objects are then used to pass data between functions.

However, such objects would also make OOP methods and properties completely redundant. What’s the use in having methods and properties on an object if it cannot be mutated?


We’ve been told that global state is the root of all evil. It should be avoided at all costs. What we have never been told is that encapsulation, in fact, is glorified global state.

To make the code more efficient, objects are passed not by their value, but by their reference. This is where “dependency injection” falls flat.


Some people say that OOP tries to model the real world. This is simply not true — OOP has nothing to relate to in the real world. 

Objects in the real world interact with each other using messages, but they mostly are independent of each other.


Objects (or nouns) are at the very core of OOP. A fundamental limitation of OOP is that it forces everything into nouns. And not everything should be modeled as nouns. Operations (functions) should not be modeled as objects. 

Unfortunately, the design patterns are nothing other than band-aids. They exist solely to address the shortcomings of OOP.




```
