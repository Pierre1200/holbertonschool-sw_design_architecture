#Design Patterns
Introduction and Context
Writing classes is only one part of object-oriented programming. A more difficult step is deciding how responsibilities should be distributed between objects so that a program remains understandable, maintainable, and easy to extend.

Several design problems appear repeatedly in software systems:

How should objects be created without scattering construction logic across the codebase?
How can one part of the system react to changes in another without becoming tightly coupled to it?
How can behavior be extended without modifying existing code or creating an unmanageable number of subclasses?
These problems appear in real applications such as notification systems, APIs, payment platforms, user interfaces, and content management tools. Solving them well requires more than syntax. It requires good design decisions.

A design pattern is a reusable way of organizing code to solve a recurring design problem. A pattern is not a finished implementation to copy mechanically. Instead, it describes a structure of responsibilities and interactions that has proven useful in many systems.

A design pattern usually helps answer three questions:

What design problem is being solved?
Which roles do the participating classes or objects play?
Why does this structure make the system easier to change?
In this project, you will work with three foundational patterns from the Gang of Four catalog. Each belongs to one major category:

Creational patterns focus on how objects are created
Behavioral patterns focus on how objects communicate
Structural patterns focus on how objects are composed
The goal of this project is not to memorize patterns by name. The goal is to understand why a given structure solves a specific problem, and how that structure supports maintainable object-oriented design.

Important Note About Python
Design patterns were originally described in a language-agnostic way, but the way they are expressed depends on the programming language.

In Python, some patterns may look simpler or more flexible than in statically typed languages. Features such as dynamic typing, first-class objects, and composition can reduce the amount of boilerplate needed.

For that reason, this project does not expect rigid textbook implementations. Instead, it focuses on the design problem behind each pattern and on the reasoning that makes the solution useful.

Skills Developed
By completing this project, you will develop the ability to:

Identify when code becomes difficult to extend because responsibilities are too tightly coupled
Recognize recurring design problems in object-oriented systems
Extend existing systems without modifying their core logic
Reason about maintainability and flexibility, not only correctness
Explain why a particular structure improves the design of a program
Learning Objectives
After completing this project, you should be able to:

Understand what design patterns are

Distinguish between creational, behavioral, and structural patterns
Explain what kind of problem each pattern solves
Describe patterns as reusable design strategies rather than code templates
Apply the Factory pattern

Identify the coupling caused by scattered direct instantiation
Extend a factory registry to support a new type without modifying the core creation logic
Apply the Observer pattern

Explain how a subject can publish events without knowing the concrete type of every listener
Add a new observer and configure it to receive only specific topics
Apply the Decorator pattern

Explain why composition can avoid subclass explosion
Add a new decorator that composes correctly with existing ones without modifying any existing class
Core Concepts
Before starting the tasks, keep these ideas in mind:

Creational patterns focus on object creation
Behavioral patterns focus on communication between objects
Structural patterns focus on composition and arrangement of objects
Two important design ideas appear throughout the project:

Open/Closed Principle: code should be open for extension, but closed for modification
Composition over inheritance: behavior can often be extended more flexibly by combining objects rather than creating many subclasses
These ideas are closely related to broader object-oriented design principles such as SOLID, which aim to make software easier to maintain and evolve.

Resources
Required
Refactoring Guru — Design Patterns Introduction
Refactoring Guru — Factory Method
Refactoring Guru — Observer
Refactoring Guru — Decorator
Complementary Concepts
Geeks for Geeks — SOLID Principles with Real Life Examples
Open/Closed Principle
Composition over inheritance
Conceptual companion for this project
Recommended Python References
Python typing.Protocol
Python abc.ABC and abstractmethod
AI Tools
Any LLM-based assistant is allowed.

Use AI to explore ideas, compare alternatives, or clarify terminology. Do not use it as a substitute for understanding. If you cannot explain why a pattern helps in a given situation, your understanding is still incomplete.

General Requirements
Python 3.10 or later
Every submitted file must start with:
#!/usr/bin/env python3
Code must follow PEP 8
No external dependencies are required unless explicitly stated
Files must run with:
python3 <filename>
Final Note
Completing the TODOs is only one part of the work. By the end of this project, you should be able to explain:

what problem each pattern solves,
why the structure is organized the way it is,
and how that structure makes future changes easier and safer.
Tasks
0. Factory — Extending a registry
Design Problem
In many systems, object creation is spread across several parts of the code. This may start as something simple, but it becomes harder to maintain when new concrete types are added.

Friendly scenario
Imagine a mobility platform that supports buses, trains, bikes, and scooters. If different parts of the application create these objects directly, adding a new vehicle type requires modifying several places. A factory centralizes that decision.

Objective
Extend an existing factory registry to support a new vehicle type, without modifying the core creation logic inside create.

Context
The Factory pattern is a creational pattern. Its role is to centralize object creation so the rest of the code does not need to know which concrete class to instantiate. Instead of scattering Bus(), Train(), and Bike() calls across the codebase, callers ask the factory for a vehicle by name.

A naive factory that grows with every new type looks like this:

def create(self, kind: str):
    if kind == "bus":
        return Bus()
    elif kind == "train":
        return Train()
    elif kind == "scooter":    # must edit here every time
        return Scooter()
This violates the open/closed principle: the method is never closed for modification. The registry approach solves this — new types are registered from outside, and create never changes:

factory.register_kind("scooter", Scooter)
In the provided starter file, VehicleFactory already manages Bus, Train, and Bike via a _registry dictionary. register_kind(name, cls) maps a string key to a class; create(kind) looks up the key and calls the class with no arguments. The Scooter class is defined but not yet registered.

Instructions
Copy the starter code from here:

Read the existing VehicleFactory and main().
In main(), call factory.register_kind("scooter", Scooter) to register the new type.
Add print(factory.create("scooter").mode()) after the existing prints.
Running the code must print exactly:

road
rails
lane
scooter_lane
VehicleFactory.create must not contain a hardcoded if kind == "scooter" branch — the registry does the mapping. Adding a new vehicle type required zero edits to existing factory logic.