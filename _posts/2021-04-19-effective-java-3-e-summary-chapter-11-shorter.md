---
layout: post
title: Effective Java 3/E summary chanpter 10 (Shorter version)
---

# Chanpter 11 : Serialization

You can find the longer version of this summary [here]({% post_url 2021-02-22-effective-java-3-e-summary-item-46-to-55 %}).

## Serialization
- Use `JSON`, `protocol buffer` instead of Java serialization.
    - `JSON` is human-readable.
    - Because the `protocol buffer` is a binary representation, it is highly efficient.

## Prohibit use of Serializable
- `Serailzable` is vulnerable to security
- Prohibit `Serailzable` in `classes` designed for inheritance and `interfaces`.
- Inner classes should not implement serialization.
- If not for inheritance, use serialization proxy pattern
    - Create nested class
    - Implement Outer class `writeReplace()` + `readObject()`
    - Implement Nested class `readResolve()`

## If you're still going to use Seralizable,
- Judgment of logical and physical differences.
- Logic == physics
    - Just implement `Serailzable`
- Logic != Physics
    - Custom serialization
    - `transient` + `writeObject()` + `readObject()`
    - UID explicitly granted (compatibility)
    - When writing `readObejct()` (like public constructor)
        - Defensive copy
        - Prohibit calling overridable methods
- Instance control class
    - `Enum` type for singleton class
    - If the `enum` type is not available, `readResolve()` + `transient`


