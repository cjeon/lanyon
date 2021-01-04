---
layout: post
title: Effective Java 3/E summary chanpter 2 (Shorter version)
---

# Chanpter 2 : Methods Common to All Objects

## Item 10

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

## equals
- Should it be implemented?
- Is it an inherited class?
- Implement hashCode

### implementation method
The equals method implements an equivalence relation (Reflexive, Symmetric, Transitive, Consistent), null check and Liskov subsitution principle

- Determine whether you are yourself with `==`
- Check type with `instanceOf`
- Type casting
- Check the 'Core' field
     - in the order of the probability of being different and the fastest comparison

## hashCode
- If `equals` is `true`, `hashCode` is always `true`. If `equals` is `false`, `hashCode` is not always `false`
- Generate hash code with fields of `equals`.
- Don't publish rules for generating hash code.

## toString
- Ideally, it should be a string that perfectly describes the object itself.
- Return all key information the object has.

## Cloneable
- Don't implement `Cloneable`. Instead, implement a copy factory, a copy constructor.
### Copy constructor
```java
public Yum(Yum yum) { ... };
```
### Copy factory
```java
public static Yum newInstance(Yum yum) { ... };
```

## Comparable
- Like `equals`, Reflexive, Symmetric and Transitive must be met.
     - An inherited object cannot implement a perfect `compareTo`.
- Sorted collections use `compareTo()` for equality comparison.
- Don't use relational operators (<, >), use static compare methods or comparators.