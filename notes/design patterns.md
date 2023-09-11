---
id: slbcis2cs1qxor0ip0m3zvx
title: design patterns
desc: ''
updated: 1694444880343
created: 1693652650529
---

#### How important is studying this?

#### How should one study this?
2021-08-04:  
I was thinking on how I would go about learning the design patterns in the GoF book. I think the angle of entry i would go ahead with is thinking, without input from the book, about each of the intents that are listed alongside the patternname:
- Intents
	- **_How do you represent an operation to be performed on the elements of an object structure_**?
		- **Case Study:** Abstract Syntax Trees
		- I'll assume object structure here also refers to C++ structs
		- So, what kind of operation is to be performed on the elements of a struct?
			- If the elements of the structs are of different types, why would we want to perform one type of operation on them? Is it even possible?
			- The operation itself, is it not just a regular function?
			- What then do you mean by representation for a function?
				- Shouldn't that just be its code?
	- **_How do you allow an object to alter its behavior when its internal state changes? (The object will appear to change its class)_**
		- **Case Study:** TCPConnection
	- _**How do you define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and update automatically.**_
		- **Case Study:** GUI toolkits
	- _**How do you capture and externalize an object's internal state so that the object can be restored to this state later?**_
		- **Case Study:** Graphical Editor
	- _**How do you access the elements of an aggregate object sequentially without exposing its underlying representation?**_
		- **Case Study:** Traversing a List
	- _**How do you encapsulate a request as an object, (thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.)**_
		- **Case Study:** user interface toolkits include objects like buttons and menus that carry out a request in response to user input
	- _**How do you avoid coupling the sender of a request to its receiver (by giving more than one objects a chance to handle the request?)**_
    - **Case Study:**

- I've not thought well-enough about how classes/OOP impact code performance, does it? I like how a solution to this problem ([[Invalid Transactions]]) was cleaned-up by making use of classes.  
  - https://softwareengineering.stackexchange.com/questions/125753/does-object-orientation-really-affect-algorithm-performance
  - https://softwareengineering.stackexchange.com/questions/272298/relation-between-object-orientation-and-algorithms?rq=1
  - https://softwareengineering.stackexchange.com/questions/239045/what-is-the-relationship-between-data-structures-and-algorithms
  - questions like these that are always stated using OOP constructs like classes ([[Design A Leaderboard]], [[LRU Cache]], etc.)
  
- Object-Oriented Design
	- [[Template Method vs. Strategy]]
	- [[Observer pattern]]
	- [[Push vs. pull observer pattern]]
	- [[Singletons and Flyweights]]
	- [[Adapters]]
	- [[Creational Patterns]]
	- [[Libraries and design patterns]]

#### Links
- https://realpython.com/inheritance-composition-python/
- https://stackoverflow.com/tags/oop/info
- The faster you unlearn OOP, the better for you and your software https://news.ycombinator.com/item?id=18526490
- Why is OOP still so widely spread? https://news.ycombinator.com/item?id=24356978
- Data-oriented design or why you might shoot yourself in the foot with OOP (2009) https://news.ycombinator.com/item?id=27658706
- Case against OOP is understated, not overstated (2020) https://news.ycombinator.com/item?id=30293622
- OOP Is Dead, Long Live OOP (gamedev.net) https://news.ycombinator.com/item?id=18250255
- Pretending OOP Never Happened https://news.ycombinator.com/item?id=23192264
- Don't distract new programmers with OOP https://news.ycombinator.com/item?id=2334939
- OOP Isn't a Fundamental Particle of Computing https://news.ycombinator.com/item?id=4781894
- 
