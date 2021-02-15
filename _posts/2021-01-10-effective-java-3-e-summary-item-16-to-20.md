---
layout: post
title: Effective Java 3/E summary item 16 to 20 (Longer version)
---

You can find the shorter version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-chapter-2-shorter %}).

## Item 16: In public classes, use accessor methods, not public fields

* The classes whose data fields are accessed directly do not offer the benefits of encapsulation. You can’t change the representation without changing the API, you can’t enforce invariants, and you can’t take auxiliary action when a field is accessed.

* Never expose mutable field in public classes - the class loses control over the field.

## Item 17: Minimize mutability

To make a class immutable, follow these five rules:

1. Don’t provide methods that modify the object’s state (known as mutators).

2. Ensure that the class can’t be extended.

3. Make all fields final.

4. Make all fields private.

5. Ensure exclusive access to any mutable components.

Why:

1. Immutable objects are simple. An immutable object can be in exactly one state, the state in which it was created.

2. Immutable objects are inherently thread-safe; they require no synchronization.

3. Not only can you share immutable objects, but they can share their internals.

4. Immutable objects make great building blocks for other objects,

5. Immutable objects provide failure atomicity for free

> Classes should be immutable unless there’s a very good reason to make them mutable.

> If a class cannot be made immutable, limit its mutability as much as possible.

## Item 18: Favor composition over inheritance

1. Inheritance violates encapsulation.

2. It is hard to enforce correct implementation rules to inheriting classes - method overriding can lead to unexpected result. 

3. Parent class may add additional methods - child class that never changed can cause unexpected results.

* Instead of extending an existing class, give your new class a private field that references an instance of the existing class.

> inheritance is powerful, but it is problematic because it violates encapsulation. It is appropriate only when a genuine subtype relationship exists between the subclass and the superclass. Even then, inheritance may lead to fragility if the subclass is in a different package from the superclass and the superclass is not designed for inheritance. To avoid this fragility, use composition and forwarding instead of inheritance, especially if an appropriate interface to implement a wrapper class exists. Not only are wrapper classes more robust than subclasses, they are also more powerful.

## Item 19: Design and document for inheritance or else prohibit it

It is so easy for other engineers to be "wrong" when inheriting your class so design and document for inheritance, or else prohibit it.

* The only way to test a class designed for inheritance is to write subclasses. Test your class by writing subclasses before you release it.

* Constructors must not invoke overridable methods, directly or indirectly.

* Designing a class for inheritance requires great effort and places substantial limitations on the class.

## Item 20: Prefer interfaces to abstract classes

* A major difference is that to implement the type defined by an abstract class, a class must be a subclass of the abstract class.

* Existing classes can easily be retrofitted to implement a new interface. All you have to do is to add the required methods, if they don’t yet exist, and to add an implements clause to the class declaration. Existing classes cannot, in general, be retrofitted to extend a new abstract class. If you want to have two classes extend the same abstract class, you have to place it high up in the type hierarchy where it is an ancestor of both classes. Unfortunately, this can cause great collateral damage to the type hierarchy, forcing all descendants of the new abstract class to subclass it, whether or not it is appropriate.

* You can, however, combine the advantages of interfaces and abstract classes by providing an abstract skeletal implementation class to go with an interface. The interface defines the type, perhaps providing some default methods, while the skeletal implementation class implements the remaining non-primitive interface methods atop the primitive interface methods. Extending a skeletal implementation takes most of the work out of implementing an interface. This is the Template Method pattern.
