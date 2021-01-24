---
layout: post
title: Effective Java 3/E summary chanpter 3 (Shorter version)
---

# Chanpter 3 : Class and Interface

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

## Class principles
Minimize the possibility of change (if there is no obvious reason, follow the rules below)
- Do not provide methods to change the state of an object (`Setter`)
- Non-extensible `final` class
- All fields `private final`
- Perform defensive copying in `constructor`, `accessor`, and `readObject` methods

## Class design pattern
1. Does this class need inheritance?
- NO,
just implement the class by following the rules above.

- Yes,
Favor composition over inheritance. Follow the steps below.

### Steps to create an inheritable class
1. Build a skeleton through the interface.
2. Create a delivery class. (Wrapper class)

> __Note__ : Doesn't need to implement wrapper class in Kotlin. Kotlin provides `delegate` keyword. 

```java
public class ForwardingSet<E> implements Set<E> { 
    private final Set<E> s; 

    public Forwarding(Set<E> s) { this.s = s; }

    public void clear() { s.clear(); } 
    public boolean contains(Object o) { return s.contains(o); } 
    public boolean isEmpty() { return s.isEmpty(); }
    public int size() { return s.size(); } 
    public Iterator<E> iterator() { return s.iterator(); } 
    public boolean add(E e) { return s.add(e); } 
    public boolean remove(Object o) { return s.remove(o); }
    public boolean containsAll(Collection<?> c) { return s.containsAll(c); } 
    public boolean addAll(Collection<? extends E> c) { return s.addAll(c); } 
    public boolean removeAll(Collection<?> c) { return s.removeAll(c); } 
    public boolean retainAll(Collection<?> c) { return s.retainsAll(c); } 
    public Object[] toArray() { return s.toArray(); } 
    public <T> T[] toArray(T[] a) { return s.toArray(a); } 
    @Override public boolean equals(Object o) { return s.equals(o); } 
    @Override public int hashCode() { return s.hashCode(); } 
    @Override public String toString() { return s.toString(); } 
}
```
3. Define only the required methods by inheriting the delivery class.

```java
public class InstrumentedSet<E> extends ForwardingSet<E> { 
    private int addCount = 0; 

    public InstrumentedSet(Set<E> s) { super(s); } 
    
    @Override public boolean add(E e) { 
        addCount++; 
        return super.add(e); 
    } 
    @Override public boolean addAll(Collection<? extends E> c) { 
        addCount += c.size(); 
        return super.addAll(c); 
    } 
    public int getAddCount() { return addCount; } 
}
```

### Reasons for prohibiting inheritance
- Broken encapsulation (parent affects children)
- Multiple inheritance not possible
- `Equals` cannot be implemented

### Interface
- The purpose of the `interface` is to tell the client what the instance can do.
- `Interface` is difficult to modify, so design creating a new interface.
- Use default methods when creating a new interface. (Java 8 or higher)

### Use of class
- Tagged classes are used in hierarchical structure by using `abstract class`.
- Implement as `static` as possible by preventing member classes from referencing outer classes.
- Limit source files to a single top-level class!