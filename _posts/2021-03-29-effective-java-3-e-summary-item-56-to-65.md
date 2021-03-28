---
layout: post
title: Effective Java 3/E summary item 56 to 65 (Longer version)
---

## Item 56: Write doc comments for all exposed API elements

* The conventions are described in the How to Write Doc Comments web page [Javadoc-guide].
* To document your API properly, you must precede every exported class, interface, constructor, method, and field declaration with a doc comment.
* Say what the method does rather than how it does its job.
* To avoid confusion, no two members or constructors in a class or interface should have the same summary description.
* Whether or not a class or static method is thread-safe, you should document its thread-safety

## Item 57: Minimize the scope of local variables

* The most powerful technique for minimizing the scope of a local variable is to declare it where it is first used.
* Nearly every local variable declaration should contain an initializer. If you don’t yet have enough information to initialize a variable sensibly, you should postpone the declaration until you do.
* The for loop, in both its traditional and for-each forms, allows you to declare loop variables, limiting their scope to the exact region where they’re needed. Therefore, prefer for loops to while loops, assuming the contents of the loop variable aren’t needed after the loop terminates.
* keep methods small and focused.

## Item 58: Prefer for-each loops to traditional for loops

* Traditional `for-loop` has some clutter when iterating over colletion or array. `For-each` loop does not have them.

## Item 59: Know and use the libraries

* By using a standard library, you take advantage of the knowledge of the experts who wrote it and the experience of those who used it before you.
* every programmer should be familiar with the basics of java.lang, java.util, and java.io, and their subpackages.

## Item 60: Avoid float and double if exact answers are required

* The float and double types are particularly ill-suited for monetary calculations because it is impossible to represent 0.1 (or any other negative power of ten) as a float or double exactly.
* The right way is to use BigDecimal, int, or long for monetary calculations.

## Item 61: Prefer primitive types to boxed primitives

* There are three major differences between primitives and boxed primitives. First, primitives have only their values, whereas boxed primitives have **identities** distinct from their values. In other words, two boxed primitive instances can have the same value and different identities. Second, primitive types have only fully functional values, whereas each boxed primitive type has one nonfunctional value, which is null, in addition to all the functional values of the corresponding primitive type. Last, primitives are more time- and space-efficient than boxed primitives. All three of these differences can get you into real trouble if you aren’t careful.

## Item 62: Avoid strings where other types are more appropriate

* Strings are designed to represent text, and they do a fine job of it.
* Strings are poor substitutes for other value types.

## Item 63: Beware the performance of string concatenation

* Using the string concatenation operator repeatedly to concatenate n strings requires time quadratic in n.
* To achieve acceptable performance, use a StringBuilder

## Item 64: Refer to objects by their interfaces

* If you get into the habit of using interfaces as types, your program will be much more flexible.

