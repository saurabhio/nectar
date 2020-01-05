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

```
