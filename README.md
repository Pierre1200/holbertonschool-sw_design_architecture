# holbertonschool-sw_design_architecture

Introduction and Context
In this project, you will be introduced to UML (Unified Modeling Language) as a tool to represent software systems.

You will work with a well-defined problem and your task will be to:

analyze the system description
identify its components
represent its structure using a class diagram
represent its behavior using a sequence diagram
This project is designed to be automatically validated, which means:

all required elements must be correctly identified from the problem
naming must match exactly
diagrams must follow the expected structure
This is an individual project focused on building your first modeling skills before moving to more open-ended design problems.

Learning Objectives
By the end of this project, you should be able to:

extract classes, attributes, and methods from a textual description
model relationships between classes
determine multiplicity from system rules
represent a system using UML class diagrams
model interactions using sequence diagrams
use Mermaid syntax to express diagrams
Resources
Introductory UML references (watch/read this first):

UML Class Diagrams
UML Sequence Diagrams
Mermaid documentation:

Mermaid Class Diagram Documentation
Mermaid Sequence Diagram Documentation
Optional design tools
You may use tools such as Lucidchart to sketch your diagrams visually before implementing them in Mermaid.

⚠️ Final submission must be in Mermaid format

General Requirements
Environment:

Ubuntu 20.04

Mermaid-compatible renderer

Use Python-style data types (str, bool, etc.)

File names must match exactly

Do not introduce elements not described in the problem

Do not rename classes, attributes, or methods

Diagrams must be syntactically valid

Only include elements that can be justified from the problem statement

The project will be automatically corrected

Problem — Library Loan System
A small library wants to manage its books and users.

The system must allow the library to:

store information about books
register users
create loans when a user borrows a book
System description
The system revolves around a Library that manages books, users, and loans.

Each Book has:

a title
an author
a state indicating whether it is available or not (true/false)
Each User has:

a name
an email
When a user borrows a book, a Loan is created.

Each Loan contains:

a start_date
an end_date
System behavior
The Library must be able to:

add_book to its collection
register_user
create_loan when a user borrows a book
When a loan is created:

the selected book must no longer be available
the loan must reference the book and the user involved
A Book must be able to:

mark_as_unavailable
mark_as_available
A Loan must be able to:

close_loan
When a loan is closed:

the associated book becomes available again
Important note
All the required information to build your diagrams is contained in this description.

You must extract:

class names
attributes
methods
relationships
multiplicities
The names used in your diagrams must match exactly the ones provided in the problem.

Do not introduce additional elements.

Hints for modeling
Use the following questions to guide your reasoning:

Can a Loan exist without a Book?
Can a Loan exist without a User?
Can a Book exist without being loaned?
Can a User exist without having loans?
If the Library is removed, should books and users still exist in the system?
Which object is responsible for creating a loan?
Which object is responsible for changing the availability of a book?
Final Notes
This project is intentionally structured to have a single correct solution.

You are expected to:

carefully read the problem
extract the required elements
translate them into diagrams
Precision matters. Small deviations in naming or structure may result in incorrect validation.

This project is your first step into software modeling. Future projects will be less guided and will allow multiple valid solutions.
