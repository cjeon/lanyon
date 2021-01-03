---
layout: post
title: Effective Java 3/E summary item 11 to 15 (Longer version)
---

You can find the shorter version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-chapter-2-shorter %}).

## Item 11: Always override hashCode when you override equals

You must override hashCode in every class that overrides equals.

* If two objects are equal according to the equals(Object) method, then calling hashCode on the two objects must produce the same integer result.

> equal objects must have equal hash codes.

* A good hash function tends to produce unequal hash codes for unequal instances. Ideally, a hash function should distribute any reasonable collection of unequal instances uniformly across all int values.

* Don’t provide a detailed specification for the value returned by hashCode, so clients can’t reasonably depend on it; this gives you the flexibility to change it.

## Item 12: Always override toString

* The general contract for toString says that the returned string should be “a concise but informative representation that is easy for a person to read.”

* Providing a good toString implementation makes your class much more pleasant to use and makes systems using the class easier to debug.

* Override Object’s toString implementation in every instantiable class you write, unless a superclass has already done so.

## Item 13: Override clone judiciously

* A class implementing Cloneable is expected to provide a properly functioning public clone method. In order to achieve this, the class and all of its superclasses must obey a complex, unenforceable, thinly documented protocol. The resulting mechanism is fragile, dangerous, and extralinguistic: it creates objects without calling a constructor.

* You are usually better off providing an alternative means of object copying. A better approach to object copying is to provide a copy constructor or copy factory.

## Item 14: Consider implementing Comparable

* Virtually all of the value classes in the Java platform libraries, as well as all enum types (Item 34), implement Comparable.

* whenever you implement a value class that has a sensible ordering, you should have the class implement the Comparable interface so that its instances can be easily sorted, searched, and used in comparison-based collections.

* When comparing field values in the implementations of the compareTo methods, avoid the use of the < and > operators. Instead, use the static compare methods in the boxed primitive classes or the comparator construction methods in the Comparator interface.

## Item 15: Minimize the accessibility of classes and members

* This concept, known as information hiding or encapsulation, is a fundamental tenet of software design.

* Information hiding is important for many reasons, most of which stem from the fact that it decouples the components that comprise a system, allowing them to be developed, tested, optimized, used, understood, and modified in isolation.

> The rule of thumb is simple: make each class or member as inaccessible as possible.  

> If you make it public, you are obligated to support it forever to maintain compatibility.

* It is acceptable to make a private member of a public class package-private in order to test it, but it is not acceptable to raise the accessibility any higher. In
