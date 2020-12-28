---
layout: post
title: Effective Java 3/E summary chanpter 2 (Shorter version)
---

# Chanpter 2 : Methods Common to All Objects


## Item 10

You can find the longer version of this summary [here]({% post_url 2020-12-28-effective-java-3-e-summary-item-6-to-10 %}).

### equals
#### Considerations when implementing
- Should it be implemented?
- Is it an inherited class?
- Implement hashCode

#### implementation method
The equals method implements an equivalence relation (Reflexive, Symmetric, Transitive, Consistent), null check and Liskov subsitution principle

- Determine whether you are yourself with `==`
- Check type with `instanceOf`
- Type casting
- Check the 'Core' field
     - in the order of the probability of being different and the fastest comparison