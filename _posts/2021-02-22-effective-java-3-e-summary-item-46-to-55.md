---
layout: post
title: Effective Java 3/E summary item 46 to 55 (Longer version)
---

You can find the shorter version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-chapter-2-shorter %}).

## Item 46: Prefer side-effect-free functions in streams

* Streams isn’t just an API, it’s a paradigm based on functional programming.

* The essence of programming stream pipelines is side-effect-free function objects.

## Item 47: Prefer Collection to Stream as a return type

* If an API returns only a stream and some users want to iterate over the returned sequence with a for-each loop, those users will be justifiably upset.

* The only thing preventing programmers from using a for-each loop to iterate over a stream is `Stream`’s failure to extend `Iterable`.

* But do not store a large sequence in memory just to return it as a collection. If the sequence you’re returning is large but can be represented concisely, consider implementing a special-purpose collection.

## Item 48: Use caution when making streams parallel

* Writing concurrent programs in Java keeps getting easier, but writing concurrent programs that are correct and fast is as difficult as it ever was.

* Do not parallelize stream pipelines indiscriminately.

* An acquaintance who maintains a multimillion-line codebase that makes heavy use of streams found only a handful of places where parallel streams were effective.

## Item 49: Check parameters for validity

* Each time you write a method or constructor, you should think about what restrictions exist on its parameters. You should document these restrictions and enforce them with explicit checks at the beginning of the method body.

## Item 50: Make defensive copies when needed

* You must program defensively, with the assumption that clients of your class will do their best to destroy its invariants.

## Item 51: Design method signatures carefully

* Choose method names carefully.

* Don’t go overboard in providing convenience methods.

* Avoid long parameter lists. Aim for four parameters or fewer.

* For parameter types, favor interfaces over classes.

## Item 52: Use overloading judiciously

* You should avoid confusing uses of overloading.

* A safe, conservative policy is never to export two overloadings with the same number of parameters.

## Item 53: Use varargs judiciously

* varargs are effective in circumstances where you want a method with a variable number of arguments, but every invocation of a varargs method causes an array allocation and initialization.

## Item 54: Return empty collections or arrays, not nulls

* Never return null in place of an empty array or collection. It makes your API more difficult to use and more prone to error, and it has no performance advantages.

## Item 55: Return optionals judiciously

* If you find yourself writing a method that can’t always return a value and you believe it is important that users of the method consider this possibility every time they call it, then you should probably return an optional.

* Container types, including collections, maps, streams, arrays, and optionals should not be wrapped in optionals.

* You should be aware that there are real performance consequences associated with returning optionals; for performance-critical methods, it may be better to return a null or throw an exception.

* You should rarely use an optional in any other capacity than as a return value.