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


Higher Order Functions
- Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions.

.this - The “this” keyword refers to the object that the function is a property of.

self-invoking function
A self-invoking function is a nameless (anonymous) function that is invoked immediately after its definition.
(function(){
    console.log("This function is called immediately");
})();

call() - This method invokes a method (function) by specifying the owner object. - sayHello.call(obj);
apply() - call() method takes arguments separately whereas, apply() method takes arguments as an array. - saySomething.apply(person4, ["awesome"]);
bind() - This method returns a new function, where the value of “this” keyword will be bound to the owner object, which is provided as a parameter. - var detailsOfPerson1 = bikeDetails.displayDetails.bind(person1, "TS0122", "Bullet");
Call, apply, and bind are the functions that help you change the context of the this keyword present inside the invoking function.
We saw how each function can be called in different ways – for example, with apply you can execute a function with an array of arguments, and with the call function you can execute the same but the arguments are spread via commas.
These functions are really useful in class-based components of React.


Currying - Currying is an advanced technique to transform a function of arguments n, to n functions of one or fewer arguments.
f we have a function f(a,b), then the function after currying, will be transformed to f(a)(b).

Scope in JS determines the accessibility of variables and functions at various parts of one’s code.
Global Scope - Variables or functions declared in the global namespace have global scope
Local or Function Scope - Any variables or functions declared inside a function have local/function scope
Block Scope - Block scope is related to the variables declared using let and const. Variables declared with var do not have block scope.
Scope Chain - As you can see in the code above, if the javascript engine does not find the variable in local scope, it tries to check for the variable in the outer scope. If the variable does not exist in the outer scope, it tries to find the variable in the global scope.

If the variable is not found in the global space as well, a reference error is thrown.

Closures - Closures are an ability of a function to remember the variables and functions that are declared in its outer scope.


All javascript objects inherit properties from a prototype A prototype is a blueprint of an object. The prototype allows us to use properties and methods on an object even if the properties and methods do not exist on the current object.

callback() - callback is a function that will be executed after another function gets executed.
operationOnSum(3, 3, divideByHalf); 


memoization - Memoization is a form of caching where the return value of a function is cached based on its parameters. If the parameter of that function is not changed, the cached version of the function is returned.
this is where memoization comes in, by using memoization we can store(cache) the computed results based on the parameters. If the same parameter is used again while invoking the function, instead of computing the result, we directly return the stored (cached) value.

Recursion - Recursion is a technique to iterate over an operation by having a function call itself repeatedly until it arrives at a result.

constructor function - If we want to create multiple objects having similar properties and methods, constructor functions are used.


arrow functions - They provide us with a new and shorter syntax for declaring functions.
- The biggest difference between the traditional function expression and the arrow function is the handling of this keyword. By general definition, this keyword always refers to the object that is calling the function. In the arrow functions, there is no binding of this keyword. This keyword inside an arrow function does not refer to the object calling it. It rather inherits its value from the parent scope which is the window object in this case.

Rest parameter & spread parameter
Rest parameter is used to take a variable number of arguments and turns them into an array while the spread operator takes an array or an object and spreads it
Rest parameter is used in function declaration whereas the spread operator is used in function calls.


Promises are used to handle asynchronous operations like server requests, for ease of understanding, we are using an operation to calculate the sum of three elements.
new Promise((resolve,reject)=>{});

generator functions
They can be stopped midway and then continue from where they had stopped.
yield: pauses the generator execution and returns the value of the expression which is being written after the yield keyword.
yield*: it iterates over the operand and returns each value until done is true. it's use for array
function* fun() { 
    yield 10; 
    yield [2,3,5,5; 
    yield 30; 
} 

Temporal Dead Zone 
Temporal Dead Zone is a behaviour that occurs with variables declared using let and const keywords. It is a behaviour where we try to access a variable before it is initialized.

Babel, it converts modern JavaScript syntax into a version that is compatible with all environments.
Prototype Design Pattern - Prototype Pattern creates new objects, but instead of returning uninitialized objects, it returns objects with values copied from a prototype - or sample - object. 
