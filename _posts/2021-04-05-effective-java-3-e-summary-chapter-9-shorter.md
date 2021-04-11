---
layout: post
title: Effective Java 3/E summary chanpter 9 (Shorter version)
---

# Chanpter 9 : Exceptions

You can find the longer version of this summary [here]({% post_url 2021-02-22-effective-java-3-e-summary-item-46-to-55 %}).

## When to use?
- Exception situation other than control flow (normal API should not use `Exception`)
- If `Exception` occurs, that is, the client needs to recover, use checked exception.
- Use runtime exceptions for Programming errors.

## Standard exceptions
`IllegalArgumentException` : Argument is invalid
`IllegalStateException` : Object state is inappropriate for method execution
`ConcurrentModificationException` : Single threaded design accessed by multiple threads
`UnsupportedOperationException` : When calling an unavailable method
`NullPointerException` : If null is not allowed, but null is entered
`IndexOutOfBoundsException` : When the index range is exceeded

## Better exception
- If low-level exceptions are widespread, high-level exceptions are used.
- If you want to show low-level exceptions, use exception chaining.
- If it is difficult to provide information due to exception, use logging.
- Documentation.
- Include failure information in detail messages.
- Maintains the state of the object even if an exception occurs.