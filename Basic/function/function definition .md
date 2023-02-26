# Function declaration and definition
## Example 

Ex1:

    function main()
    {
    
    }

Ex2:

    function func1(v1,v2,v3)
    {
    
    }
    
## Valid function declaration
Same as an identifier.
A function is consist of an identifier, () and {}

## Syntax 
I will use lex to represent the syntax

    {underscore} := _
    {digit} := [0-9]
    {alphaletter} := [a-z]|[A-Z]
    {validletter} := {digit}|{letter}|{underscore}
    {identifier} :=  {alphaletter}({validletter}*)
    {whitespace} := ' '// Just a whitespace
    {comma}  := , // Just a signle comma
    {leftCurly} := '{'
    {rightCurly} := '}'
    {leftParen} := '('
    {rightParen} := ')'
    {funcName} := {identifier}
    {parameter} := {identifier}
    {function} := function({whitespace}*){funcName}{leftParen}{parameter}({parameter}{comma})*){rightParen}({whitespace}*){leftCurly}({whitespace}*){rightCurly}
    
  
