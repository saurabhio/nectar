### Practice

Note: Most of the following notes are taken from the various sources on the internet.

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
- Windows use CR+LF (\r\n) to indicate new lines, Unix based systems use just LF (\n)


- Logging level should be: 
  ```
  by default >= WARNING
  --verbose  >= INFO
  --debug    >= DEBUG
  ```
 
- The first rule of optimization is to not do it. 

- DevOps define "what" and SRE define "how", i.e. the philosophy of DevOps is implemented by SRE.

- LLVM is a compiler framework that is used to make, optimize intermediate or binary machine code. Its frontend is programming language (parser & lexer) and backend is machine specific code.

- Multi-processing means running many programs at same time. These processes do not share memory and run on different core if available.

- Simultaneous multi-threading is also called Hyper-threading. In this process, a CPU splits each of its physical core into two virtual cores.

- Web Assembly is a binary instruction format, designed as a portable target for compilation of C/C++/rust, etc., enabling deployment on browser or other JS runtime. WASM defines an Abstract Syntax Tree (AST) that gets stored in a binary format.


- The key in making great & growable systems is much more to design how its modules communicate rather than what their internal properties and behaviour should be. 
    The big idea is "messaging".
    
 - All teams will henceforth expose their data and functionality through service interfaces. And communicate through these interfaces only (over the network).
 - There will be no other form of IPC allowed, no direct linking, no direct reads from other team data store, no shared-memory model
 - It doesn't matter what technology each team use.
 - All services, without exception, must be designed keeping in mind that exposing these to developers outside.
    

- Rest API
  ```
  API is about what is going to be done, not about how
  Naming of API must convey "what" and only do that. (no side-effects)
  Specific error message should be returned
  API is a developer UI, ensure UX is pleasant
  Keep only two baseurls per resource
  Keep verbs out of baseurls, (as HTTP verbs do that). Use noun for resources
  GET /tickets
  GET /tickets/123
  Use plural url formats, e.g. tickets (not ticket)      
  Always use SSL
  Good documentation (should be publicly easily available)
  Always version APIs
  Create aliases for common queries
  API should have ability to take json as input
  Limit which fields are returned by API
  RESTful APIs should be stateless. And the authentication should not depend on cookies or sessions.
  ```
- Functions
  ```
  Names should reveal intent
  Functions should do one thing (single responsibility principle)
  Proper Abstraction, neither too high nor too low
  Not too much comments
  Functions should not use global variables, and not write to disk or console. This should be handled by some other special functions
  Avoid writing functions that take more than three (2^3 is 8 cases) input arguments
    ```

- Continuous Integration
  ```
  CI is a team problem. 
  Developers work on different things on different branches. Once someone is done with his change, 
  he’ll push or merge it to the main branch. And then the whole team will pull this change. The scenario we want to avoid is 
  that a faulty commit makes it to the main branch. 
  
  CI is all about preventing the main branch of being broken so your team is not stuck. That’s it. It is not about having all 
  your tests green all the time and the main branch deployable to production at every commit.
  
  The process of CI is independent of any tool. You could verify manually that the merge of your branch and the main branch 
  works locally. And then only actually push the merge to the repository. Now that would be very inefficient. That’s why 
  Continuous Integration is implemented using automated checks.
  
  In practice it means you need to pull any unit test framework that work for you and secure the common layers of the 
  application. If you have hundreds or thousands of tests you don’t need to run them all for each merge. It will take a lot 
  of time and most tests probably verify "non team blocker" features.
  
  Continuous Integration is not about tools. It is about working in small chunks and integrating your new code to the main
  branch and pulling frequently. Frequently means at least daily. Split the task you are working on into smaller tasks. Merge 
  your code very often and pull very often. This way nobody works apart for more than a day or two and problems do not have 
  time to become snowballs.
  
  Key points for a good CI build:
  It’s very simple. Keep it short. 3-7 minutes should be max. It’s not about CPU and resources. It is about developers productivity. The first rule of productivity is focus. Do one thing, finish it, then move to the next thing.
  
  Context switching is costly. Keep the context switching to its minimum.
  Keeping your CI build short makes it a trade off. Tests that run longer or provide little value in the context of CI should be moved to the CD step.
  ```
  
- Continuous Delivery
  ```
  Continuous Delivery and Deployment are engineering problems.
  Continuous Delivery is about being able to deploy any version of your code at all times. In practice it means the last or 
  pre last version of your code. You don’t deploy automatically, usually because you don’t have to or are limited by your 
  project lifecycle. But as soon as someone feels like it, deploy can be done in minimum time. That someone can be the 
  test/QA team that wants to test things out on a staging or preproduction environment. Or it can actually be time to roll 
  out the code to production.
  
  The idea of Continuous Delivery is to prepare artefacts as close as possible from what you want to run in your environment. 
  By preparing artefacts I don’t mean turning code into artefacts. This is usually a few scripts and minutes of execution. 
  Preparing means: 
  Run all the tests you can to ensure that once deployed the code will actually work. Run unit tests, integration tests, end 
  to end tests and even performance tests if you can automate that.
  
  Continuous Deployment is the next step. You deploy the most up to date and production ready version of your code to some 
  environment. Ideally production if you trust your CD test suite enough.
  
  Continuous Delivery and Continuous Deployment (let’s call them CD from now on) are not team problems. They are about 
  finding the right balance between execution time, maintenance efforts and relevance of your tests suite to be able to say  
  "This version works as it should". And it is a balance. 
  
  If you spend so much time keeping your tests up to date with latest code that it impedes the team progress, that is not 
  good either. And if your test suite ensures pretty much nothing … it is basically useless.
  
  In an ideal world we want 1 set of deployable artefacts per commit to the main branch. You can see we have a vertical 
  scalability problem: the faster we move from code to artefacts, the more ready we are to deploy the newest version of the 
  code.
  
  Continuous Integration is an horizontal scalability problem. You want developers to merge their code often so the checks 
  must be fast. Ideally within minutes to avoid developers switching context all the time with highly async feedback from the 
  CI builds.

  A good CI build:
  Ensures no code that breaks basic stuff and prevents other team members to work is introduced to the main branch
  Is fast enough to provide feedback to developers within minutes to prevent context switching between tasks
  
  Continuous Delivery and Deployment are vertical scalability problems. You have one rather complex operation to perform.
  A good CD build:
  Ensures that as many features as possible are working properly
  The faster the better, but it is not a matter of speed. A 30-60 minutes build is OK
  
  Continuous Integration is a trade off between speed of feedback loop to developers and relevance of the checks your perform 
  (build and test). No code that would impede the team progress should make it to the main branch. 
  
  Continuous Delivery of Deployment is about running as thorough checks as you can to catch issues on your code. Completeness 
  of the checks is the most important factor.
  ```
  
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
  
- SSH
  ```
  There are a number of SSH clients available both free and commercial, with OpenSSH being the most widely used client.  
  The OpenSSH client program is called ssh and can be invoked from the terminal. The OpenSSH client package 
  also provides other SSH utilities such as scp and sftp that are installed alongside the ssh command.
  
  sudo apt update
  sudo apt install openssh-server openssh-client
  
  nc -vz 127.0.0.1 22
  sudo /etc/init.d/ssh restart
  or
  sudo service ssh restart

  Each host has a unique fingerprint that is stored in the ~/.ssh/known_hosts file.
  
  When the username is not given, the ssh command uses the current system login name.
  
  To connect on a non-default port, use the -p option to specify the port:

  ssh -p 5522 username@hostname
  
  The OpenSSH client reads the options set in the per-user configuration file (~/.ssh/config). 
  A sample SSH config is shown below:

  Host dev
    HostName dev.linuxize.com
    User mike
    Port 4422

  now
  ssh dev
  means ssh -p 4422 mike@dev.linuxize.com

  If you already don't have SSH key pair on your local machine you can generate one by typing:

  ssh-keygen -t rsa -b 4096 -C "your_email@domain.com"

  Once you have your key pair, copy the public key to the remote server:

  ssh-copy-id username@hostname

  Enter the remote user password, and the public key will be appended to the remote user authorized_keys file.

  Once the key is uploaded, you can log in to the remote server without being prompted for a password.


  SSH tunneling or SSH port forwarding is a method of creating an encrypted SSH connection between a client 
  and a server machine through which services ports can be relayed.

  There are three types of SSH port forwarding:
    Local Port Forwarding
    Remote Port Forwarding
    Dynamic Port Forwarding

  Local Port Forwarding
  Local port forwarding allows you to forward a connection from the client host to the SSH server host and then to the destination host port. 
  Local port forwarding allows you to forward a port on the local (ssh client) machine to a port on the remote (ssh server) machine, which is then forwarded to a port on the destination machine.
  
  In this type of forwarding the SSH client listens on a given port and tunnels any connection to that port to the specified port on the remote SSH server, which then connects to a port on the destination machine. The destination machine can be the remote SSH server or any other machine.


  ssh -L [LOCAL_IP:]LOCAL_PORT:DESTINATION_HOST:DESTINATION_PORT -N -f [USER@]SSH_SERVER
  The -f option tells the ssh command to run in the background and -N not to execute a remote command.
  
  Remote Port Forwarding

  Remote port forwarding is the opposite of local port forwarding. It forwards a port from the server host to the client host and then to the destination host port. 
  Remote port forwarding is the opposite of local port forwarding. It allows you to forward a port on the remote (ssh server) machine to a port on the local (ssh client) machine, which is then forwarded to a port on the destination machine. 
  
  In this type of forwarding the SSH server listens on a given port and tunnels any connection to that port to the specified port on the local SSH client, which then connects to a port on the destination machine. The destination machine can be the local or any other machine.

  ssh -R [REMOTE:]REMOTE_PORT:DESTINATION:DESTINATION_PORT -N -f [USER@]SSH_SERVER

  Dynamic Port Forwarding

  Dynamic port forwarding creates a SOCKS proxy server that allows communication across a range of ports.
  Dynamic port forwarding allows you to create a socket on the local (ssh client) machine which acts as a SOCKS proxy server. 
  When a client connects to this port the connection is forwarded to the remote (ssh server) machine, which is then forwarded to a dynamic port on the destination machine.

  This way, all the applications using the SOCKS proxy will connect to the SSH server and the server will forward all the traffic to its actual destination.

  To create a dynamic port forwarding (SOCKS) pass the -D option to the ssh client:

  ssh -R [LOCAL_IP:]LOCAL_PORT  -N -f username@hostname

  scp local-file.txt remote_user@remote_server:/home/remote_user/xyz 

  scp -rp /path/to/source/.  remote_user@remote_server:/path/to/dest/
  
  recommended way:
  rsync -avzP /path/to/source/ remote_user@remote_server:/path/to/dest/

  scp remote_user@remote_server:/home/remote_user/xyz.tar /home/local_user/Desktop

  ```
  
- 
