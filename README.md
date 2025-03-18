[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MMj2nZMu)
# Rsearch and Reflection Journal
Research and Reflection Journal for DGL 104 course

## Week 8 Lecture
**FUNCTIONAL USER REQUIREMENTS**
**USER STORIES:**

**As developers, I encourage you to draw on programming knowledge when assessing apps**
• The first thing we tend to assess when critically examining an app is the interface and the UX. 
• Consider your programming knowledge when assessing apps: 
• Frameworks/libraries/APIs 
• Data structures 
• Platform-specific conventions

**User stories are a common tool employed in the design of user-facing systems**
• User stories are written in natural language from the perspective of the user 
• Typically written in the form: "As a user, I can " 
• User stories facilitate intra-team communication

**The downside of user stories is the lack of implementation details** 
• Typically written without immediate consideration of technical constraints.  
• Issues related to technical considerations are sometimes overlooked (e.g. performance criteria). 
• User stories can be written with technical concerns in mind, but this may not be an ideal approach.

**A technical design document (TDD) is a written artefact that addresses technical concerns in a design context** 
• Goal: Produce an unambiguous document detailing: 
• Architecture 
• Feature implementation 
• Testing plan 
• Performance criteria 
• There is no accepted standard for the development of TDDs. 
• TDDs can encompass a complete software design, or specific features

**Functional requirements describe software features on an input/output basis** 
• Just like 'functions' in programming (or in mathematics). 
• These may be included in a TDD, or related document. 
• Typically derived from user stories, or from use cases (a more technical-first approach to modeling systems).

**We can use the input/output approach to develop clear 'specifications' for our apps**
• Functional requirements and specifications are part of the standard software engineering toolkit... 
• If our user story says: "as a forum user I can see posters' profile pictures as avatars", this might imply the following set of functional requirements: 
• Update profile: Enter required profile data (name, email) and optional profile data (profile pic, address, website, social accounts) -> return profile page with default content (e.g. default avatar) for incomple optional data.

## Week 9 Lecture
**Design Patters:**
•	They are reusable fragments of code that provide a solution to a specific – and typically well-understood-coding problem.
•	They really do nothing at the time of coding but really help to encounter common problems in the code. 
•	Long-term maintainability of a codebase is the main advantage of design patterns.

**Design patterns are accepted solutions to common well-defined problems**
•	Popularized by the ‘Gang of Four’ and Design Patters: Elements of Reusable Object-Oriented Software.
•	Based on OOP principles:
1.	“Program to an interface, not an implementation”.
2.	“Favor ‘object composition’ over ‘class inheritance’.”

**In OOP we reply on the inheritance chain to share data and behaviour**
•	In the typical OOP approach one might write inherited classes that are meant to interact in some way.
•	But what happens when you need your BMW to fill up at the pump? Where do the methods(behaviour) live?
•	If Vehicle is a base class, then Car will be derived class 1 and the BMW would be derived class 2.
•	Service station is base class, then Shell will be derived class and pump as well.

**“[Programming] to an interface” means to write a “shared contract” for implementations**
•	An interface is an abstract definition of some behavior that you want your objects to implement.
•	This has the benefit of keeping your class definitions clean and making testing easier.
•	The pump interface could be implemented for non-car classes (e.g. aeroplanes).

**Similarly, relying solely on inheritance chains for behaviour can be limiting**
•	Inheritance chains can lock you into dangerous patterns that produce brittle code, or over-engineered code.
•	Object composition allows data and behaviour from related objects to be “composed” into more complex objects that meet behaviour requirements.
•	This is related to the idea of function composition and higher-order functions in functional programming paradigm.

**Design patters are typically categorized into three solution-based classifications**
•	Creational patterns are used for creating objects(sometimes many objects) in a predictable way.
•	Structural patterns are used for composing classes into larger structures with more complex behavior
•	Behavioural patterns are used to support common communication patterns between distinct objects

**The Singleton pattern ensures that there is only ever one instance of a particular class**
•	Responsibility: managing a common resource, or program state
•	A creational pattern
•	Typically globally available
•	The class definition makes creating instances of the class impossible via: 
•	Private constructors
•	Public getInstance() method that returns a static instance.

**The Observer pattern notifies observers of state changes so that they can update correctly**
•	Responsibility: subjects keep a list of observers, observers subscribe and unsubscribe to subjects
•	A behavioral pattern
•	Notifications are one-to-many
•	Subjects don’t care how many observers they have
•	Ideally subject and observer are loosely couples.
•	For example: In an auction, If auctioneer is subject then the bidders would be observers

**Design patterns aren’t bullet proof solutions to all problems, however **
•	Some have stated that design patterns are really ‘kludge’ solutions to missing features in programming languages
•	Design patterns are paradigmatic by nature- the common design patterns won’t naturally fit other programming paradigms
•	Hammers and  nails…

**Anti-patterns on other hand, demonstrate common patterns you should avoid**
•	Originally inspired by the Gang of Four design patterns.
•	Has been applied more broadly than exclusively to software(tend to be used in management studies).
•	The best way to avoid anti-patterns
•	Code review
•	Style guides
•	Idiomatic code

**Few Design patterns used in software industry**
1.	Creational DP - Singleton, Factory, Builder, Prototype
2.	Structural DP – Adapter, Decorator, Façade, Composite
3.	Behavioral DP – Observer, Strategy, Command, State

## Week 10 Class: MV Patterns
**MV* refers to the collection of user interface architecture patterns using Model and View** 
-  Model View Controller (MVC)  
- Model View Presenter (MVP) 
- Model View Adapter (MVA) 
- Model View Intent (MVI) 
- Model View ViewModel (MVVM)

**Model View Controller was the first; Model View ViewModel is common in apps today**
- MVC developed as part of Smalltalk at Apple. 
- MVC became an integral part of iOS development. 
- MVC is a key architectural pattern on the web (Django, Ruby on Rails). 
- MVVM is presently the most commonly used in app development 
    -	Mobile: Jetpack Compose, SwiftUl 
    -	There are some MVVM-specific web frameworks too

**The common thread across all MV* patterns is separation of concerns and testable code** 
- The Model contains the business logic of the app. 
- The View represents all app data and captures user interactions. 
- The Model and View should never intersect -separation of concerns. 
- All MV* patterns are graphical in nature – GUI architecture.

**Model View Controller (MVC) is a user interface design / architecture pattern** 
- Sometimes referred to as a design pattern... 
- Sometimes referred to as an architectural pattern... 
- All MV* patterns are user interface driven

**The model contains the software's business logic** 
- Typically data and all logic that creates, modifies and stores data. 
- Data is often modeled by OOP classes or enums. 
- Model must be completely independent of the View

**The View contains the user interface, presents data and interaction opportunities to the user**
- No data nor state should be stored in the View.
- The View only represents what is stored in the Model.
- Mobile: Android Studio design editor, Xcode interface builder

**The Controller mediates between the two and ensures Model and View are not connected**
- The Controller captures user actions from the View which then updates the Model. 
- The Mode notifies the Controller of changes which updates the View

**Although MVC remains fairly common in web apps, but less so in mobile today**
- MVC is still 'enforced' by frameworks like Ruby on Rails, Django, Angular, Vue and others. 
- Up until relatively recently MVC was more common with iOS apps – recently replaced by the declarative SwiftUl framework which favours MVVM. 
- Similarly with Android, although MVI was more common

## Week 11  Lecture
**Object Oriented Programming** is programming paradigm based on the concept  of “objects”, which can contain data and code: data in the form of fields(often known as attributes or properties), and code, in the form of procedures(often known as methods).
Key terms in OOP
•	Classes
•	Encapsulation
•	Inheritance
•	Polymorphism

**Programming paradigms** are a way to classify programming languages based on their features.

**Some well known paradigms**
Imperative(OOP): Provides statements that specify how a program should perform necessary computations.
Declarative(Functional): Specifies what a prog should do without describing control flow
Prototypal(part of imperative and related to OOP): Uses prototype objects rather than classes as blueprints. Shared functionality is delegated rather than inherited.

**The Solid design principles for OOP**
The solid design principles for OOP were first proposed in 2000 but have been recently updated(or defended) to address more
•	Single-responsibility principle
•	Open-closed principle
•	Liskov substitution principle
•	Interface segregation principle
•	Dependency inversion principle

**Single-responsibility principle**
“There should never be more than one reason for a class to change”.
•	Think of class and function responsibilities in terms if roles(or jobs) in a company
•	Each role should have narrowly defined responsibilities
•	Responsibilities belonging to one role should not bleed into others

**Open-closed principle**
“Software” entities(classes, modules, functions etc.)should be open for extension, but closed for modification.”
•	Consider what you’ve learned in the past about:
o	Class inheritance
o	Private and protected vs public methods
o	What might happen to a class extension if the underlying code it is based on is modified?

**Interface segregation principle**
“Many client-specific interfaces are better than one general-purpose interface.”
•	Interfaces mediate between user interactions and underlying code
•	We might think of ‘interface’ in the java sense…..
•	….or we could think about user interfaces

Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

**Do not repeat yourself(DRY) code**
•	One source of truth for all ‘knowledge in the system’.
•	Apply it to everything!
•	Code duplication can result in:
o	Bugs
o	Difficult maintenance practices
o	More line of code

**Dependency inversion principle**
•	Definition – Dependency Inversion Principle (DIP) states that high-level modules should not depend on low-level modules; both should depend on abstractions (interfaces or abstract classes).
•	Key Rules – Abstractions should not depend on details, and details (concrete implementations) should depend on abstractions.
•	Benefits – DIP reduces tight coupling, improves flexibility, enhances testability, and makes the code easier to maintain and extend.
•	Implementation – Use interfaces/abstract classes to define dependencies and inject concrete implementations via constructor injection, method injection, or dependency injection frameworks.


