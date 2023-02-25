# Global v.s. Local
## Intro
The concept is very simple as the words describe.

A local variable has lifecycle only in the block.

A global variable has lifecycle in anywhere of the file.

## Declare a local variable.
To declare a local variable, just simply declare it inside the block.

## Declare a global variable.
To declare a global variable, just simply declare it outside of block.

## Scope

At runtime, the order to search for identifier are from inner block to outer block respectively.

More details on the following examples.

## Examples

Ex1:

    function main()
    {
        var x = 3; // here the lifecycle of z is inside the main.
        var y = 4; // here the lifecycle of z is inside the main.
        function func1()
        {
          var z=5;  // here the lifecycle of z is inside the func1.
        } // end of lifecycle of z.
    } // end of lifecycle of x and y.
    
Ex2:
  
    function main()
    {
        var x = 3 ; // here the lifecycle of z is inside the main.
        function func1(v1,v2) // here the lifecycle of v1 and v2 is inside the func1.
        {
            var z = 5 ; // here the lifecycle of z is inside the func1.
        } // end of lifecycle of z , v1 , v2.
    } // end of lifecycle of x.
