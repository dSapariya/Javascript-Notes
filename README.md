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

