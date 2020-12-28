---
layout: post
title: Effective Java 3/E summary item 6 to 10 (Longer version)
---

You can find the shorter version of this summary [here]({% post_url 2020-12-22-effective-java-3-e-summary-chapter-1-shorter %}).

## Item 6: Avoid creating unnecessary objects

* An object can always be reused if it is immutable.
  * We can avoid creating unnecessary objects by using static factory methods - constructor is required to create a new object while static factory methods is not.
* Even if an object is mutable, it can be reused if all mutable fields won't be modified.
* Be careful with "expensive" objects. For example, using `String.matches` in a loop could greatly reduce performance since it internally creates an expensive `Pattern` instance.
  * Lazy initialization could also help, but this complicates the implementation. Measure the improvement before and after the optimization.
* Adapters or views can always reused since its only state is the backing object. (ex: every call to `Map#keySet` returns a functionally identical object)
* Prefer primitives to boxed primitives and be careful with the unintentional autoboxing.

## Item 7: Eliminate obsolete object references

* Define variables in the narrowest possible scope.
* Whenever a class manages its own memory, the programmer should be alert for memory leaks.
* Caches are source of the leak too.
  * Using `WeakHashMap` may help. But use this class only when the lifetime of the entry depends on the entry's key not the value.
  * Using `LinkedHashMap` deletes old entries so this could also be helpful.
* Listeners and other callbacks are sources of a leak too. Maintaining only a weak reference to them can help.

## Item 8: Avoid finalizers and cleaners

* Finalizers are unpredictable, often dangerous, and generally unnecessary.
* The Java 9 replacement for finalizers is cleaners. Cleaners are less dangerous than finalizers, but still unpredictable, slow, and generally unnecessary.
* There is no guarantee that finalizers or cleaners will run at all.
* There is a severe performance penalty for using finalizers and cleaners.
* Finalizers have a serious security problem: they open your class up to finalizer attacks.
* Just have your class implement AutoCloseable, and require its clients to invoke the close method on each instance when it is no longer needed.

## Item 9: Prefer try-with-resources to try-finally

* When a second exception occurs during handling a first exception occurred in a nested try-finally clauses, the first exception is hidden. Use try-with-resources can resolve this issue.

You can find the shorter version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-chapter-2-shorter %}).

## Item 10: Obey the general contract when overriding equals

It is when a class has a notion of logical equality that differs from mere object identity, it is appropriate to override equals.

We don't have to implement equals if:

* Each instance of the class is inherently unique. (e.g. `Thread`)
* There is no need for the class to provide a “logical equality” test. (e.g. `Pattern`)
* There is no need for the class to provide a “logical equality” test.
* The class is private or package-private, and you are certain that its equals method will never be invoked.

The equals method implements an equivalence relation. It has these properties:

* Reflexive: For any non-null reference value x, x.equals(x) must return true.
* Symmetric: For any non-null reference values x and y, x.equals(y) must return true if and only if y.equals(x) returns true.
* Transitive: For any non-null reference values x, y, z, if x.equals(y) returns true and y.equals(z) returns true, then x.equals(z) must return true.
* Consistent: For any non-null reference values x and y, multiple invocations of x.equals(y) must consistently return true or consistently return false, provided no information used in equals comparisons is modified.
* For any non-null reference value x, x.equals(null) must return false.

Notes:

* There is no way to extend an instantiable class and add a value component while preserving the equals contract,
* Do not break the Liskov subsitution principle: any important property of a type should also hold for all its subtypes so that any method written for the type should work equally well on its subtypes
* Whether or not a class is immutable, do not write an equals method that depends on unreliable resources. (Consistency)
* Always override hashCode when you override equals.
* Don’t try to be too clever. It is generally a bad idea to take any form of aliasing into account. For example, the File class shouldn’t attempt to equate symbolic links referring to the same file.
