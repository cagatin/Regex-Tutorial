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
    - [What is a Quantifier?](#what-is-a-quantifier)
    - [Quantifier Characters](#quantifier-characters)
    - [Example: Email Validation - Quantifiers](#example-email-validation---quantifiers)
  - [Grouping Constructs and Subexpressions](#grouping-constructs-and-subexpressions)
    - [What is a Subexpression?](#what-is-a-subexpression)
    - [Capturing Groups have two main effects:](#capturing-groups-have-two-main-effects)
    - [Example: Email Validation - Grouping Contruct](#example-email-validation---grouping-contruct)
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
### What is a Quantifier?
A **Quantifier** is a limit set on a regular expression which specifies the numerical value of characters or expressions to match. **Quantifiers** are inherently **greedy**, and will search the entirety of the section of the string for **ALL** occurances of the specified pattern. 

### Quantifier Characters
A **quantifier** is denoted by specific characters, which specify the numerical limit of matched patterns. 

* ```x*``` - Matches the preceeding pattern ```x``` ***zero or more*** times. 
* ```x+``` - Matches the preceeding pattern ```x``` ***one or more*** times. 
  * equivalent to {1,}
* ```x?``` - Matches the preceeding pattern ```x``` ***zero or one*** times.
  * Can be used immediately *after* any of the quantifiers to make the regex ***lazy*** (i.e. the regex quantifier will now match the pattern the ***minimum*** number of times). 
* ```x{}``` - Creates the following limit matches:
  * ```x{n}``` - Matches the preceeding pattern ```x```  ***exactly*** **n** times.
  * ```x{n,}``` - Matches the preceeding pattern ```x```  ***at least*** **n** times.
  * ```x{n,m}``` - Creates a numerical **range** limit on the number of matches in the preceeding pattern ```x```. 
    * Matches the pattern ***at least*** **n** times, and ***at most*** **m** times. 
* 


### Example: Email Validation - Quantifiers
Let us return to our email validation example from above.
```
const emailRegex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/;
```
Notice the use of the quanitfier towards the tail end of the regular expression:
```
([a-z\.]{2,6})$
```
So, what does this mean? 
The values in the brackets ```{2,6}``` specify a numerical range of patterns to match in the given bracket expression.
<br>
This means that the trail end of the string can contain at minimum two characters specfied within the bracket expression, and at maximum, 6 charaters within it. 
<br>
<br>
## Grouping Constructs and Subexpressions
### What is a Subexpression?
A **subexpression** is a means of grouping a section of a regex via parentheses ```()```. 
When a pattern is enclosed within parenthesis, it is called a **capturing group.**

### Capturing Groups have two main effects:
1. Enables users to retrieve a part of the pattern match as a seperate item in the results array. 
2. Enables users to place a **quantifier** after the parenthesis.
   * causes the quantifier to apply to the entirety of the capture group.  

For example, let us take a look at the following example which utilizes the ```:``` colon grouping construct:
```
(hello)-(world)
```
Here, we create a regex which seeks to match one word, ```(Hello)```, a dash, followed by another word, ```(World)```.
<br>
<br>
Let us again utilize the ```regex.test``` method to display this.
```
let text1 = "Hello-World"
let text2 = "Hello World"

const myRegex = /(Hello)-(World)/;

console.log(myRegex.test(text1));     // returns true
console.log(myRegex.test(text2));     // returns false
```
### Example: Email Validation - Grouping Contruct
Let us return to our email validation example from above.
```
const emailRegex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/;
```
Let us seperate the different groups below:
```
Group 1: ([a-z0-9_\.-]+)
Group 2: @([\da-z\.-]+)
Group 3: \.([a-z\.]{2,6})
```
- The first group uses the bracket expression in order to create a pattern to match the username of the email address.
<br>
- The second group begins with the ```@``` symbol, and is used to group the bracket expression which matches the mail server or domain name of the email. 
<br>
- The third group begins with a period or dot (```.```), and is used to group together the bracket expression to match the domain. This group utilizes a **quantifier** to apply a match limit on the entirety of the capture group. 
## Bracket Expressions

## Character Classes

## The OR Operator

## Flags

## Character Escapes


## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
