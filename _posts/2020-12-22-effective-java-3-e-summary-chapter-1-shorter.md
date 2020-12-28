---
layout: post
title: Effective Java 3/E summary chanpter 1 (Shorter version)
---

# Chanpter 1 : Creating and Destroying Objects

## Item 1~5

You can find the longer version of this summary [here]({% post_url 2020-12-22-effective-java-3-e-summary-item-1-to-5-longer %}).

### Object creation patterns

- Default constructor
- Static factory method pattern
- Telescoping constructor pattern
- Java Beans pattern
- Builder pattern

### Things to consider before object creation

- Will it be used as a singleton?
- Is it a utility class?
- Is it a class that implements an interface?
- Will it allow inheritance?
- How many parameters are required?

## Item 6~9

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

### Efficient object management
- Reuse immutable objects
- Always minimize the scope
- Watch out for memory leaks in the following situations
     - Class that directly manages memory
     - Use of cache (considering WeakHashMap)
     - Listener, Callback
- Don't use object destructor `finalizer`, `cleaner`
     - As an alternative, use `AutoCloseable` + `try-with-resources` syntax