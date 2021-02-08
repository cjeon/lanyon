---
layout: post
title: Effective Java 3/E summary item 21 to 25 (Longer version)
---

You can find the shorter version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-chapter-2-shorter %}).

## Item 26: Don’t use raw types

* it is legal to use raw types (generic types without their type parameters), but you should never do it. If you use raw types, you lose all the safety and expressiveness benefits of generics.
* use `<?>` instead.

## Item 27: Eliminate unchecked warnings

* When you get warnings that require some thought, persevere! Eliminate every unchecked warning that you can. If you eliminate all warnings, you are assured that your code is typesafe, which is a very good thing.
* If you can’t eliminate a warning, but you can prove that the code that provoked the warning is typesafe, then (and only then) suppress the warning with an @SuppressWarnings("unchecked") annotation.

## Item 28: Prefer lists to arrays

* Arrays and generics have very different type rules. Arrays are covariant and reified; generics are invariant and erased. As a consequence, arrays provide runtime type safety but not compile-time type safety, and vice versa for generics. As a rule, arrays and generics don’t mix well. If you find yourself mixing them and getting compile-time errors or warnings, your first impulse should be to replace the arrays with lists.

## Item 29: Favor generic types

* Generic types are safer and easier to use than types that require casts in client code. When you design new types, make sure that they can be used without such casts.

## Item 30: Favor generic methods

* Generic methods, like generic types, are safer and easier to use than methods requiring their clients to put explicit casts on input parameters and return values. Like types, you should make sure that your methods can be used without casts, which often means making them generic.

## Item 31: Use bounded wildcards to increase API flexibility

* For maximum flexibility, use wildcard types on input parameters that represent producers or consumers.
* PECS stands for producer-extends, consumer-super.

## Item 32: Combine generics and varargs judiciously

* Varargs and generics do not interact well because the varargs facility is a leaky abstraction built atop arrays, and arrays have different type rules from generics.
* If you choose to write a method with a generic (or parameterized) varargs parameter, first ensure that the method is typesafe, and then annotate it with @SafeVarargs so it is not unpleasant to use.

## Item 33: Consider typesafe heterogeneous containers

* When you need more flexibility, for example, a database row can have arbitrarily many columns, and it would be nice to be able to access all of them in a typesafe manner. Luckily, there is an easy way to achieve this effect. The idea is to parameterize the key instead of the container. Then present the parameterized key to the container to insert or retrieve a value. The generic type system is used to guarantee that the type of the value agrees with its key.

## Item 34: Use enums instead of int constants

* Enums are more readable, safer, and more powerful. Many enums require no explicit constructors or members, but others benefit from associating data with each constant and providing methods whose behavior is affected by this data.

## Item 35: Use instance fields instead of ordinals

* Never derive a value associated with an enum from its ordinal; store it in an instance field instead.

