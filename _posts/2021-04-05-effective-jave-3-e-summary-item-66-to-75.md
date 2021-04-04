---
layout: post
title: Effective Java 3/E summary item 56 to 65 (Longer version)
---

## Item 66: Use native methods judiciously

* It is rarely advisable to use native methods for improved performance. In early releases (prior to Java 3), it was often necessary, but JVMs have gotten much faster since then.
* Disadvantages: native methods are not safe, less portable, harder to debug, may leak memory.

## Item 67: Optimize judiciously

> Premature optimization is the root of all evil.  
> We follow two rules in the matter of optimization:  
>Rule 1. Don’t do it.  
>Rule 2 (for experts only). Don’t do it yet—that is, not until you have a perfectly clear and unoptimized solution.

* Strive to write good programs rather than fast ones.
* Strive to avoid design decisions that limit performance.
* It is a very bad idea to warp an API to achieve good performance.

## Item 68: Adhere to generally accepted naming conventions

* Use common sense.

## Item 69: Use exceptions only for exceptional conditions

* Don't use it for control flows.
* A well-designed API must not force its clients to use exceptions for ordinary control flow.

## Item 70: Use checked exceptions for recoverable conditions and runtime exceptions for programming errors

* Throw checked exceptions for recoverable conditions and unchecked exceptions for programming errors.

## Item 71: Avoid unnecessary use of checked exceptions

* If callers won’t be able to recover from failures, throw unchecked exceptions. If recovery may be possible and you want to force callers to handle exceptional conditions, first consider returning an optional. Only if this would provide insufficient information in the case of failure should you throw a checked exception.

## Item 72: Favor the use of standard exceptions

* such as IllegalArgumentException, IllegalStateException, NullPointerException.

## Item 73: Throw exceptions appropriate to the abstraction

* If it isn’t feasible to prevent or to handle exceptions from lower layers, use exception translation, unless the lower-level method happens to guarantee that all of its exceptions are appropriate to the higher level. Chaining provides the best of both worlds: it allows you to throw an appropriate higher-level exception, while capturing the underlying cause for failure analysis.

## Item 74: Document all exceptions thrown by each method

* document every exception that can be thrown by each method that you write. Use `throws` clause and `@throws` tag.
