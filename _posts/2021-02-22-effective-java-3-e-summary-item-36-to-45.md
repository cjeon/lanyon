---
layout: post
title: Effective Java 3/E summary item 36 to 45 (Longer version)
---

You can find the shorter version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-chapter-2-shorter %}).

## Item 36: Use EnumSet instead of bit fields

* Bit fields are inefficient and using it decreases readability. The EnumSet class combines the conciseness and performance of bit fields with all the many advantages of enum types described in Item 34. Use enum set instead.

## Item 37: Use EnumMap instead of ordinal indexing

* Ordinals are subject to change and compilers cannot check its usage. It is rarely appropriate to use ordinals to index into arrays: use EnumMap instead.

## Item 38: Emulate extensible enums with interfaces

* Enums are not extensible so create an interface and make subtype enums implement that interface to mimic extensible enum. 

## Item 39: Prefer annotations to naming patterns

* Annotation processor and compiler knows about annotation but not naming patterns.
* Most programmers will have no need to define annotation types. But all programmers should use the predefined annotation types that Java provides.

## Item 40: Consistently use the Override annotation

* The compiler can protect you from a great many errors if you use the Override annotation on every method declaration that you believe to override a supertype declaration,

## Item 41: Use marker interfaces to define types

* A marker interface is an interface that contains no method declarations but merely designates (or “marks”) a class that implements the interface as having some property. (e.g. `Serializable`)

## Item 42: Prefer lambdas to anonymous classes

* lambdas are clearer and more concise.
* Omit the types of all lambda parameters unless their presence makes your program clearer.

## Item 43: Prefer method references to lambdas

* When you use method reference, you can eliminate boilerplate codes. The more parameters a method has, the more boilerplate you can eliminate with a method reference.
* The more parameters a method has, the more boilerplate you can eliminate with a method reference.

## Item 44: Favor the use of standard functional interfaces

* This will make your API easier to learn, by reducing its conceptual surface area, and will provide significant interoperability benefits, as many of the standard functional interfaces provide useful default methods.

## Item 45: Use streams judiciously

* Stream pipelines are evaluated lazily: evaluation doesn’t start until the terminal operation is invoked, and data elements that aren’t required in order to complete the terminal operation are never computed.
* Overusing streams makes programs hard to read and maintain.