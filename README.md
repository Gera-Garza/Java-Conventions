
# Java Conventions

Revision History

| Revision    | Date    | Author | Description| 
|------------- | -------||------ | -------- |
| v1.0 | 03-29-2022 | Gerardo Garza| Guide to understand the basic Guidelines in Java draft version


## Why Have Code Conventions

Code conventions are important to programmers for several reasons:

- 80% of the lifetime cost of a piece of software goes to maintenance.
- Hardly any software is maintained for its whole life by the original author.
- Code conventions improve the readability of the software, allowing engineers to understand new code more quickly and thoroughly.
- If you ship your source code as a product, you need to make sure it is as well packaged and clean as any other product you create.

## Name Convention
When naming it is important to keep a mix between upper and lower case but making use of the convention of CamelCase, Lowercase and a mixed case.
It’s important to keep simple and descriptive names, avoid to use full words and acronyms but some are permitted like DAO,URL,DTO etc..
Here is a table with some examples:
![image names table]()

### Packages

For packages names should be in lowercase. With small projects that only have a few packages it's okay to just give them simple (but meaningful!) names:

```java
package pokeranalyzer package mycalculator
```

### Classes & Interfaces 

When you have classes and interfaces names should be in CamelCase. Try to use nouns because a class is normally representing something in the real world:

```java
class Customer class Account
```
> **Note** that some programmers like to distinguish interfaces by beginning the name with an "I":

```java
interface IComparable interface IEnumerable
```

###	Methods and Variables

For methods names should be in mixed case. Use verbs to describe what the method does:
```java
void calculateTax() string getSurname()
```
And for variables names should be in mixed case. The names should represent what the value of the variable represents:
```java
string firstName int orderNumber
```

> additional notes in variables
- Add // comment if meaning of variable isn't completely clear or if has special range, values, etc.
- Don't reuse variable name for more than one purpose. Variables are cheap.
- Local variables (declared in method)
> - Declare at first use is preferred to declaring at front.
> -	Give variable the least required scope (without adding extra blocks).
> -	Declare within for loop header if possible.
> - Don't hesitate to create extra local variable if it improved readability.
- Instance variables (fields)
> -	Declare them private.
- Static (class) variables
> -	Use static final for named constants.

###	Constants
With the constant we use uppercase 
```java
static final int DEFAULT_WIDTH static final int MAX_HEIGHT
```
## Error handling

-	Crash on programming errors is acceptable. Debugging output is useful.
-	Catching exceptions
> -	Don't catch an exception if you can't handle it.
> -	Don't use exceptions to handle normal flow (eg, ArrayIndexOutOfBoundsException).
> -	Don't use exceptions to hide program errors; fix them.
> -	Don't silently ignore exceptions, except in those few cases where you can't do anything anyway.
-	Throwing exceptions
> -	Don't throw Exception - make it more specific.
> -	Put informative message in exception constructor.
> -	If you're supplying a class for someone, throw meaningful exceptions.
When throwing an exception here are samples of good and poorly indented messages
```java
// Avoid (x) - Not easy to read
throw new IllegalStateException("Failed to process request" + request.getId()
    + " for user " + user.getId() + " query: '" + query.getText()
    + "'");

// Prefer (✔️) - Fairly easier to read
throw new IllegalStateException("Failed to process"
    + " request " + request.getId()
    + " for user " + user.getId()
    + " query: '" + query.getText() + "'");
```
