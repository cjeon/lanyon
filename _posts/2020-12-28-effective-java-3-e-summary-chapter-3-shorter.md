---
layout: post
title: Effective Java 3/E summary chanpter 3 (Shorter version)
---

# Chanpter 3 : Class and Interface

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

### Classs
- Set access restrictions to a minimum. (private > package-private > protected > public)
- Allow only immutable `public` fields.
- Declare a immutable `public` array like this:
```java
private static final Thing[] PRIVATE_VALUES = {...};
public static final List<Thing> VALUES = Collections.unmodifiableList(Arrays.asList(PRIVATE_VALUES));
```
```java
private static final Thing[] PRIVATE_VALUES = {...};
public static final Thing[] values() {
     return PRIVATE_VALUES.clone();
}
```

     