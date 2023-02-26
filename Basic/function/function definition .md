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
    {funcName} := {identifier}
    {parameter} := {identifier}
    {function} := function({whitespace}*){funcName}({parameter}({parameter}{comma})*)({whitespace}*){leftCurly}({whitespace}*){rightCurly}
    
  
