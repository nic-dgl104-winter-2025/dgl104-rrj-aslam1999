[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MMj2nZMu)

# Research and Reflection Journal

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

**Example:**
You're reviewing a **mobile food delivery app**.
Interface/UX: Looks clean, easy to navigate, with smooth animations.
**Developer’s Assessment:**
**Framework:** You recognize the app is built using React Native, due to the component structure and navigation style.
**Libraries:** You inspect the network traffic and notice use of Axios for API calls.
**API Design:** You notice the app uses REST APIs but lacks proper error handling—if the server returns a 500 error, the app crashes instead of showing a message.
**Data Structures:** Cart data seems to be stored in a flat object, which may become hard to manage if items have multiple options (e.g. toppings, size).
**Platform Conventions:** On Android, the back button doesn’t behave as expected (doesn’t close modals or navigate back correctly), which breaks Android UX norms.
As a developer, you not only evaluate how the app feels but also how it’s built, helping identify performance issues, architectural flaws, or areas for optimization.

**User stories are a common tool employed in the design of user-facing systems**
• User stories are written in natural language from the perspective of the user
• Typically written in the form: "As a user, I can "
• User stories facilitate intra-team communication

**Example:**
User story for a food delivery app: "As a user, I can browse a variety of cuisines and restaurants so that I can choose the food I crave."
This user story highlights a feature request from the user's perspective, allowing developers to understand and design functionality. User stories like this bridge communication between team members, ensuring the end-user experience remains central throughout development.

**The downside of user stories is the lack of implementation details**
• Typically written without immediate consideration of technical constraints.  
• Issues related to technical considerations are sometimes overlooked (e.g. performance criteria).
• User stories can be written with technical concerns in mind, but this may not be an ideal approach.

**Example:**
User Story: "As a user, I can receive notifications when someone replies to my post so that I stay updated."
This sounds simple, but from a developer’s perspective, many questions arise:
Should notifications be real-time (e.g. WebSocket), periodic (e.g. email digests), or push notifications?
What if a user gets 100 replies at once? Will it send 100 notifications?
Should the system respect user notification preferences?
How will this affect performance during high traffic?
Without these details, developers may implement a system that:
Sends too many notifications and overwhelms the user.
Consumes too much server bandwidth.
Misses critical edge cases (e.g. handling offline users).

**A technical design document (TDD) is a written artefact that addresses technical concerns in a design context**
• Goal: Produce an unambiguous document detailing:
• Architecture
• Feature implementation
• Testing plan
• Performance criteria
• There is no accepted standard for the development of TDDs.
• TDDs can encompass a complete software design, or specific features

**Example:**
Password Reset Feature:
**Architecture:** React (frontend), Node.js/Express (backend), MongoDB (database), AWS SES (email service).
**Feature Implementation:** User clicks "Forgot Password" → Token generated and emailed → User resets password via link → System updates password securely.
**Testing Plan:** Unit tests for token and hashing logic; UI tests for reset flow.
**Performance Criteria:**
Token validation under 200ms,
Email sent within 1 second,
Handle 1000 reset requests/min.

**Functional requirements describe software features on an input/output basis**
• Just like 'functions' in programming (or in mathematics).
• These may be included in a TDD, or related document.
• Typically derived from user stories, or from use cases (a more technical-first approach to modeling systems).

**We can use the input/output approach to develop clear 'specifications' for our apps**
• Functional requirements and specifications are part of the standard software engineering toolkit...
• If our user story says: "as a forum user I can see posters' profile pictures as avatars", this might imply the following set of functional requirements:
• Update profile: Enter required profile data (name, email) and optional profile data (profile pic, address, website, social accounts) -> return profile page with default content (e.g. default avatar) for incomple optional data.

**Example:**
Functional Requirements for a Banking App:
Login Functionality:
Input: User credentials (username and password).
Output: Access granted to the user's account if credentials are valid; otherwise, an error message.

## Week 9 Lecture

**Design Patterns:**
• They are reusable fragments of code that provide a solution to a specific – and typically well-understood-coding problem.
• They really do nothing at the time of coding but really help to encounter common problems in the code.
• Long-term maintainability of a codebase is the main advantage of design patterns.

**Example:** Singleton Pattern.

Problem: You want to ensure that only one instance of a class (e.g., a configuration manager or database connection) exists throughout the app.
Solution (Singleton Pattern):

```
class ConfigManager {
    constructor() {
    if (ConfigManager.instance) {
        return ConfigManager.instance;
    }
        this.settings = {};
        ConfigManager.instance = this;
    }
}
```

**Design patterns are accepted solutions to common well-defined problems**
• Popularized by the ‘Gang of Four’ and Design Patters: Elements of Reusable Object-Oriented Software.
• Based on OOP principles:

1. “Program to an interface, not an implementation”.
2. “Favor ‘object composition’ over ‘class inheritance’.”

**Example:** Strategy Pattern.
Problem: You have multiple algorithms (e.g., for sorting or payment methods), and you want to switch between them at runtime without changing the core logic.
OOP Principles Used:
• Program to an interface: Define a common interface for all strategies
• Favor composition over inheritance: Use objects (strategies) instead of hard-coded logic

**In OOP we reply on the inheritance chain to share data and behaviour**
• In the typical OOP approach one might write inherited classes that are meant to interact in some way.
• But what happens when you need your BMW to fill up at the pump? Where do the methods(behaviour) live?
• If Vehicle is a base class, then Car will be derived class 1 and the BMW would be derived class 2.
• Service station is base class, then Shell will be derived class and pump as well.

**Example:**
A Vehicle class may define general behaviors like start() or stop().
A Car class inherits from Vehicle, and a specific car like BMW inherits from Car.
Similarly, a ServiceStation class might define behaviors like refuel(), and ShellStation is a specific type of service station.

Pseudocode: Inheritance – Start and Stop Example

```
Class Vehicle:
Method start():
Print "Vehicle started"

    Method stop():
        Print "Vehicle stopped"

Class Car inherits Vehicle:
// Inherits start() and stop()

Class BMW inherits Car:
// Inherits start() and stop()

// Usage
bmw = new BMW()
bmw.start() // Output: Vehicle started
bmw.stop() // Output: Vehicle stopped
```

**“[Programming] to an interface” means to write a “shared contract” for implementations**
• An interface is an abstract definition of some behavior that you want your objects to implement.
• This has the benefit of keeping your class definitions clean and making testing easier.
• The pump interface could be implemented for non-car classes (e.g. aeroplanes).

**Example:** Pump Interface

```
Interface Pumpable:
Method refuel()

Class Car implements Pumpable:
Method refuel():
Print "Refueling car"

Class Airplane implements Pumpable:
Method refuel():
Print "Refueling airplane"

// Usage
Function refillAtPump(pumpable: Pumpable):
pumpable.refuel()

car = new Car()
plane = new Airplane()

refillAtPump(car) // Output: Refueling car
refillAtPump(plane) // Output: Refueling airplane
```

The Pumpable interface defines what should be done, not how.
Both Car and Airplane implement the same interface differently, but can be used interchangeably in functions like refillAtPump().

**Similarly, relying solely on inheritance chains for behaviour can be limiting**
• Inheritance chains can lock you into dangerous patterns that produce brittle code, or over-engineered code.
• Object composition allows data and behaviour from related objects to be “composed” into more complex objects that meet behaviour requirements.
• This is related to the idea of function composition and higher-order functions in functional programming paradigm.

**Example:** Object Composition.
No need for complex class inheritance — just compose what you need.

```
// Reusable behavior objects
const move = {
  move: () => console.log("Moving")
};

const honk = {
  honk: () => console.log("Honking")
};

const charge = {
  charge: () => console.log("Charging battery")
};

// Compose behaviors
const car = { ...move, ...honk };
const electricCar = { ...move, ...honk, ...charge };
const electricBike = { ...move, ...charge };

// Use them
car.honk();           // Honking
electricBike.charge(); // Charging battery
```

**Design patters are typically categorized into three solution-based classifications**
• Creational patterns are used for creating objects(sometimes many objects) in a predictable way.
• Structural patterns are used for composing classes into larger structures with more complex behavior
• Behavioural patterns are used to support common communication patterns between distinct objects

**Example:**

1. Creational Pattern (e.g., Factory Pattern)
   Example: Coffee machine
   You press a button for Espresso or Latte.
   The machine knows how to create each type of coffee.
   You don’t need to know the detailed process.
   Purpose: Hide complex creation logic behind a simple interface.
2. Structural Pattern (e.g., Adapter Pattern)
   Example: Travel plug adapter
   You have a European plug but a US socket.
   You use an adapter to make them work together.
   Purpose: Allow incompatible systems to work together smoothly.
3. Behavioral Pattern (e.g., Observer Pattern)
   Example: YouTube channel notifications
   You subscribe to a channel.
   When a new video is uploaded, you get notified.
   Purpose: One-to-many communication — one subject notifies many observers.

**The Singleton pattern ensures that there is only ever one instance of a particular class**
• Responsibility: managing a common resource, or program state
• A creational pattern
• Typically globally available
• The class definition makes creating instances of the class impossible via:
• Private constructors
• Public getInstance() method that returns a static instance.

**Example:**
Singleton Pattern. Real-World Example - President of a Country.
There is only one president at a time.
No one can just "create" a new president.
If someone needs to talk to the president, they are directed to the same person.
A special system ensures that only one instance exists and is used everywhere.
How This Relates to the Singleton Pattern:
One instance: Only one president exists — like only one instance of the class.
Private constructor: You can’t randomly create new presidents — like you can’t create new instances.
Public method to access: Everyone accesses the president through a controlled channel — like a getInstance() method.

**The Observer pattern notifies observers of state changes so that they can update correctly**
• Responsibility: subjects keep a list of observers, observers subscribe and unsubscribe to subjects
• A behavioral pattern
• Notifications are one-to-many
• Subjects don’t care how many observers they have
• Ideally subject and observer are loosely couples.
• For example: In an auction, If auctioneer is subject then the bidders would be observers.
**How It Works:**
The auctioneer announces a new bid (state change).
All bidders are immediately notified of the new price.
Each bidder decides how to react (e.g., place a new bid or wait).
Bidders can join or leave the auction at any time.
The auctioneer doesn't care who or how many bidders are observing.

**Design patterns aren’t bullet proof solutions to all problems, however**
• Some have stated that design patterns are really ‘kludge’ solutions to missing features in programming languages
• Design patterns are paradigmatic by nature- the common design patterns won’t naturally fit other programming paradigms
• Hammers and nails…

**Example:**
Using a hammer to screw in a bolt.
A hammer is great for nails — it's designed for that.
But if you try to use it on a bolt, it’s not the right tool — it may work poorly or damage the bolt.
You really need a wrench (a better-suited tool for bolts).

**Anti-patterns on other hand, demonstrate common patterns you should avoid**
• Originally inspired by the Gang of Four design patterns.
• Has been applied more broadly than exclusively to software(tend to be used in management studies).
• The best way to avoid anti-patterns
• Code review - let others catch bad patterns early.
• Style guides - set standards to keep code clean and consistent.
• Idiomatic code - write code that follows the natural style of the language.

**Few Design patterns used in software industry**

1. Creational DP - Singleton, Factory, Builder, Prototype
2. Structural DP – Adapter, Decorator, Façade, Composite
3. Behavioral DP – Observer, Strategy, Command, State

## Week 10 Class: MV Patterns

**MV\* refers to the collection of user interface architecture patterns using Model and View**

- Model View Controller (MVC)
- Model View Presenter (MVP)
- Model View Adapter (MVA)
- Model View Intent (MVI)
- Model View ViewModel (MVVM)

**Example:**

1. Model-View-Controller (MVC) - Web App (e.g., Instagram)
   Model: Holds the data (user profile, posts).
   View: Displays posts and profile to the user.
   Controller: Handles user actions like clicking "Like" or "Comment", and updates the model.
   Controller connects Model ↔ View

2. Model-View-Presenter (MVP) - Android App with Buttons
   Model: Business logic and data (e.g., settings, saved values).
   View: UI (e.g., buttons, text fields).
   Presenter: Handles logic and updates the View manually.
   Presenter actively updates View after Model changes

3. Model-View-Adapter (MVA) - A data-driven list in a mobile app
   Model: Data items (e.g., contacts).
   View: UI that displays each contact.
   Adapter: Converts model data into a form the view can use.
   Adapter helps bridge Model and View with formatting/mapping

4. Model-View-Intent (MVI) - Reactive app (e.g., stock price tracker)
   Model: Reactive data (stock prices).
   View: Charts/UI.
   Intent: User actions (e.g., select company), which feed into state updates.
   Everything flows one-way: Intent → Model → View

5. Model-View-ViewModel (MVVM) - Modern mobile apps (e.g., weather apps using LiveData)
   Model: Weather data (from an API).
   View: UI showing temperature, forecast.
   ViewModel: Binds UI with data using observers (auto-updates View when data changes).
   ViewModel manages data logic, View just listens

**Model View Controller was the first; Model View ViewModel is common in apps today**

- MVC developed as part of Smalltalk at Apple.
- MVC became an integral part of iOS development.
- MVC is a key architectural pattern on the web (Django, Ruby on Rails).
- MVVM is presently the most commonly used in app development
  - Mobile: Jetpack Compose, SwiftUl
  - There are some MVVM-specific web frameworks too

**The common thread across all MV\* patterns is separation of concerns and testable code**

- The Model contains the business logic of the app.
- The View represents all app data and captures user interactions.
- The Model and View should never intersect -separation of concerns.
- All MV\* patterns are graphical in nature – GUI architecture.

**Model View Controller (MVC) is a user interface design / architecture pattern**

- Sometimes referred to as a design pattern...
- Sometimes referred to as an architectural pattern...
- All MV\* patterns are user interface driven

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

**Example:** To-Do List App using MVC

1. Model (Business Logic & Data) - Stores and manages the task data.

```
Task {
  id: 1,
  title: "Submit assignment",
  completed: false
}
```

Handles: adding, removing, editing tasks.
No awareness of the UI or user actions.

2. View (User Interface) - Displays the list of tasks and user controls.

   - [ ] Submit assignment [Mark Complete] [Delete]
   - Just shows the data — no logic or state.
   - Doesn't decide how tasks are added or changed.

3. Controller (Mediator) - Acts as the bridge between Model and View. Captures user interaction from the View:
   e.g., "Mark Complete" button clicked.
   Updates the Model with the action:
   Task is marked as completed.
   Gets updated data from Model and updates the View.

Real-World Contexts:
iOS (UIKit): You build your Views in Interface Builder (Storyboard), and use ViewControllers to connect logic and UI.
Web: Frameworks like Django, Ruby on Rails, and ASP.NET use MVC to separate HTML (View), backend logic (Model), and routing (Controller).

## Week 11 Lecture

**Object Oriented Programming** is programming paradigm based on the concept of “objects”, which can contain data and code: data in the form of fields(often known as attributes or properties), and code, in the form of procedures(often known as methods).
Key terms in OOP:

• Classes - A class is a blueprint or template for creating objects. Example: A Car class defines what a car is and can do.

• Encapsulation - concept of bundling data (attributes) and methods (functions) that operate on that data into a single unit — the object.It also hides internal details from the outside world to protect the object's integrity. Example: You can access a car's speed using a method, but you can't directly change its engine behavior.

• Inheritance - mechanism that allows one class (child or subclass) to inherit the properties and methods of another class (parent or superclass). Example: A ElectricCar class can inherit from the Car class and add its own charge() method.

• Polymorphism - Polymorphism means "many forms" — the same method name can behave differently depending on the object calling it. Example: Both Car and ElectricCar can have a drive() method, but each can implement it differently.

**Programming paradigms** are a way to classify programming languages based on their features.

**Some well known paradigms**
Imperative(OOP): Provides statements that specify how a program should perform necessary computations.
Declarative(Functional): Specifies what a program should do without describing control flow.
Prototypal(part of imperative and related to OOP): Uses prototype objects rather than classes as blueprints. Shared functionality is delegated rather than inherited.

**Example:**

1. Imperative (Object-Oriented Programming) -
   You define a class, create an object, and call a method to perform an action.

```OOP in Python
class Dog:
    def bark(self):
        print("Woof!")

d = Dog()
d.bark()
```

2. Declarative (Functional Programming) -
   Focuses on what the program should accomplish, not how to do it.

```
// Example: Declarative style in JavaScript using map
const numbers = [1, 2, 3];
const squares = numbers.map(n => n * n);
console.log(squares); // [1, 4, 9]
```

3. Prototypal (Prototype-based OOP in JavaScript)

```
const animal = {
  speak() {
    console.log("Animal speaks");
  }
};

const dog = Object.create(animal);
dog.speak(); // Inherits method from animal
```

**The Solid design principles for OOP**
The solid design principles for OOP were first proposed in 2000 but have been recently updated(or defended) to address more
• Single-responsibility principle
• Open-closed principle
• Liskov substitution principle
• Interface segregation principle
• Dependency inversion principle

**Single-responsibility principle**
“There should never be more than one reason for a class to change”.
• Think of class and function responsibilities in terms if roles(or jobs) in a company
• Each role should have narrowly defined responsibilities
• Responsibilities belonging to one role should not bleed into others

**Example:** Split responsibilities into two classes

```
class UserManager:
    def add_user(self, user): ...

class FileManager:
    def save_to_file(self, user): ...
```

**Open-closed principle**
“Software” entities(classes, modules, functions etc.)should be open for extension, but closed for modification.”
• Consider what you’ve learned in the past about:
o Class inheritance
o Private and protected vs public methods
o What might happen to a class extension if the underlying code it is based on is modified?

**Example:**
Use polymorphism instead of modifying the class

```
class Notification:
    def send(self, message): pass

class EmailNotification(Notification):
    def send(self, message):
        print("Email:", message)

class SMSNotification(Notification):
    def send(self, message):
        print("SMS:", message)
```

Easily extend by adding new types without changing old code

**Interface segregation principle**
“Many client-specific interfaces are better than one general-purpose interface.”
• Interfaces mediate between user interactions and underlying code
• We might think of ‘interface’ in the java sense…..
• ….or we could think about user interfaces

Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

**Example:** Smaller, segregated interfaces

```
class Printer:
    def print(self): ...

class Scanner:
    def scan(self): ...
```

**Do not repeat yourself(DRY) code**
• One source of truth for all ‘knowledge in the system’.
• Apply it to everything!
• Code duplication can result in:
o Bugs (if you update logic in one place but forget another).
o Difficult maintenance practices.
o More lines of code.
**Benefits of DRY Code:**
• Easier Maintenance: Changing the tax calculation logic only requires editing the single calculate_tax functio
• Reduced Bugs: Less code duplication minimizes the risk of inconsistencies.
• Compact Code: Fewer lines of code improve readability.

**Dependency inversion principle**
• Definition – Dependency Inversion Principle (DIP) states that high-level modules should not depend on low-level modules; both should depend on abstractions (interfaces or abstract classes).
• Key Rules – Abstractions should not depend on details, and details (concrete implementations) should depend on abstractions.
• Benefits – DIP reduces tight coupling, improves flexibility, enhances testability, and makes the code easier to maintain and extend.
• Implementation – Use interfaces/abstract classes to define dependencies and inject concrete implementations via constructor injection, method injection, or dependency injection frameworks.

**Example:** Depends on an abstraction

```
class Notification:
    def __init__(self, service):
        self.service = service

    def notify(self, message):
        self.service.send(message)
```

````

```

```
````

## Rest of the weeks, I have completely worked on my final project and this reflection journal.
**Citations:**
1. Class videos by Ashley for class content
2. AI for examples
Note : Both are just references.