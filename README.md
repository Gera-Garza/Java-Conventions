
# Java Conventions

Revision History

| Revision | Date    | Author | Description | 
| ------------- | ------- | ---- | ------ | 
| v1.0 | 03-29-2022 | Gerardo Garza| Guide to understand the basic Guidelines in Java draft version |

## Table of contents
 * [Why conventions](#why-have-code-conventions)
 * [Name Conventions](#name-convention)
 > * [Packages](#packages)
 > * [Classes and Interfaces](#classes-and-interfaces)
 > * [Methods and Variables](#methods-and-variables) 
 > * [Constants](#constants)
 * [Error Handling](#error-handling)
 * [JavaDocs](#javadocs)
 > * [Javadoc Format](#javadoc-format)
 > * [Javadoc at Class Level](#javadoc-at-class-level)
 > * [Javadoc at Field Level](#javadoc-at-field-level)
 > * [Javadoc at Method Level](#javadoc-at-method-level)
 
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
![image name table](https://user-images.githubusercontent.com/43157958/161159253-dc7f3bf4-bacd-4eb8-bf2f-ffd015c18bf3.png)


### Packages

For packages names should be in lowercase. With small projects that only have a few packages it's okay to just give them simple (but meaningful!) names:

```java
package pokeranalyzer package mycalculator
```

### Classes and Interfaces

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
## Java Docs
Javadoc comments structure look very similar to a regular multi-line comment, but the key difference is the extra asterisk at the beginning
```java
// This is a single line comment

/*
 * This is a regular multi-line comment
 */

/**
 * This is a Javadoc
 */
```
### Javadoc Format
Javadoc comments may be placed above any class, method, or field which we want to document.

These comments are commonly made up of two sections:

The description of what we're commenting on
The standalone block tags (marked with the “@” symbol) which describe specific meta-data

### Javadoc at Class Level
Let's take a look at what a class-level Javadoc comment would look like
```java
/**
* Hero is the main entity we'll be using to . . .
* 
* Please see the {@link com.baeldung.javadoc.Person} class for true identity
* @author Captain America
* 
*/
public class SuperHero extends Person {
    // fields and methods
}
```
### Javadoc at Field Level
We can also use a description without any block tags like this inside our SuperHero class
```java
/**
 * The public name of a hero that is common knowledge
 */
private String heroName;
```
Private fields won't have Javadoc generated for them unless we explicitly pass the -private option to the Javadoc command.
### Javadoc at Method Level
Methods can contain a variety of Javadoc block tags.
Let's take a look at a method we're using:
```java
/**
 * <p>This is a simple description of the method. . .
 * <a href="http://www.supermanisthegreatest.com">Superman!</a>
 * </p>
 * @param incomingDamage the amount of incoming damage
 * @return the amount of health hero has after attack
 * @see <a href="http://www.link_to_jira/HERO-402">HERO-402</a>
 * @since 1.0
 */
public int successfullyAttacked(int incomingDamage) {
    // do things
    return 0;
}
```
Let's go over the tags we encounter in the example above:

* @param provides any useful description about a method's parameter or input it should expect
* @return provides a description of what a method will or can return
* @see will generate a link similar to the {@link} tag, but more in the context of a reference and not inline
* @since specifies which version the class, field, or method was added to the project
* @version specifies the version of the software, commonly used with %I% and %G% macros
* @throws is used to further explain the cases the software would expect an exception
* @deprecated gives an explanation of why code was deprecated, when it may have been deprecated, and what the alternatives are
