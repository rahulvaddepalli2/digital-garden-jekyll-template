---
title: Programming
---

[[Problem Solving]] —Functions? Classes? Object-oriented programming? 

Coders like to talk about coding paradigms. 

So you’re lured into the illusion that you need to code with ONE of these paradigms.

But you don’t.

**Don’t think of structure**.

Overcoming coder’s block is simple. **Think of the problem you want to solve**. 

1. Understand the problem at hand
2. Plan a solution

Then you can follow these four steps:

1.  Break down the problem into small problems
2.  Find solutions to your small problems
3.  Assemble the solutions in a coherent manner
4.  Refactor and improve

**Structure comes in last** (during the 4th step, refactoring). If you think of structure, you screw up your brain before you even begin. Thinking of structure before solving the problem leads to complicated, overwhelming, bloated code.

[[Object-oriented Programming]] — Object-oriented programming (OOP) is a computer programming model that organizes software design around data, or objects, rather than functions and logic. An object can be defined as a data field that has unique attributes and behavior.

[[Functional Programming]] — Functional programming is the process of building software by composing [[pure functions]], avoiding shared [[state]], mutable data, and [[side-effects]]. Functional programming is declarative rather than imperative, and application state flows through pure functions. Contrast with object oriented programming, where application state is usually shared and colocated with methods in objects.

A popular way to describe the difference between to two is that:
1. Declarative Programming focuses on **_what_** the program should accomplish while 
2. Imperative Programming focuses on **_how_** the program should achieve the result.

## The Imperative Way

Let’s say that we have an array of pets.
`let pets = [
		``{ name: 'fluffy', color: 'white', age: 6, type: 'dog' },

			{ name: 'molly', color: 'brown', age: 9, type: 'cat' },

			{ name: 'buster', color: 'black', age: 3, type: 'dog' },

			{ name: 'grant', color: 'black', age: 6, type: 'cat' },

			{ name: 'pepsi', color: 'grey', age: 4, type: 'dog' },

			{ name: 'winston', color: 'brown', age: 8, type: 'dog' },

			{ name: 'sprite', color: 'white', age: 10, type: 'cat' },

			{ name: 'oscar', color: 'grey', age: 2, type: 'dog' },

			{ name: 'bumper', color: 'black', age: 12, type: 'dog' },

			{ name: 'happy', color: 'white', age: 11, type: 'dog' },

			{ name: 'speedy', color: 'black', age: 9, type: 'cat' }
		];
		
		ach element of the array is an object defining a pet.

Let’s assume that the business requirements state that we to filter the objects using these criteria: the pet is older than 7 years and has black fur.

For each matching record, we need to produce a string in the following format:

**_<petName> is <age> years old and is<color> in color._**

Now that we know what the output needs to be, how do we get it?

First, let's look at the imperative way of approaching the problem. Here’s the code.
	
  let outputArr = [];
  for (let index = 0; index < pets.length; index++) {
      const pet = pets[index];
      if (pet.age > 7 && pet.color == 'black') {
          outputArr.push(`${pet.name} is ${pet.age} years old and is ${pet.color} in color.`);
      }
  }
  console.table(outputArr);


## The Declarative Way

If we stop a moment and think about what we want to do from a higher level what do we come up with. In plain English I’d say:

“I want to filter an array based on a set of criteria and produce a string as output.”

I’m intentionally not thinking about the implementation. My thoughts are 10,000 feet above the problem, not 10 feet.

The words that jump out at me here are **_filter_** and **_produce a string_**. With that in mind, how about something like this:

pets.filter().map()

and the actual implementation

`let ageFilter = (pet) => (pet.age > 7);

`let colorFilter = (pet) => (pet.color == 'black');

`let stringMaker = (pet) => ${pet.name} is ${pet.age} years old and is ${pet.color} in color.`;

console.table(pets.filter(ageFilter).filter(colorFilter).map(stringMaker));

1.  Functional programming is a style of programming that requires thinking about your problems at a more abstract level.
2. Most of us learn to program at a procedural, imperative level so making the transition can be difficult when you’re just getting started.
3. Code written in a functional style is generally easier to reason about and easier to read.
4.  Functional code can be easier to maintain and modify.

	- Link(s):
		- https://itnext.io/how-to-start-thinking-functionally-in-javascript-b7805e3b48e

[[Interpreted & compiled programming languages]]