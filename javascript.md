JavaScript - is an object-oriented programming language.
Data Types of JS
- Premitive - Primitive data types can store only a single value.
    - String, number, Boolean ,undefined ,Symbol(introduce in ES6),bigInt etc
- Non-premitive -  To store multiple and complex values, non-primitive data types are used.
    - Object ,Array
 
Hoisting 
- variable and function declarations are moved on top.it can be in local and globle scope.
Eg. // only variable declarations are hoisted
hoistedVariable = 3;
console.log(hoistedVariable); // outputs 3 even when the variable is declared after it is initialized	
var hoistedVariable;

var x; // Variable initializations are not hoisted
console.log(x); // Outputs "undefined" since the initialization of "x" is not hoisted
x = 23;
Note - Variable initializations are not hoisted, only variable declarations are hoisted:
Note - To avoid hoisting, you can run javascript in strict mode by using “use strict” on top of the code:
let and const are hoisted but not initialized. - Referencing the variable in the block before the variable declaration results in a ReferenceError because the variable is in a "temporal dead zone" from the start of the block until the declaration is processed.

Difference between “ == “ and “ === “ operators
- “==” is used to compare values whereas, “ === “ is used to compare both values and types.

Difference between var and let keyword
var - it's functional scope we can access any where in function.
let - it's limited to the block in which it is declared
