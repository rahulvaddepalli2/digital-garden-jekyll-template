---
title: Structures & Interpretation of Computer Programs - JS
---

What is Structures & Interpretation of Computer Programs about?

This book is known as the Wizard Book in hacker culture. It teaches the fundamental principles of computer programming (recursion, abstraction, modularity & programming language design & implementation.)

SICP is about standing back from the details to learn big-picture ways to think about the programming process. It focused attention on the central idea of _abstraction_ — finding general patterns from specific problems and building software tools that embody each pattern. It made heavy use of the idea of _functions as data_, an idea that's hard to learn initially, but immensely powerful once learned.

[](https://sourceacademy.org/sicpjs/1#p2)

The acts of the mind, wherein it exerts its power over simple ideas, are chiefly these three: 
1. Combining several simple ideas into one compound one, and thus all complex ideas are made. 
2. The second is bringing two ideas, whether simple or complex, together, and setting them by one another so as to take a view of them at once, without uniting them into one, by which it gets all its ideas of relations. 
3. The third is separating them from all other ideas that accompany them in their real existence: this is called [[abstraction]], and thus all its general ideas are made.

- John Locke, An Essay Concerning Human Understanding_ (1690)

We are about to study the idea of a computational process. 

Computational processes are abstract beings that inhabit computers. 

As they evolve, processes manipulate other abstract things called *data*.
The evolution of a process is directed by a pattern of rules called a *program*. 
People create programs to direct processes. 

In effect, we conjure the spirits of the computer with our spells.

A computational process is indeed much like a sorcerer's idea of a spirit. It cannot be seen or touched. It is not composed of matter at all. However, it is very real. It can perform intellectual work. It can answer questions. It can affect the world by disbursing money at a bank or by controlling a robot arm in a factory. The programs we use to conjure processes are like a sorcerer's spells. They are carefully composed from symbolic expressions in arcane and esoteric _programming languages_ that prescribe the tasks we want our processes to perform.

A computational process, in a correctly working computer, executes programs precisely and accurately. Thus, like the sorcerer's apprentice, novice programmers must learn to understand and to anticipate the consequences of their conjuring. Even small errors (usually called _bugs_) in programs can have complex and unanticipated consequences.

Fortunately, learning to program is considerably less dangerous than learning sorcery, because the spirits we deal with are conveniently contained in a secure way. Real-world programming, however, requires care, expertise, and wisdom. A small bug in a computer-aided design program, for example, can lead to the catastrophic collapse of an airplane or a dam or the self-destruction of an industrial robot.

Master software engineers have the ability to organize programs so that they can be reasonably sure that the resulting processes will perform the tasks intended. They can visualize the behavior of their systems in advance. They know how to structure programs so that unanticipated problems do not lead to catastrophic consequences, and when problems do arise, they can _debug_ their programs. Well-designed computational systems, like well-designed automobiles or nuclear reactors, are designed in a modular manner, so that the parts can be constructed, replaced, and debugged separately.

1.1 — The Elements of Programming

A powerful programming language is more than just a means for instructing a computer to perform tasks. The language also serves as a framework within which we organize our ideas about processes. Thus, when we describe a language, we should pay particular attention to the means that the language provides for combining simple ideas to form more complex ideas. 

Every powerful language has three mechanisms for accomplishing this:

-   1. **primitive expressions**, which represent the simplest entities the language is concerned with,
-   2. **means of combination**, by which compound elements are built from simpler ones, and
-   3. **means of abstraction**, by which compound elements can be named and manipulated as units.

# 2.2  — Hierarchical Data and the Closure Property
Closure is the key to power in any means of combination because it permits us to create _hierarchical_ structures—structures made up of parts, which themselves are made up of parts, and so on.

# 2.2.4   Example: A Picture Language
## Higher-order operations

In addition to abstracting patterns of combining painters, we can work at a higher level, abstracting patterns of combining painter operations. That is, we can view the painter operations as elements to manipulate and can write means of combination for these elements—functions that take painter operations as arguments and create new painter operations.

# 3.1  Assignment and Local State
 An object is said to "have [[state]]" if its behavior is influenced by its history. A bank account, for example, has state in that the answer to the question "Can I withdraw $100?" depends upon the history of deposit and withdrawal transactions. We can characterize an object's state by one or more _state variables_, which among them maintain enough information about history to determine the object's current behavior. In a simple banking system, we could characterize the state of an account by a current balance rather than by remembering the entire history of account transactions.
 
 In a system composed of many objects, the objects are rarely completely independent. Each may influence the states of others through interactions, which serve to couple the state variables of one object to those of other objects.
 
 # 3.1.2   The Benefits of Introducing Assignment
 Viewing systems as collections of objects with local state is a powerful technique for maintaining a modular design.
 
 # 3.4 [[Concurrency in Javascript]] — Time is of the essence
 My Notes:
	 - Concurrency is the idea that multiple operations can execute at the same time (ideally makes functions faster—↑ speed complexity)
	 	- This can lead to issues, especially if these operations share the same state variable (i.e., a balance variable for a bank account).
		- One solution is to implement serialization.
 
 # 3.4.2   Mechanisms for Controlling Concurrency
 ## Serializing access to shared state

Serialization implements the following idea: Threads will execute concurrently, but there will be certain collections of functions that cannot be executed concurrently. More precisely, serialization creates distinguished sets of functions such that only one execution of a function in each serialized set is permitted to happen at a time. If some function in the set is being executed, then a thread that attempts to execute any function in the set will be forced to wait until the first execution has finished.

[](https://sourceacademy.org/sicpjs/3.4.2#p4)

We can use serialization to control access to shared variables. For example, if we want to update a shared variable based on the previous value of that variable, we put the access to the previous value of the variable and the assignment of the new value to the variable in the same function. We then ensure that no other function that assigns to the variable can run concurrently with this function by serializing all of these functions with the same serializer. This guarantees that the value of the variable cannot be changed between an access and the corresponding assignment.

**Concurrency, time, and communication:**

We've seen how programming concurrent systems requires controlling the ordering of events when different threads access shared state, and we've seen how to achieve this control through judicious use of serializers. 

But the problems of concurrency lie deeper than this, because, from a fundamental point of view, it's not always clear what is meant by "shared state."

The basic phenomenon here is that synchronizing different threads, establishing shared state, or imposing an order on events requires communication among the threads. In essence, any notion of time in concurrency control must be intimately tied to communication.[11](https://sourceacademy.org/sicpjs/3.4.2#footnote-11) 

It is intriguing that a similar connection between time and communication also arises in the Theory of Relativity, where the speed of light (the fastest signal that can be used to synchronize events) is a fundamental constant relating time and space. The complexities we encounter in dealing with time and state in our computational models may in fact mirror a fundamental complexity of the physical universe.

 # 4.1.1  The Core of the Evaluator
 The evaluation process can be described as the interplay between what two functions? 
 1. f
 2. f
 ![[Pasted image 20220312202056.png]]
 
 