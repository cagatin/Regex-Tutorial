# Regex Tuorial
## Introduction
Hello, and welcome to my **Regular Expressions** tutorial! In this tutorial, we will be going over what a **regex** is, along with how to use it in our **Javascript** code! Now, get comfortable, and let us learn together!

## Table of Contents
- [Regex Tuorial](#regex-tuorial)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Summary](#summary)
    - [What is a Regex?](#what-is-a-regex)
    - [Example: Email Validation](#example-email-validation)
  - [Anchors](#anchors)
    - [What is an Anchor?](#what-is-an-anchor)
    - [The Caret Anchor](#the-caret-anchor)
    - [The Dollar Sign Anchor](#the-dollar-sign-anchor)
    - [Example: Email Validation - Anchors](#example-email-validation---anchors)
  - [Quantifiers](#quantifiers)
  - [Grouping Constructs](#grouping-constructs)
  - [Bracket Expressions](#bracket-expressions)
  - [Character Classes](#character-classes)
  - [The OR Operator](#the-or-operator)
  - [Flags](#flags)
  - [Character Escapes](#character-escapes)
  - [Author](#author)

## Summary
### What is a Regex?
A **Regex**, or **Regular Expression**, is a search pattern primarily used to match a series of character combinations found within a string. When included in code, a **Regex** could be particularly helpful in finding certain characters, sequences of characters, or input string validation. 

### Example: Email Validation
To illustrate what a Regex is, let us look at one of the most commonly used regex patterns - email validation!
```
const emailRegex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/;
```
What this means exactly is not important for now (We will understand this regex more as we progress through this tutorial). What is important understand, however, is that a regex is enclosed within two forward slashes ```//```. 
<br>
<br>
The general syntax to denote the start and end of a regex is as follows: <br>
```
const myRegex = /<regex expression goes here>/;
```
Now that we have an understanding of what a Regex is and how to declare them, let us learn how to create much more complex regex patterns!

## Anchors
### What is an Anchor?
**Anchors** in a Regular Expression enable us to match a character's **position** within a string. Specifically, the anchor characters are:
```
^ - Matches the BEGINNING of the input.
$ - Matches the END of the input.
```

### The Caret Anchor
The Caret anchor (```^```) signifies that the string begins with a specific character. 
<br>
<br>
Say we have the following string:
```
const testStr = "Hello World!";
```
Now, let us use the ```test()``` method of the ```RegExp``` object to execute a search for a match between our regular expressioun and test string.
```
let myRegex = /^H/;

console.log(testStr.test(myRegex));   // returns true! 'Hello, World!' starts w/ H.
```
Let us ust ```test()```, along with the caret anchor to test if our test string ends in an exclamation point.

### The Dollar Sign Anchor
The Dollar Sign anchor (```$```) signifies that the string ends with a specific character. 
<br>
<br>
Here is an example using our test string from above. 
```
const testStr = "Hello World!";

myRegex = /!$/;                     // The character is placed before the $ sign!
console.log(myRegex.test(str));     // returns true!
```
Note: A key difference in syntax between the caret anchor and dollar sign anchor is that the dollar sign anchor is placed ***after*** the character. 

### Example: Email Validation - Anchors
Let us return to our email validation example from above.
```
const emailRegex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/;
```
The following regex section uses the **carat anchor** to denote that the email string begins with a character contained within the **bracket expression** (we will cover this later). In essence, we are stating that the first character ***begins*** with a character a-z, 0-9, an underscore character, dot character, or hyphen character. 
```
Beginning anchor:
/^([a-z0-9_\.-]+) 
```
Now let us take a look at the end character.
```
Ending anchor:
([a-z\.]{2,6})$/
```
Here, we are again utilizing **bracket notation**, as well as a **quantifier**  to specifiy what our string should end with. In essence, we are stating that our string should ***end*** with the specified characters above, and should only contain 2 characters minimum, and 6 characters maximum. 

## Quantifiers

## Grouping Constructs

## Bracket Expressions

## Character Classes

## The OR Operator

## Flags

## Character Escapes


## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
