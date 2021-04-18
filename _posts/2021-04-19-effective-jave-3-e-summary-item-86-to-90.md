---
layout: post
title: Effective Java 3/E summary item 86 to 90 (Longer version)
---

## Item 86: Implement Serializable with great caution

* it decreases the flexibility to change a class’s implementation once it has been released.
* it increases the likelihood of bugs and security holes.
* it increases the testing burden associated with releasing a new version of a class.

## Item 87: Consider using a custom serialized form

* Use the default serialized form only if it is a reasonable description of the logical state of the object; otherwise design a custom serialized form that aptly describes the object.
* Choosing the wrong serialized form can have a permanent, negative impact on the complexity and performance of a class.

## Item 88: Write readObject methods defensively

* For classes with object reference fields that must remain private, defensively copy each object in such a field. Mutable components of immutable classes fall into this category.
* Check any invariants and throw an InvalidObjectException if a check fails. The checks should follow any defensive copying.
* If an entire object graph must be validated after it is deserialized, use the ObjectInputValidation interface (not discussed in this book).
* Do not invoke any overridable methods in the class, directly or indirectly.

## Item 89: For instance control, prefer enum types to readResolve

* Use enum types to enforce instance control invariants wherever possible.
* If this is not possible and you need a class to be both serializable and instance-controlled, provide a readResolve method and ensure that all of the class’s instance fields are either primitive or transient.

## Item 90: Consider serialization proxies instead of serialized instances

* consider the serialization proxy pattern whenever you find yourself having to write a readObject or writeObject method on a class that is not extendable by its clients.
