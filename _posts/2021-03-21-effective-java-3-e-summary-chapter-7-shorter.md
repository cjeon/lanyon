---
layout: post
title: Effective Java 3/E summary chanpter 7 (Shorter version)
---

# Chanpter 7 : Method

You can find the longer version of this summary [here]({% post_url 2021-02-22-effective-java-3-e-summary-item-46-to-55 %}).

## Parameters
- Consider protective copied instance to prevent an attack
- Validation early + Documentation
    - Null check
    - Range check
    - Type check
- Minimize parameters
    - Highly orthogonal
    - Use static member class
    - Use static member class + Builder pattern
- `Interface` is better than `Class`
- `Enum` is better than `boolean`
- Avoid overloading when same size of paramters
- When using `varargs`, define required params separately
```java
    static int min(int firstArg, int... remainingArgs) { ... }
```

## Return
- Do not return `null`
- Return `Collections.empty*()` replacing `null`
- Return `Optional<T>` when
    - avoiding return `null`
    - clients need to deal with return value specially