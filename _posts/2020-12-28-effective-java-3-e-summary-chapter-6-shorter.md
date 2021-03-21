---
layout: post
title: Effective Java 3/E summary chanpter 3 (Shorter version)
---

# Chanpter 6 : Lambda and Stream

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

- Java 8, Android API 24 or higher

## Lambda
- Use Lambda instaed of an anonymous class
- Anonymous class < Lambda < Method reference
    - If the readability seems to be poor, use Lambda instaed of Method reference
- Standard functional interface (java.util.function)
    - 43 in total : 6 basic types can be extended
        - `UnaryOperator` : 1 argument, argument type = return type
        - `BinaryOperator` : 2 arguments, argument type = return type
        - `Predicate` : 1 argument, return booelan
        - `Function` : 1 argument, argument type != return type
        - `Supplier` : Returns a value without arguments
        - `Consumer` : 1 argument, return void
        - Transform 3 pieces each for `int`, `long`, and `double`
        - 9 transformations from `Function` to SrcToRes
        - transformation that takes 2 arguments (`Predicate`, `Function`, `Consumer`)
        - 2 arguments + return basic type `Fuction`
        - 1 argument + argument basic type `Consumer`
        - `Supplier` that returns Boolean

## Stream
- Replace loop (`for`, `while`)
- Change the loop to `Stream` and consider readability
- Cannot be changed to `Stream` when
    - local variables need to be modified
    - `return`, `break`, `continue`, `exception` is implemented
- Use `java.util.stream.Collectors` methods for reducing side-effects
    - `toList`, `toSet`, `toMap`, `groupingBy`, `joining`
- Best return type is `Collection`!
    - `Collection` can be both (Iterable, Stream).
    - Tremendous sequence can be replaced to `AbstractCollecion`.
- For `parallel()`, consider whether (the number of elements * the number of implemented codes > Hundreds of thousands)