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

Implicit Type Coercion - conversion of value from one data type to another.

javascript a statically typed or a dynamically typed language
- JavaScript is a dynamically typed language. In a dynamically typed language, the type of a variable is checked during run-time in contrast to a statically typed language, where the type of a variable is checked during compile-time(eg. typescript).
- loosely(dynamically) typed language - A variable can hold the value of any data type.

Passed by value and passed by reference.
Passed by value - primitive data types when passed to another variable, are passed by value. Instead of just assigning the same address to another variable, the value is passed and new space of memory is created.

var y = #8454; // y pointing to address of the value 234
var z = y; 
var z = #5411; // z pointing to a completely new address of the value 234
// Changing the value of y
y = 23;
console.log(z);  // Returns 234, since z points to a new address in the memory so changes in y will not effect z.

Passs by Refrence - while passing non-primitive data types, the assigned operator directly passes the address (reference) of the variable.
var obj = #8711;  // obj pointing to address of { name: "Vivek", surname: "Bisht" }
var obj2 = obj;
var obj2 = #8711; // obj2 pointing to the same address 
// changing the value of obj1
obj.name = "Akki";
console.log(obj2);
