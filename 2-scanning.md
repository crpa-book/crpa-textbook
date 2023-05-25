# Chapter 2: Scanning

## What's Scanning?
*Woah, It's getting hot! many information is filling up my head!* Don't panic, it's just a long journey but we will take it a step by step. let's start with our first step into building our compiler which is scanning, but first let's see from our human view, how would us see source code. Take a line from our previous example
```basic
num number_variable = 15
```
Knowing from Appendix A1, this line declares a variable called `number_variable` of type `num` and initializes it with value 15 that's called the semantic of that statement which refers to the meaning and interpretation of a code. Get a step back, you first seen the structure of the line your mind was "Okay, we start our statement with the keyword `num` then another word `number_variable` which is not a keyword then an equal sign and a number which is 15" you broke down the code statement into units *(Yes you thought of that, I hope)* which you used to build that statement. And since you know the syntax of pBASIC, you know that is the syntax of declaraing a variable from that break down of the code statement, Such a way of thinking is more easier for us as humans but it's complicated to implement on computers. We call that an abstraction.. *What?* To clear things what's a suitable type for dealing with source code? a `string`, right? A string just provides us the characters of the text string (`n`, `u`, `m`, *`SPACE`*, `n`, `u`, `m`, `b`, `e`, `r`, `_`, ...) it's simple units too but that representation is too granular. You want to work with more meaningful units so you can into the next phases. So grouping these characters into bigger units (We will start calling them tokens) that will help us in processing source code text. The scanner generates tokens (that's why it's called a tokenizer too) like [`num`] [`number_variable`] [`=`] [`15`]. These tokens (called lexemes too) provide a more manageable representation for further processing.
> Todo: Power of Abstraction!

**Scanning** or **Tokenizing** or **Lexical Analysis** is the process of breaking down source code into more meaningful tokens from raw string format.

