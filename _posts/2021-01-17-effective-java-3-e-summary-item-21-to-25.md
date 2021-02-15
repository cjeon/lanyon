---
layout: post
title: Effective Java 3/E summary item 21 to 25 (Longer version)
---

You can find the shorter version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-chapter-2-shorter %}).

## Item 21: Design interfaces for posterity

* Using default methods to add new methods to existing interfaces should be avoided unless the need is critical, in which case you should think long and hard about whether an existing interface implementation might be broken by your default method implementation.

* Default methods are, however, extremely useful for providing standard method implementations when an interface is created, to ease the task of implementing the interface.

> it is critically important to test each new interface before you release it. Multiple programmers should implement each interface in different ways. At a minimum, you should aim for three diverse implementations.

## Item 22: Use interfaces only to define types

* constant interface - an interface contains no methods and consists solely of static final fields (constants) should be avoided.

## Item 23: Prefer class hierarchies to tagged classes

> In short, tagged classes are verbose, error-prone, and inefficient. (less readable, more boilerplate, more memory footprint, non-final states...)

## Item 24: Favor static member classes over nonstatic

* If you declare a member class that does not require access to an enclosing instance, always put the static modifier in its declaration, making it a static rather than a nonstatic member class. If you omit this modifier, each instance will have a hidden extraneous reference to its enclosing instance.

## Item 25: Limit source files to a single top-level class

* While the Java compiler lets you define multiple top-level classes in a single source file, there are no benefits associated with doing so, and there are significant risks.
