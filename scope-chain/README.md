# The Scope Chain

## What is the scope chain?


The scope chain is a mechanism that allows JavaScript to find variables and functions when they are referenced in code. It's a chain of scopes, where each scope is a collection of variables and functions that are accessible within that scope.

When a variable or function is referenced in code, the JavaScript engine searches the scope chain for that variable or function, starting from the innermost scope and working its way out. If the variable or function is not found in any of the scopes, the engine throws a ReferenceError.

```js
// Global Scope
let name = "Burt"

function greet() {
  // Function Scope
  let message = "Hello, " + name + "!"
  console.log(message)
}

greet()
```

In the example above, the `name` variable is defined in global scope, making it accessible from anywhere in the code. The `message` variable is declared in the function scope of the `greet()` function, so it's only accessible inside of that function. 

## You can go up the scope chain, but not down!

