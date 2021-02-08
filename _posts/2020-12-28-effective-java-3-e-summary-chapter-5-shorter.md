---
layout: post
title: Effective Java 3/E summary chanpter 3 (Shorter version)
---

# Chanpter 5 : Enum and Annotation

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

## Enum
- Enum : instance control (declared as `public static final`), singleton, type stability
- Method and field can be added to enum type. -> Receives data from the constructor and stores it in the instance (adds a value when creating each enum field)

```java
public enum Operation {
    PLUS("+") {
        double apply(double x, double y) {
            return x + y;
        }
    },
    MINUS("-") {
        double apply(double x, double y) {
            return x - y;
        }
    },
    TIMES("*") {
        double apply(double x, double y) {
            return x * y;
        }
    },
    DIVIDE("/") {
        double apply(double x, double y) {
            return x / y;
        }
    };
    private final String symbol;

    Operation(String symbol) {
        this.symbol = symbol;
    }

    @Override
    public String toString() {
        return symbol;
    }
    public abstract double apply(double x, double y);
}
```

## Precautions for Enum
- Prohibit use of `ordinal()`. Instead, it is marked as an instance field