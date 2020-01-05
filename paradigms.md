### Paradigms

- Imperative
    - Procedural
    - Object oriented

- Declarative
    - Logic
    - Functional
    - Mathematical
    


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
  
