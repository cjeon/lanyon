---
layout: post
title: Effective Java 3/E summary chanpter 10 (Shorter version)
---

# Chanpter 10 : Concurrency

You can find the longer version of this summary [here]({% post_url 2021-02-22-effective-java-3-e-summary-item-46-to-55 %}).

## Concurrency satisfaction
- Exclusive execution: `synchronized` keyword
- Communication between threads: `volatile` field, both read and write sychronization

## Synchronization failure
- Unresponsive, safety failure
    - Avoid calling alien methods
    - Minimize the synchronization area

## Executor rather than thread, use task, use concurrency utility
- Normally use `newCachedThreadPool`
- Use `newFixedThreadPool` on heavy servers
- If you want full control, use `ThreadPoolExecutor` class directly
- `ConcurrentHashMap`, `BlockingQueue`, `CountDownLatch`, `Semaphore`, `Phaser`

## Documentation
- Immutable: No need to sync (`@Immutable`)
- Unconditional thread safety: No need to sync (`@ThreadSafe`)
- Conditional thread safety: synchronization for some methods (`@ThreadSafe`)
- Not thread safe: should be wrapped with an external synchronization mechanism (`@NotThreadSafe`)

## Caution
- Avoid using lazy initialization (`synchroized`, `volatile`)
- Avoid priority for `Thread` (using `Thread.yield`)