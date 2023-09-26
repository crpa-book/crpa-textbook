# Compilers-Runthrough
Text and materials of "Compilers Runthrough: A Practical Approach" book

# Building the book
1- Install Jupyter Book via pip
```
pip install -U jupyter-book
```
2- Generate the book
```
jupyter-book build --all craa-book
```
# Chapters Outlines

## Part 1: Compiler Frontend
* Introduction
    * About Authors
    * Preface
    * Why do we learn compilers?
    * What are compilers?
    * Compilers vs Interpreters
    * Compiler phases
    * Language Paradigms and Terminology
    * petiteBASIC
* Scanning 
    * What’s scanning/lexing?
    * Tokens
    * Regular Languages and Expressions
    * Writing The Scanner
* Parsing
    * What’s parsing
    * Context-free grammars
    * BNF
    * Recursive Decent
    * Writing The Parser
* Intermediate Representations
    * Traversing trees
    * Adding Semantics
    * Interpreting
## Part 2: Compiler Backend
* Virtual Machine
    * Abstractions and Constraints
    * pVM Architecture
    * Intermediate Representations
    * Code Generation I
* Code Generations II:
    * Strings, basic Input Output
    * Variables
    * Branching and Loops
    * Functions
## Appendix
* pBASIC Language Specification
* pBASIC Language Grammar
* pVM Instruction Set
