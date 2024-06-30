# JavaScript

- JavaScript is a synchronous, single-threaded language.
- The whole JavaScript executes in the "Global Execution Context".

## Execution Context

### Memory Allocation (Environment Variable)
- Executes code line by line and allocates memory for variables and functions.
- Sets the default value as `undefined` for variables and for functions sets the whole function code.

### Code (Thread of Execution)
- Executes code line by line and sets values to variables.
- For functions, it creates a new "execution context" inside the global execution context.
- The new execution context creates 2 parts: memory and code. Once its execution is complete, it finds the return keyword, which means it returns the control of execution to the upper execution context where the function was invoked.

## Call Stack

- Maintains the order of execution of "Execution Context".
- The execution of JavaScript follows the call stack. Every global execution context is put at the bottom of the stack, and once a new execution starts, it is pushed onto the stack. Once execution is complete, it will pop from the stack.
- The call stack is also known as the "Execution Context Stack," "Program Stack," "Control Stack," "Machine Stack," or "Runtime Stack."

## Hoisting

- Hoisting allows access to variables and functions before they are initialized.
- It returns `undefined` for variables and returns the whole function for functions.
- For arrow functions, it works as a variable, so it returns `undefined`.

### Example of Hoisting

```javascript
console.log(myVar); // Output: undefined
console.log(myFunc); // Output: [Function: myFunc]
console.log(myArrowFunc); // Output: undefined

var myVar = 10;

function myFunc() {
    console.log('This is my function.');
}

var myArrowFunc = () => {
    console.log('This is my arrow function.');
};

console.log(myVar); // Output: 10
myFunc(); // Output: This is my function.
myArrowFunc(); // Output: This is my arrow function.
```

In the example above:
- `myVar` is accessed before it is initialized, so it returns `undefined`.
- `myFunc` is accessed before it is defined, so it returns the whole function.
- `myArrowFunc` is accessed before it is initialized, so it returns `undefined`.

## Lexical Environment, Scope, and Scope Chain

### Lexical Environment

- A lexical environment is the environment in which variables and functions are physically written in the source code.
- It consists of the local memory (variable environment) and a reference to the parent lexical environment.

### Scope

- Scope determines the accessibility of variables and functions at various parts of the code.
- There are three types of scope:
  1. **Global Scope**: Variables declared outside any function have a global scope and can be accessed anywhere in the code.
  2. **Function Scope**: Variables declared within a function are only accessible within that function.
  3. **Block Scope**: Variables declared within a block (e.g., inside a loop or conditional statement) are only accessible within that block (introduced with `let` and `const` in ES6).

### Scope Chain

- The scope chain is used to resolve variable access in nested functions.
- It consists of references to its own lexical environment and its parent lexical environments up to the global environment.

### Example of Lexical Environment, Scope, and Scope Chain

```javascript
const globalVar = 'Global';

function outerFunc() {
    const outerVar = 'Outer';

    function innerFunc() {
        const innerVar = 'Inner';
        console.log(globalVar); // Output: Global
        console.log(outerVar);  // Output: Outer
        console.log(innerVar);  // Output: Inner
    }

    innerFunc();
    console.log(globalVar); // Output: Global
    console.log(outerVar);  // Output: Outer
    // console.log(innerVar); // Error: innerVar is not defined
}

outerFunc();
// console.log(outerVar); // Error: outerVar is not defined
// console.log(innerVar); // Error: innerVar is not defined
```
---

# Block and Block Scope in JavaScript

## Block

In JavaScript, a block is a statement enclosed in curly braces `{}`. Blocks are used to group statements together. Common places where blocks are used include control structures like `if`, `for`, `while` loops, and functions.

### Example:
```javascript
{
  // This is a block
  let x = 10;
  console.log(x); // Output: 10
}
```

## Block Scope

Block scope refers to the scope of variables declared within a block. In JavaScript, variables declared with `let` and `const` are block-scoped, meaning they are only accessible within the block in which they are declared. Variables declared with `var` are not block-scoped; they are function-scoped or globally scoped if declared outside a function.

### Example with `let` and `const`:
```javascript
if (true) {
  let a = 10;
  const b = 20;
  console.log(a); // Output: 10
  console.log(b); // Output: 20
}

// console.log(a); // ReferenceError: a is not defined
// console.log(b); // ReferenceError: b is not defined
```

### Example with `var`:
```javascript
if (true) {
  var c = 30;
  console.log(c); // Output: 30
}
console.log(c); // Output: 30 (var is not block-scoped, it is function-scoped or globally scoped)
```

## `let` and `const` in Loops

Block scope is particularly useful in loops where the loop variable should be limited to the loop's block.

### Example:
```javascript
for (let i = 0; i < 3; i++) {
  console.log(i); // Output: 0, 1, 2
}
// console.log(i); // ReferenceError: i is not defined
```

### Example with `var` (not block-scoped):
```javascript
for (var j = 0; j < 3; j++) {
  console.log(j); // Output: 0, 1, 2
}
console.log(j); // Output: 3 (var is not block-scoped)
```

## Function Scope vs. Block Scope

Understanding the difference between function scope and block scope is crucial for writing effective JavaScript code.

### Function Scope:
```javascript
function testFunction() {
  var x = 1;
  if (true) {
    var x = 2; // Same variable as above, due to function scope
    console.log(x); // Output: 2
  }
  console.log(x); // Output: 2
}
testFunction();
```

### Block Scope:
```javascript
function testBlockScope() {
  let y = 1;
  if (true) {
    let y = 2; // Different variable, due to block scope
    console.log(y); // Output: 2
  }
  console.log(y); // Output: 1
}
testBlockScope();
```

## Temporal Dead Zone (TDZ)

- The Temporal Dead Zone is the period between the start of the execution of a block and the point where a variable is declared and initialized.
- During this time, any reference to the variable will result in a `ReferenceError`.
Note : var store in gloabl space where let and const not store in separate memory space(script) so it's not accessible and gives refrence error
### Example of Temporal Dead Zone

```javascript
console.log(myVar); // Output: undefined (due to hoisting)
console.log(myLet); // Error: Cannot access 'myLet' before initialization
console.log(myConst); // Error: Cannot access 'myConst' before initialization

var myVar = 10;
let myLet = 20;
const myConst = 30;
```

### JavaScript Variable Declaration: `var`, `let`, and `const`

## `var`

`var` is used to declare variables in JavaScript. It has function scope, meaning it's accessible within the function it is declared in. It can be redeclared and updated.

### Example:
```javascript
var x = 10;
console.log(x); // Output: 10

var x = 20; // Redeclaration is allowed
console.log(x); // Output: 20

x = 30; // Updating the value is allowed
console.log(x); // Output: 30
```

## `let`

`let` is used to declare variables that are block-scoped. Variables declared with `let` can be updated but not redeclared within the same scope.

### Key Points:
- We cannot redeclare a `let` variable in the same scope.
- It is block-scoped.

### Example:
```javascript
let y = 10;
console.log(y); // Output: 10

// let y = 20; // SyntaxError: Identifier 'y' has already been declared

y = 20; // Updating the value is allowed
console.log(y); // Output: 20
```

## `const`

`const` is used to declare variables that are block-scoped and whose values cannot be reassigned. The variable must be initialized at the time of declaration.

### Key Points:
- We cannot redeclare a `const` variable in the same scope.
- We must assign a value at the time of declaration.
- The value of a `const` variable cannot be changed through reassignment, but if it's an object or array, the properties or elements can be modified.

### Example:
```javascript
const z = 10;
console.log(z); // Output: 10

// const z = 20; // SyntaxError: Identifier 'z' has already been declared

// z = 20; // TypeError: Assignment to constant variable

const obj = { key: 'value' };
obj.key = 'newValue'; // Allowed: Object properties can be modified
console.log(obj.key); // Output: 'newValue'

const arr = [1, 2, 3];
arr.push(4); // Allowed: Array elements can be modified
console.log(arr); // Output: [1, 2, 3, 4]
```

## Memory Location

Variables declared with `let` and `const` are stored in separate memory locations compared to `var`. This helps avoid hoisting issues and ensures block scoping.

### Example:
```javascript
if (true) {
  var a = 1; // Function-scoped or globally scoped
  let b = 2; // Block-scoped
  const c = 3; // Block-scoped
}
console.log(a); // Output: 1
// console.log(b); // ReferenceError: b is not defined
// console.log(c); // ReferenceError: c is not defined
```
---

# Common JavaScript Errors

JavaScript errors are categorized into different types, each indicating a specific kind of issue in your code. Here are some of the most common JavaScript errors:

## `SyntaxError`

A `SyntaxError` occurs when the code syntax is incorrect and cannot be parsed by the JavaScript engine.

### Example:
```javascript
// Missing closing parenthesis
console.log("Hello, world!" // SyntaxError: Unexpected end of input

// Using a reserved keyword as a variable name
var let = 10; // SyntaxError: Unexpected token let
```

## `ReferenceError`

A `ReferenceError` occurs when a variable that has not been declared is referenced in the code.

### Example:
```javascript
console.log(x); // ReferenceError: x is not defined

function test() {
  console.log(y); // ReferenceError: y is not defined
  let y = 5;
}
test();
```

## `TypeError`

A `TypeError` occurs when a value is not of the expected type or when an operation is performed on a value of the wrong type.

### Example:
```javascript
// Trying to call a non-function as a function
var x = 10;
x(); // TypeError: x is not a function

// Accessing a property on `undefined` or `null`
var obj = null;
console.log(obj.property); // TypeError: Cannot read property 'property' of null
```
## Handling Errors with `try...catch`

JavaScript provides the `try...catch` block to handle runtime errors gracefully.

### Example:
```javascript
try {
  // Code that may throw an error
  let result = riskyOperation();
  console.log(result);
} catch (error) {
  // Handling the error
  console.error('An error occurred:', error.message);
} finally {
  // Code that will run regardless of an error occurring or not
  console.log('This will always run');
}

function riskyOperation() {
  // Example function that throws an error
  throw new Error('Something went wrong!');
}
```

# Shadowing and Deep Copy in JavaScript

## Shadowing

Shadowing occurs when a variable declared within a certain scope (e.g., a block or function) has the same name as a variable declared in an outer scope. The inner variable "shadows" the outer variable, making the outer variable inaccessible within the inner scope.

### Example of Shadowing:
```javascript
let x = 10;

function shadowExample() {
  let x = 20; // This x shadows the outer x
  console.log(x); // Output: 20
}

shadowExample();
console.log(x); // Output: 10 (outer x is unaffected)
```

### Example with `var`:
```javascript
var y = 30;

if (true) {
  var y = 40; // This y shadows the outer y within the function scope
  console.log(y); // Output: 40
}

console.log(y); // Output: 40 (outer y is affected due to function scope)
```

## Deep Copy

A deep copy is a process where all levels of an object or array are copied. This means that nested objects and arrays are also duplicated, creating a completely independent copy. In contrast, a shallow copy only duplicates the top-level properties. This means only the top-level properties are copied, and nested objects are still referenced.

### Example of Shallow Copy:
```javascript
let original = { a: 1, b: { c: 2 } };
let shallowCopy = Object.assign({}, original);

shallowCopy.b.c = 3;
console.log(original.b.c); // Output: 3 (original object is affected)
```

### Example of Deep Copy:
```javascript
let original = { a: 1, b: { c: 2 } };

// Using JSON methods (not recommended for all cases due to loss of functions and undefined values)
let deepCopy = JSON.parse(JSON.stringify(original));

deepCopy.b.c = 3;
console.log(original.b.c); // Output: 2 (original object is unaffected)
```

## Practical Usage of Deep Copy

Deep copies are essential when working with complex data structures where changes to a copied object should not affect the original object. This is particularly important in state management, functional programming, and scenarios involving immutability.

### Example in State Management:
```javascript
let state = {
  user: { name: 'Alice', age: 25 },
  settings: { theme: 'dark', notifications: true }
};

let newState = deepCopy(state);
newState.user.name = 'Bob';

console.log(state.user.name); // Output: Alice (original state is unaffected)
console.log(newState.user.name); // Output: Bob
```
Certainly! Let's delve into closures in JavaScript from the perspective of lexical environments. 

## Lexical Environment and Closures

A lexical environment is the environment in which a function was created. It consists of any local variables that were in-scope at the time the function was defined.

### What is a Closure?

A closure is formed when an inner function is defined within an outer function and the inner function retains access to the outer function's variables even after the outer function has returned. This ability of the inner function to access the outer function’s scope is what constitutes a closure.
Funaction along with it's lexical scope which bundle together forms a closure.
### Lexical Environment

The lexical environment includes:
- The local environment where the function is defined (variables, constants, parameters).
- The outer environment (parent scopes up to the global scope).

### Example of Closure with Lexical Environment

Here’s an example that illustrates closures with lexical environments:

```javascript
function outerFunction() {
  let outerVariable = 'I am outside!';
  
  function innerFunction() {
    console.log(outerVariable); // Inner function can access outer function's variable
  }

  return innerFunction;
}

const myClosure = outerFunction();
myClosure(); // Output: I am outside!
```

### Lexical Environment Example with State

Let’s see a more complex example where closures help maintain state across function calls:

```javascript
function createCounter() {
  let count = 0; // Private variable

  return {
    increment: function() {
      count++;
      console.log(count);
    },
    decrement: function() {
      count--;
      console.log(count);
    },
    getCount: function() {
      return count;
    }
  };
}

const counter = createCounter();
counter.increment(); // Output: 1
counter.increment(); // Output: 2
counter.decrement(); // Output: 1
console.log(counter.getCount()); // Output: 1
```

Using closures in loops can sometimes be tricky due to how lexical environments work. Here’s an example with closures inside a loop:

```javascript
function createArrayOfClosures() {
  let closures = [];
  
  for (let i = 0; i < 3; i++) {
    closures.push(function() {
      console.log(i); // Each closure captures the current value of `i`
    });
  }

  return closures;
}

let myClosures = createArrayOfClosures();
myClosures[0](); // Output: 0
myClosures[1](); // Output: 1
myClosures[2](); // Output: 2
```
### Summary

- **Closures** allow functions to retain access to their lexical environment.
- **Lexical environments** consist of local variables and their parent scopes.
- **Example** demonstrates closures maintaining state and working within loops.

