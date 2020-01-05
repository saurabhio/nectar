### Practice

- For naming directories and files, use convention foo-bar

   Avoid foo_bar, foo bar, Foo bar, ...

- For every if write its else also. (otherwise anomaly may happen when calling that code in a loop)

   Or, for setting value based on condition, first initialize it with a default value. 
   ```
   k = default_value
   if condition:
       k = updated_value
   ...
   ```
   
   
- Common errors: Naming things, Off by 1 errors, cache invalidation
- For image processing,
  ```
  x+w-1    // instead of x+w
  y+h-1    // y+h
  x2-x1+1  // x2-x1
  y2-y1+1  // y2-y1
  ```
- 



- The key in making great & growable systems is much more to design how its modules communicate rather than what their internal properties and behaviour should be. 
    The big idea is "messaging".
    
 - All teams will henceforth expose their data and functionality through service interfaces. And communicate through these interfaces only (over the network).
 - There will be no other form of IPC allowed, no direct linking, no direct reads from other team data store, no shared-memory model
 - It doesn't matter what technology each team use.
 - All services, without exception, must be designed keeping in mind that exposing these to developers outside.
    

- API is about what is going to be done, not about how
- Naming of API must convey "what" and only do that. (no side-effects)
- Specific error message should be returned

- Names should reveal intent
- Functions should do one thing (single responsibility principle)
- Proper Abstraction, neither too high nor too low
- Not too much comments
- Functions should not use global variables, and not write to disk or console. This should be handled by some other special functions
- Avoid writing functions that take more than three (2^3 is 8 cases) input arguments
- API is a developer UI, ensure UX is pleasant
- Keep only two baseurls per resource
- Keep verbs out of baseurls, (as HTTP verbs do that). Use noun for resources
  ```
  GET /tickets
  GET /tickets/123
  ```
 - Use plural url formats, e.g. tickets (not ticket)      
 - Always use SSL
 - Good documentation (should be publicly easily available)
 - Always version APIs
 - Create aliases for common queries
 - API should have ability to take json as input
 - Limit which fields are returned by API
 - RESTful APIs should be stateless. And the authentication should not depend on cookies or sessions.
 



