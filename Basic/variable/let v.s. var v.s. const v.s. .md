# Let v.s. var v.s. const v.s.
## const
const stands for the word "constant".

### Limitation
1) The variable declared by the keyword const must also be defined. That is, you have to assigment value while you declare the variable.
2) It is NOT allowed to change the value after the declaration. That is, the object itself can NOT be reassigned.

## Example 
These examples will either generate compiler error or runtime error.

Ex1:

      function()
      {
        const x = 3;
        x = 5; // compiler error!!! The value of variable defined by keyword const can NOT changed after declaration. 
      }
      
Ex2:

      function()
      {
        const x; // compiler error!!! The value of variable defined by keyword must be also assigned.
      }
      
## let
### Limitation
1) It is NOT allowed to declare the variable again after the declaration. That is, the object itself can NOT be redeclared.

## Example 
These examples will either generate compiler error or runtime error.

Ex1:

      function()
      {
        let x = 3;
        let x = 5; // compiler error!!! The value of variable declared by keyword let can NOT be redeclared. 
      }

These examples are allowed.

Ex1:

      function()
      {
        let x= 3 ;
        x = 5;
      }

Ex2:

      function()
      {
        let x;
         x = 5;
      }
      
## var
### Limitation
Nothing
### Feature
It can impose potential problems if you don't care about variables declared with keyword var.

1) Variables declared with the var keyword can NOT have block scope.

That is, variables declared inside a { } block can be accessed from outside the block.

## Example 
These examples are allowed.

Ex1:

     var x = 10;
    // Here x is 10

    {
    var x = 2;
    // Here x is 2
    }

    // Here x is 2
 
 ## Summary
 Can NOT be redeclared:
 
 let, const
 
 Must be assigned immediately:
 
 const
 
 var is convenient for me, but it imposes potential problems.
 
 ## Ref
 
 https://www.w3schools.com/js/js_let.asp
 
 https://www.w3schools.com/js/js_const.asp
 
 https://www.w3schools.com/js/js_variables.asp
