### Beginner Topics

1. **Syntax and Basics**
   - **Variables**
     - **Question**: What is the difference between `var`, `let`, and `const`?
     - **Answer**: `var` is function-scoped and can be re-declared. `let` and `const` are block-scoped; `let` can be updated but not re-declared, while `const` cannot be updated or re-declared.

   - **Example**: Create a simple calculator that performs addition.
     ```javascript
     function add(a, b) {
       return a + b;
     }
     console.log(add(2, 3)); // Output: 5
     ```

2. **Control Structures**
   - **Question**: How do you write a conditional statement in JavaScript?
   - **Answer**: Using `if`, `else if`, and `else` keywords.
     ```javascript
     let number = 10;
     if (number > 0) {
       console.log('Positive');
     } else if (number < 0) {
       console.log('Negative');
     } else {
       console.log('Zero');
     }
     ```

   - **Example**: Write a program that prints all prime numbers up to a given number.
     ```javascript
     function isPrime(num) {
       if (num <= 1) return false;
       for (let i = 2; i < num; i++) {
         if (num % i === 0) return false;
       }
       return true;
     }
     
     function printPrimes(limit) {
       for (let i = 2; i <= limit; i++) {
         if (isPrime(i)) console.log(i);
       }
     }
     printPrimes(10); // Output: 2, 3, 5, 7
     ```

3. **Functions**
   - **Question**: What is the difference between function declarations and function expressions?
   - **Answer**: Function declarations are hoisted and can be called before they are defined. Function expressions are not hoisted.
     ```javascript
     // Function Declaration
     function greet() {
       return 'Hello';
     }

     // Function Expression
     const greet = function() {
       return 'Hello';
     };
     ```

   - **Example**: Create a function that checks if a string is a palindrome.
     ```javascript
     function isPalindrome(str) {
       const reversed = str.split('').reverse().join('');
       return str === reversed;
     }
     console.log(isPalindrome('racecar')); // Output: true
     ```

4. **Events and DOM Manipulation**
   - **Question**: How do you add an event listener to a button in JavaScript?
   - **Answer**: Using the `addEventListener` method.
     ```javascript
     document.getElementById('myButton').addEventListener('click', function() {
       alert('Button clicked!');
     });
     ```

   - **Example**: Build a to-do list application where users can add and remove tasks.
     ```html
     <input type="text" id="taskInput">
     <button id="addTaskButton">Add Task</button>
     <ul id="taskList"></ul>
     
     <script>
       document.getElementById('addTaskButton').addEventListener('click', function() {
         const taskInput = document.getElementById('taskInput');
         const task = taskInput.value;
         if (task) {
           const li = document.createElement('li');
           li.textContent = task;
           document.getElementById('taskList').appendChild(li);
           taskInput.value = '';
         }
       });
     </script>
     ```

### Intermediate Topics

5. **Arrays and Objects**
   - **Question**: How do you add and remove elements from an array in JavaScript?
   - **Answer**: Using `push` to add and `pop` to remove the last element, `shift` to remove the first element, and `unshift` to add at the beginning.
     ```javascript
     let fruits = ['apple', 'banana'];
     fruits.push('orange'); // ['apple', 'banana', 'orange']
     fruits.pop(); // ['apple', 'banana']
     fruits.shift(); // ['banana']
     fruits.unshift('mango'); // ['mango', 'banana']
     ```

   - **Example**: Create a shopping cart where items can be added, removed, and the total price is calculated.
     ```javascript
     const cart = [];
     
     function addItem(item) {
       cart.push(item);
     }

     function removeItem(itemName) {
       const index = cart.findIndex(item => item.name === itemName);
       if (index !== -1) {
         cart.splice(index, 1);
       }
     }

     function getTotalPrice() {
       return cart.reduce((total, item) => total + item.price, 0);
     }

     addItem({ name: 'Apple', price: 1.0 });
     addItem({ name: 'Banana', price: 0.5 });
     console.log(getTotalPrice()); // Output: 1.5
     removeItem('Apple');
     console.log(getTotalPrice()); // Output: 0.5
     ```

6. **Asynchronous JavaScript**
   - **Question**: What are Promises and how do you use them?
   - **Answer**: Promises represent the eventual completion (or failure) of an asynchronous operation and its resulting value.
     ```javascript
     function fetchData() {
       return new Promise((resolve, reject) => {
         setTimeout(() => resolve('Data fetched!'), 1000);
       });
     }

     fetchData().then(data => console.log(data)); // Output: Data fetched!
     ```

   - **Example**: Fetch data from an API and display it on a webpage.
     ```html
     <div id="data"></div>
     
     <script>
       fetch('https://api.example.com/data')
         .then(response => response.json())
         .then(data => {
           document.getElementById('data').textContent = JSON.stringify(data);
         })
         .catch(error => console.error('Error fetching data:', error));
     </script>
     ```

7. **Error Handling**
   - **Question**: How do you handle errors in JavaScript using try...catch?
   - **Answer**: Use `try` to wrap the code that may throw an error, and `catch` to handle the error.
     ```javascript
     try {
       // Code that may throw an error
       let result = riskyFunction();
     } catch (error) {
       console.error('An error occurred:', error);
     }
     ```

   - **Example**: Build a form that validates user input and provides error messages if the input is invalid.
     ```html
     <input type="text" id="nameInput">
     <button id="submitButton">Submit</button>
     <p id="errorMessage"></p>
     
     <script>
       document.getElementById('submitButton').addEventListener('click', function() {
         const nameInput = document.getElementById('nameInput').value;
         try {
           if (nameInput === '') {
             throw new Error('Name is required');
           }
           document.getElementById('errorMessage').textContent = '';
           alert('Form submitted successfully!');
         } catch (error) {
           document.getElementById('errorMessage').textContent = error.message;
         }
       });
     </script>
     ```

8. **Local Storage and Session Storage**
   - **Question**: How do you store and retrieve data using local storage?
   - **Answer**: Use `localStorage.setItem` to store data and `localStorage.getItem` to retrieve it.
     ```javascript
     // Store data
     localStorage.setItem('username', 'JohnDoe');

     // Retrieve data
     const username = localStorage.getItem('username');
     console.log(username); // Output: JohnDoe
     ```

   - **Example**: Enhance the to-do list application to save tasks in local storage.
     ```html
     <input type="text" id="taskInput">
     <button id="addTaskButton">Add Task</button>
     <ul id="taskList"></ul>
     
     <script>
       document.getElementById('addTaskButton').addEventListener('click', function() {
         const taskInput = document.getElementById('taskInput');
         const task = taskInput.value;
         if (task) {
           addTask(task);
           saveTasks();
           taskInput.value = '';
         }
       });

       function addTask(task) {
         const li = document.createElement('li');
         li.textContent = task;
         document.getElementById('taskList').appendChild(li);
       }

       function saveTasks() {
         const tasks = [];
         document.querySelectorAll('#taskList li').forEach(li => {
           tasks.push(li.textContent);
         });
         localStorage.setItem('tasks', JSON.stringify(tasks));
       }

       function loadTasks() {
         const tasks = JSON.parse(localStorage.getItem('tasks'));
         if (tasks) {
           tasks.forEach(task => addTask(task));
         }
       }

       loadTasks();
     </script>
     ```

### Advanced Topics

9. **Advanced Functions**
   - **Question**: What is a closure in JavaScript?
   - **Answer**: A closure is a function that retains

 access to its lexical scope, even when the function is executed outside that scope.
     ```javascript
     function createCounter() {
       let count = 0;
       return function() {
         count++;
         return count;
       };
     }

     const counter = createCounter();
     console.log(counter()); // Output: 1
     console.log(counter()); // Output: 2
     ```

   - **Example**: Implement a debounce function to limit the rate at which a function can fire.
     ```javascript
     function debounce(func, wait) {
       let timeout;
       return function(...args) {
         clearTimeout(timeout);
         timeout = setTimeout(() => func.apply(this, args), wait);
       };
     }

     const logMessage = debounce(() => console.log('Debounced!'), 1000);

     // Will only log 'Debounced!' once, even though it's called multiple times
     logMessage();
     logMessage();
     logMessage();
     ```

10. **Object-Oriented JavaScript**
    - **Question**: How do you create a class in JavaScript?
    - **Answer**: Use the `class` keyword.
      ```javascript
      class Person {
        constructor(name, age) {
          this.name = name;
          this.age = age;
        }

        greet() {
          return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
        }
      }

      const john = new Person('John', 30);
      console.log(john.greet()); // Output: Hello, my name is John and I am 30 years old.
      ```

    - **Example**: Create a simple game (e.g., tic-tac-toe) using object-oriented principles.
      ```javascript
      class TicTacToe {
        constructor() {
          this.board = Array(9).fill(null);
          this.currentPlayer = 'X';
        }

        makeMove(position) {
          if (!this.board[position]) {
            this.board[position] = this.currentPlayer;
            this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X';
            return true;
          }
          return false;
        }

        checkWinner() {
          const winningCombinations = [
            [0, 1, 2],
            [3, 4, 5],
            [6, 7, 8],
            [0, 3, 6],
            [1, 4, 7],
            [2, 5, 8],
            [0, 4, 8],
            [2, 4, 6]
          ];

          for (const [a, b, c] of winningCombinations) {
            if (this.board[a] && this.board[a] === this.board[b] && this.board[a] === this.board[c]) {
              return this.board[a];
            }
          }
          return null;
        }
      }

      const game = new TicTacToe();
      game.makeMove(0);
      game.makeMove(1);
      game.makeMove(3);
      game.makeMove(4);
      game.makeMove(6);
      console.log(game.checkWinner()); // Output: X
      ```

11. **Modules**
    - **Question**: How do you export and import modules in JavaScript?
    - **Answer**: Use `export` to export and `import` to import.
      ```javascript
      // module.js
      export function greet() {
        return 'Hello';
      }

      // main.js
      import { greet } from './module.js';
      console.log(greet()); // Output: Hello
      ```

    - **Example**: Modularize the shopping cart application into separate files.
      ```javascript
      // cart.js
      const cart = [];

      function addItem(item) {
        cart.push(item);
      }

      function removeItem(itemName) {
        const index = cart.findIndex(item => item.name === itemName);
        if (index !== -1) {
          cart.splice(index, 1);
        }
      }

      function getTotalPrice() {
        return cart.reduce((total, item) => total + item.price, 0);
      }

      export { addItem, removeItem, getTotalPrice };

      // main.js
      import { addItem, removeItem, getTotalPrice } from './cart.js';

      addItem({ name: 'Apple', price: 1.0 });
      addItem({ name: 'Banana', price: 0.5 });
      console.log(getTotalPrice()); // Output: 1.5
      removeItem('Apple');
      console.log(getTotalPrice()); // Output: 0.5
      ```

12. **JavaScript Design Patterns**
    - **Question**: What is the Singleton pattern and how do you implement it in JavaScript?
    - **Answer**: The Singleton pattern ensures a class has only one instance and provides a global point of access to it.
      ```javascript
      const Singleton = (function() {
        let instance;

        function createInstance() {
          return new Object('I am the instance');
        }

        return {
          getInstance: function() {
            if (!instance) {
              instance = createInstance();
            }
            return instance;
          }
        };
      })();

      const instance1 = Singleton.getInstance();
      const instance2 = Singleton.getInstance();
      console.log(instance1 === instance2); // Output: true
      ```

    - **Example**: Implement the Observer pattern in a chat application where multiple components need to be notified of new messages.
      ```javascript
      class Subject {
        constructor() {
          this.observers = [];
        }

        subscribe(observer) {
          this.observers.push(observer);
        }

        unsubscribe(observer) {
          this.observers = this.observers.filter(obs => obs !== observer);
        }

        notify(data) {
          this.observers.forEach(observer => observer.update(data));
        }
      }

      class Observer {
        update(data) {
          console.log(`Received message: ${data}`);
        }
      }

      const chatRoom = new Subject();
      const user1 = new Observer();
      const user2 = new Observer();

      chatRoom.subscribe(user1);
      chatRoom.subscribe(user2);

      chatRoom.notify('Hello, World!'); // Output: Received message: Hello, World! (twice)
      ```

### Expert Topics

13. **Functional Programming**
    - **Question**: What is a pure function in JavaScript?
    - **Answer**: A pure function is a function that, given the same inputs, always returns the same output and has no side-effects.
      ```javascript
      function add(a, b) {
        return a + b;
      }
      ```

    - **Example**: Build a library for basic functional utilities like `compose` and `curry`.
      ```javascript
      function compose(...funcs) {
        return function(arg) {
          return funcs.reduceRight((acc, fn) => fn(acc), arg);
        };
      }

      function curry(fn) {
        return function curried(...args) {
          if (args.length >= fn.length) {
            return fn.apply(this, args);
          } else {
            return function(...args2) {
              return curried.apply(this, args.concat(args2));
            };
          }
        };
      }

      const add = (a, b) => a + b;
      const multiply = (a, b) => a * b;

      const curriedAdd = curry(add);
      console.log(curriedAdd(1)(2)); // Output: 3

      const addThenMultiply = compose(
        b => multiply(b, 2),
        a => add(a, 2)
      );
      console.log(addThenMultiply(2)); // Output: 8
      ```

14. **Performance Optimization**
    - **Question**: What is debouncing and how do you implement it in JavaScript?
    - **Answer**: Debouncing is a technique to limit the rate at which a function is executed. It ensures a function is only executed after a specified time has passed since the last time it was invoked.
      ```javascript
      function debounce(func, wait) {
        let timeout;
        return function(...args) {
          clearTimeout(timeout);
          timeout = setTimeout(() => func.apply(this, args), wait);
        };
      }
      ```

    - **Example**: Optimize a large list rendering application to improve performance.
      ```html
      <input type="text" id="searchInput">
      <ul id="results"></ul>

      <script>
        const data = Array.from({ length: 10000 }, (_, i) => `Item ${i}`);

        function filterResults(query) {
          const results = data.filter(item => item.toLowerCase().includes(query.toLowerCase()));
          displayResults(results);
        }

        function displayResults(results) {
          const resultsList = document.getElementById('results');
          resultsList.innerHTML = results.map(result => `<li>${result}</li>`).join('');
        }

        const debouncedFilter = debounce(filterResults, 300);

        document.getElementById('searchInput').addEventListener('input', function(event) {
          debouncedFilter(event.target.value);
        });
      </script>
      ```

15. **Testing**
    - **Question**: How do you write a unit test in JavaScript using Jest?
    - **Answer**: Use Jest's `test` function to define a test case and `expect` function to make assertions.
      ```javascript
      // sum.js
      function sum(a, b) {
        return a + b;
      }
      module.exports = sum;

      // sum.test.js
      const sum = require('./sum');
      test('

adds 1 + 2 to equal 3', () => {
        expect(sum(1, 2)).toBe(3);
      });
      ```

    - **Example**: Write unit tests for a utility library and end-to-end tests for a web application.
      ```javascript
      // utility.js
      function add(a, b) {
        return a + b;
      }

      function subtract(a, b) {
        return a - b;
      }

      module.exports = { add, subtract };

      // utility.test.js
      const { add, subtract } = require('./utility');
      test('adds 1 + 2 to equal 3', () => {
        expect(add(1, 2)).toBe(3);
      });

      test('subtracts 5 - 2 to equal 3', () => {
        expect(subtract(5, 2)).toBe(3);
      });

      // e2e.test.js
      const puppeteer = require('puppeteer');
      test('should display "Hello World" on page', async () => {
        const browser = await puppeteer.launch();
        const page = await browser.newPage();
        await page.goto('http://localhost:3000');
        const text = await page.$eval('h1', el => el.textContent);
        expect(text).toBe('Hello World');
        await browser.close();
      });
      ```

16. **TypeScript**
    - **Question**: How do you add type annotations in TypeScript?
    - **Answer**: Use `:` followed by the type after variable names and function parameters.
      ```typescript
      let age: number = 30;
      let isStudent: boolean = true;

      function greet(name: string): string {
        return `Hello, ${name}`;
      }
      ```

    - **Example**: Convert an existing JavaScript project to TypeScript.
      ```typescript
      // shoppingCart.ts
      interface Item {
        name: string;
        price: number;
      }

      const cart: Item[] = [];

      function addItem(item: Item): void {
        cart.push(item);
      }

      function removeItem(itemName: string): void {
        const index = cart.findIndex(item => item.name === itemName);
        if (index !== -1) {
          cart.splice(index, 1);
        }
      }

      function getTotalPrice(): number {
        return cart.reduce((total, item) => total + item.price, 0);
      }

      addItem({ name: 'Apple', price: 1.0 });
      addItem({ name: 'Banana', price: 0.5 });
      console.log(getTotalPrice()); // Output: 1.5
      removeItem('Apple');
      console.log(getTotalPrice()); // Output: 0.5
      ```

By progressing through these topics, examples, and questions, you'll develop a deep understanding of JavaScript, preparing you to tackle more complex challenges.
