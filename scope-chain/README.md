# JavaScript Scope - The Scope Chain

## What is the scope chain?


The scope chain is a mechanism that allows JavaScript to find variables and functions when they are referenced in code. It's a chain of scopes, where each scope is a collection of variables and functions that are accessible within that scope.

When a variable or function is referenced in code, the JavaScript engine searches the scope chain for that variable or function, starting from the innermost scope and working its way out. If the variable or function is not found in any of the scopes, the engine throws a **ReferenceError**.

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

## You can go up the scope chain, but not down it!

A key takeaway is that functions have access to the set of variables and functions defined within their own scope AND in the **outer** scopes. When a line of code accesses a variable (or function), JS will traverse up the scope chain until it finds what it’s looking for.

This means that you can access variables and functions that are declared in the global scope from within any function. However, you cannot access variables and functions that are declared in a function from outside of that function.

If the JS runtime engine gets to the global scope (which is the top of the food chain in the scope hierarchy) and still can’t find what it’s looking for, that’s when your program ceases due to a **ReferenceError**.

Try it out!

```js
let a = 4

function foo(x) {
  let b = a * 4

  function bar(y) {
    let c = y * b
    return c
  }

  return bar(b)
}

console.log(foo(a))
```

> ❓ Does the above function `foo` have access to the variable `c`?

