# variable declaration
## Objectives
Why do we need to declare a variable in html?

In some programming language, you must declare variables before using them (here using refers assigning and accessing them).

## Intro
Html are often be used with js (javascript), php , jquery, node. 

In most cases, syntax of html follows the js.

This is the reason why to declare (then definition) variable are same in js.

## Syntax
In js, to declare a variable, just simply type one of these 

    var
   
    ,let
    
Here, we don't talk about some details. Including 
    
     1) The valid identifier.
        
     2) The difference of var and let.
     
     3) Global declaration v.s. local declaration.
  
     
I will talk these topics in other articles.

## Examples

Here are examples of statements to declare variables without compiler error or runtime error.

1)
  
           var x; // declaration NOT definition.

2)
      
          let x; // declaration NOT definition.
         
# assignment
## Intro
Assignment can pass the rvalue (right-side value) into lvalue (left-side value).

The value of left side identifier will be overrided.

An equal symbol refers an assigment.

## Examples

1) To assign 2 to x.

       x = 2; // assignment

2) To assign x + 3 to x.
    
        x = x + 3; // assignment
        
## NOTE
NOTE that don't think it as an mathematical equation.
 
In mathematical equation,

    x = x + 3 
    => x - x = x + 3 - x
    => 0 = 3 
    => Impossible fact in math.
    
 But in programming language, it is wrong to say that it is impossible that
 
        x = x + 3
        
 Why?
 
 As I mentioned before, the statement
 
    x = x + 3
    
will access the value of x then plus 3 

, finnally put the result into x.

Thus,

    x = 4;
    x = x + 3;
    document.write(x);
    
will output 7.
    
# variable definition        
 
The definition refers declaration and initialization in one statement.

## Examples

They have same effect.

    var x = 7; // declaration and definition.
    
and
    
    var x; // declaration.
    x=7;   // assignment.
    

