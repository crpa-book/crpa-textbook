# Chapter 2: Scanning

## What's Scanning?

*Woah, it's getting hot! So much information is filling up my head!* Don't panic, it's just a long journey, but we will take it step by step. Let's start with our first step in building our compiler, which is scanning. But first, let's see source code from our human perspective. Take a line from our previous example:

```basic
num number_variable = 15
```

Knowing from Appendix A1, this line declares a variable called `number_variable` of type `num` and initializes it with the value 15. That's called the semantic of that statement, which refers to the meaning and interpretation of the code. Let's take a step back. When you first saw the structure of the line, your mind went, "Okay, we start our statement with the keyword `num`, then another word `number_variable` (which is not a keyword), then an equal sign, and a number which is 15." You broke down the code statement into units *(Yes, you thought of that, I hope)*, which you used to build that statement. And since you know the syntax of pBASIC, you know that this is the syntax for declaring a variable, based on the breakdown of the code statement. Such a way of thinking is easier for us as humans, but it's complicated to implement on computers. We call that an abstraction... *What?*

To clarify things, what's a suitable type for dealing with source code? A `string`, right? A string just provides us with the characters of the text string (`n`, `u`, `m`, *`SPACE`*, `n`, `u`, `m`, `b`, `e`, `r`, `_`, ...). They are simple units too, but that representation is too granular. You want to work with more meaningful units as you move into the next phases. So, grouping these characters into bigger units will help us process the source code text. The scanner generates **lexemes** like: [`num`], [`number_variable`], [`=`], [`15`], representing the word units of the statement code.

## Tokens
These lexemes can be assigned with attributes to describe it's meaning or type, combined together, resulting a Token. Consider the following statement in C as example:
```c
a = x + 10;
```
A C tokenizer *(another name for scanners)* would generate tokens: ([`a`], [`identifier`]) ([`=`], [`equal`]) ([`x`], [`identifier`]) ([`10`], [`number`]). A token consists of:
* A lexeme (eg. `10`), a string value of the part of text.
* A type (`number`), the class of which the lexeme belongs to, examples:
    * Keywords: reversed keywords in the language
    * Identifiers: symbols like function names, variable names, class names etc..
    * Literals: 
        * Including different number norations like hexdecimal `0x12` or binary `101010101b` or float `5.89f`.
        * Strings: `"Some string!"`

Other attributes like the position and line of the token is helpful for reporting lexical errors.
Inability to detect a token or violating a **lexical rule** should be reported as an **lexical error** and halting the process of scanning.

> Lexical Errors:
> Todo: Power of Abstraction!

```{note}
The word 'lex' comes from greek word 'λέξις' *(lexis)* meaning 'word'. So slicing the strings into lexemes would mean slicing them into words but a word in programming has different meaning than the intuitive one. The string ``print("I like compilers!")`` when it comes to our lexer, [`I`] [`like`] [`compilers`] are not words or lexemes for sure! but will produces [`print`] [`(`] [`"I like compilers!"`] [`)`] instead, denoting the them as the little pieces that build our language statement. We will deal with many  
```

```{admonition} Definition
**Scanning** *or* **Tokenization** *or* **Lexical Analysis** is the process of breaking down source code and classifying segments of the string into more meaningful tokens from raw string format for processing these tokens for further processing.
```

## Regular Languages and Expressions
We mentioned that the scanner's job is to tokenize the input string and to check whether a lexical word belongs to one of our lexical classes/rules. So we can consider the scanner as a **machine** and the rules are the **grammar** of our language, a theortical machine that deals with our strings as inputs and checks if they are grammarly correct. Let's get with  a bit of computer science wih Automata & Langauges theory! Automata theory is the study of abstract machines and their computational abilities. It analyzes formal languages and classifies them based on the computational models needed to recognize or generate them. It has applications in areas such as compiler design and natural language processing.

### Grammar
A scanner should be able to detect token type (class) from string input, as example: ``_pi = 3.14`` would produce the tokens [`_pi`,`identifier`] [`=`,`equal`] [`3.14`,`number`]. For the first token classified as `identifier`, we can define it's rule as "Sequence of alphabetical letters that can contain underscore". The third and the most interesting token has the type `number` and there's a rule that our hypothetical scanner follows to detect the token from a string. We could say the rule (according to pBASIC **syntax**) that a `number` is "Sequence of digits that optionally contains a dot", so `8502` is a valid number but neither `17.69.3` nor `12.` nor `6..9` are valid numbers. It's verbose to describe our lexical rules in English statements, we need a more concise and more formal way, and here comes **Regular Expressions**.

### Regular Expressions
When it comes to describing regular langauges, regular expressions (Regex for short) is more concise to use. Regex is widely used in text processors for string searching algorithms and to detect and match patterns in sequence of characters (string) and that's what we need for our scanner to check whether the string matches our rules therfore it's lexically correct!  
Regular Expressions are algebric notation that has it's own formal rules to describe the our patterns. 
We will see that regular expressions are easy to type, and they tend to use relatively short descriptions for common languages that we want to represent. Of course, even a relatively small and precise specification for a language can be hard to come up with (or to understand). But at least with a regular expression, it is usually quick and easy to type once you have it.

## Practical: Writing the scanner
### Numbers
### Keywords
### Identifiers
