# Appendix I: petiteBASIC Grammar

```vb
' this is a comment

' Input/Output
print("Hello, World!") ' How could we even forget it!
num age = read()   'pBASIC is weak typed so str can be converted to num

' variable declaration
num number_variable = 15 
str myName =  "john"


' Branching
if age > 18 then
    print("You are old enough")
else
    print("You need to wait " + (18 - age) + " years")
end if

' Loops
num n = 10
while n != 0 do
    print(n)
    n--
end while
```

```bnf
// A program unit
program = stmt+;

// Statements
stmt = decl_stmt
     | assign_stmt
     | if_stmt
     | while_stmt;
     | func_call;

// Declaration Statement
decl_stmt = ID ID ("=" expr)?;

// Assignment Statement
assign_smt = ID "=" expr;

// If Statement
if_stmt = "if" expr "then" stmt+ "else" stmt+ "end" "if"?

// While Statement
while_stmt = "while" expr "do" stmt+ "end" "while"?

// Expressions
expr = 

func_call = ID "(" arg_list? ")";
arg_list = expr ("," expr)*;

// Lexical Tokens
NUMBER = [0-9]+
ID = [_a-zA-Z]+
```