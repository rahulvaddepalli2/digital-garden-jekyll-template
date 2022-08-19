---
title:
---
A side effect is any application state change that is observable outside the called function other than its return value. 

Side effects include:

-   Modifying any external variable or object property (e.g., a global variable, or a variable in the parent function scope chain)
-   Logging to the console
-   Writing to the screen
-   Writing to a file
-   Writing to the network
-   Triggering any external process
-   Calling any other functions with side-effects

What you need to know right now is that side-effect actions need to be isolated from the rest of your software. 

If you keep your side effects separate from the rest of your program logic, your software will be much easier to extend, refactor, debug, test, and maintain.

This is the reason that most front-end frameworks encourage users to manage state and component rendering in separate, loosely coupled modules.