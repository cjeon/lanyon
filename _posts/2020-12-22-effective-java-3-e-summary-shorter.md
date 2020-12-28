---
layout: post
title: Effective Java 3/E summary (Shorter version)
---
You can find the longer version of this summary [here]({% post_url 2020-12-22-effective-java-3-e-summary-item-1-to-5-longer %}).

## Item 1~5: Creating and Destroying Objects 1

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

You can find the longer version of this summary [here]({% post_url 2020-12-22-effective-java-3-e-summary-item-1-to-5-longer %}).

## Item 6~9: Object creation and destruction 2

### Efficient object management
- Reuse immutable objects
- Always minimize the scope
- Watch out for memory leaks in the following situations
     - Class that directly manages memory
     - Use of cache (considering WeakHashMap)
     - Listener, Callback
- Don't use object destructor finalizer, cleaner
     - As an alternative, use AutoCloseable + try-with-resources syntax

## Item 10: Common methods of all objects

### equals
#### Considerations when implementing
- Should it be implemented?
- Is it an inherited class?
- Implement hashCode

#### implementation method
- Determine whether you are yourself with ==
- Check type with instanceOf
- Type casting
- Check the 'Core' field
     - in the order of the probability of being different and the fastest comparison