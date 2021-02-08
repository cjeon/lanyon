---
layout: post
title: Effective Java 3/E summary chanpter 3 (Shorter version)
---

# Chanpter 4 : Generic

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

## When to use Generics?
- If something is expressed as `Object`, use Generics.
- If there is a class or method in which type conversion occurs, use Generics. (For methods)
- When using Generics, the type is specified at compile time and the client doesn't need type-casting.
- When using a container of a variable type, consider using a type-safe heterogeneous container with `Class<T>` as the type token.

## Characteristics of Generics
- Invariant : Generic classes declared as different types are of different types.
- Type check at compile time.
- Type information is erased at runtime.

## Precautions for Generics
- Do not use the raw type because it exists due to compatibility with existing Java (it is difficult to find a bug at compile time)
- Do not use Generics with arrays
    - Generics don't reify, whereas arrays reify. (The array type is unknown at runtime)
- Since variable arguments are arrays, make sure to be type-safe to use with Generics and attach `@SafeVarargs`.


## Use of Wildcards
- Using wildcards makes the public API much more flexible. (Client doesn't need type declaration)
- If type parameter appears only once in the method declaration, replace it with a wildcard.
- Recursive type limitation
```java
<E extends Comparable<E>> // Any type E can be compared.
<T extends Builder<T>> // Any type T implement Builder.
```
- PECS: producer-extends, consumer-super