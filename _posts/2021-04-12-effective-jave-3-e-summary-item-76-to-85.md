---
layout: post
title: Effective Java 3/E summary item 76 to 85 (Longer version)
---

## Item 76: Strive for failure atomicity

* Generally speaking, a failed method invocation should leave the object in the state that it was in prior to the invocation.
* Even where failure atomicity is possible, it is not always desirable. For some operations, it would significantly increase the cost or complexity. That said, it is often both free and easy to achieve failure atomicity once you’re aware of the issue.

## Item 77: Don’t ignore exceptions

* If you choose to ignore an exception, the catch block should contain a comment explaining why it is appropriate to do so, and the variable should be named ignored.

## Item 78: Synchronize access to shared mutable data

* Not only does synchronization prevent threads from observing an object in an inconsistent state, but it ensures that each thread entering a synchronized method or block sees the effects of all previous modifications that were guarded by the same lock.
* Synchronization is required for reliable communication between threads as well as for mutual exclusion.
* It is not sufficient to synchronize only the write method! Synchronization is not guaranteed to work unless both read and write operations are synchronized.

## Item 79: Avoid excessive synchronization

* To avoid liveness and safety failures, never cede control to the client within a synchronized method or block.
* As a rule, you should do as little work as possible inside synchronized regions.

## Item 80: Prefer executors, tasks, and streams to threads

* Not only should you refrain from writing your own work queues, but you should generally refrain from working directly with threads. When you work directly with threads, a Thread serves as both a unit of work and the mechanism for executing it. In the executor framework, the unit of work and the execution mechanism are separate.

## Item 81: Prefer concurrency utilities to wait and notify

* There is seldom, if ever, a reason to use wait and notify in new code.

## Item 82: Document thread safety

* Common cases: immutable, unconditionally thread-safe, conditionally thread-safe, not thread-safe, thread-hostile.

## Item 83: Use lazy initialization judiciously

* Under most circumstances, normal initialization is preferable to lazy initialization.

## Item 84: Don’t depend on the thread scheduler

* Any program that relies on the thread scheduler for correctness or performance is likely to be nonportable.
* Thread priorities are among the least portable features of Java.

## Item 85: Prefer alternatives to Java serialization

* There is no reason to use Java serialization in any new system you write.
