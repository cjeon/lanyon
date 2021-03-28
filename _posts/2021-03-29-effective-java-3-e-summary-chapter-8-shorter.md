---
layout: post
title: Effective Java 3/E summary chanpter 8 (Shorter version)
---

# Chanpter 8 : General Programming

You can find the longer version of this summary [here]({% post_url 2021-02-22-effective-java-3-e-summary-item-46-to-55 %}).

1. Minimize the scope of local variables
    - Declare a varaible when it is first used
    - Keep methods small and do only one function
2. Prefer for-each loops to traditional for loops
    - Avoid using for-each loops for Destructive filtering, transfroming, parallel iteration
3. Know and use the libraries
4. Avoid float and double if exact answers are required
    - Float and double are designed for scientific and engineering calculations. (Follows `IEEE 754` floating point)
    - Use `BigDecimal`, `int` or `long`!
5. Prefer primitive types to boxed primitives
    - Null safe
    - Use `==`
    - Performance
6. Avoid strings where other types are more appropriate
    - If you use `String` as a key, it is used globally and is vulnerable to security.
7. Beware the performance of string concatenation
    - String concatenation is `O(n^2)`
8. Refer to objects by their interfaces
    - Declare interface type as possible for params, return, var, field
9. Prefer interfaces to reflection
    - Reflection: Java code exists in static area as byte code, and constructor, method, and field can be accessed only with the name of the class.
        - No type checking
        - Code smell
        - 11 times slower
    - Use `reflection` only when creating it, and refer to it by an `interface` or a `higher class`.