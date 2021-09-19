# Computer Science for JavaScript: Regex Tutorial

Developers write code, but they also *write about code*. 

Writing about code can be a canvas to share one's experiences or a method to help others... but, above all else, it can be a platform to reinforce the learned knowledge of the topic that is being written about.

In this tutorial, we will be looking at **regular expressions**. 

---

## Summary

Simply put, a **regular expression**, **regex** for short, is a sequence of characters that defines a search pattern. 

When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, to find and replace a character or sequence of characters within a string, or used to validate an input. 

For the purpose of this exercise, we will be analysing a regular expression that verifies that a user input is a valid email address to expand our learning on this topic. 

Each component of this regex has a unique responsibility to make sure that a user enters an email address that begins with an unspecified number of characters preceding the `@` symbol, followed by a domain.

The regex is:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

In regex, **Anchors** are not used to match characters but rather to match a position before, after or between characters. More commonly, they are used to match the *start and end* of a line. 

* A Caret `^` matches the position before the first character in the string. 

* A Dollar `$` matches the position after the last character in the string. 


### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.

**Greedy** and **Lazy** are two concepts commonly referred to in the context of quantifiers for regular expressions and, in essence, change how your search expression operates. 

* **Greedy** means to match the longest possible string. 

* **Lazy** means to match the shortest possible string.

Greedy quantifier | Lazy quantifier | Description
--- | --- | ---
`*` | `*?` | Match zero or more times.
`+` | `+?` | Match one or more times.
`?` | `??` | Match zero or one time.
`{ n }` | `{ n }?` | Match exactly *n* times.
`{ n ,}` | `{ n ,}?` | Match at least *n* times.
`{ n , m }` | `{ n , m }?` | Match from *n* to *m* times.

In this example:

```
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
```

We used the greedy quantifier, `+`, to denoate that there is one or more sequences to be matched. 

Furthermore, we used the `{ 2 , 6 }` quantifier to specify that the input should be between the range of a minimum 2 and a maximum of 6 characters. 

### Grouping Constructs & Bracket Expressions

*Grouping constructs* map out the subexpressions of a regular expression and allow programmers to capture the substrings of an input string. 

*Bracket Expressions* indicated a character class or range of characters that we want to match. 

For example, in:

```
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
```

There are three subexpressions being captured and/or grouped using parentheses `( )` with the bracket expressions being represented using `[ ]`. 

* 1. `([a-z0-9_\.-]+)`, must match one or more lowercase letters between a-z, numbers between 0 - 9, underscores, periods, and hyphens. This expression is then followed by the `@`sign. 

* 2. `([\da-z\.-]+)` then, the domain name, must match be matched which can use one or more digits, letters between a-z, periods and hyphens. This expression is then followed by a period `\.`. 

* 3. `([a-z\.]{2,6})`, the last group matches the top level domain, and is looking for any group of letters or dots that are between 2 - 6 characters. 

This expression can be used to match many commonly used emails such as; 

`john.smith@email.com`

### Character Classes

A *character class* allows programmers to match any symbol from a predefined character set. In our example; 

```
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
```

Specifically, in the second grouping, `\d`, is used to delinate a match for any digit character (0 - 9). 

There are other character classes; however, they are not touched on in this example. You can find further examples here...

```
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Character_Classes
```

### The OR Operator

The OR Operator, is delineated using a `|` acts by matching the expression before or after the `|`, *this* | (OR) *that*.

This operator was not used in this regex example. 

### Flags

Flags, in **regex**, are tokens used to modigy the expression's searching behaviour. These are optional and were not included in this regex example. 

There are six of them in JavaScript, which, can be found in greater depth here:

```
https://javascript.info/regexp-introduction
```

### Character Escapes

**Character Escapes** prevent a character from being interpreted as a literal character. 

In our example;

```
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
```

To find a regular dot, e.g. .com, we prepend it with a backslash `\.`. This can be seen between the second and third groupings. 

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
