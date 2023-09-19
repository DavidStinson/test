# Hoisting

Remember how we can call function declarations before they have been defined thanks to **[hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)**?

Similarly, a variable’s **declaration** (but not its assignment) is hoisted to the top of the function when it’s declared using `var` (but not when it's declared using `let` or `const`).

Hoisting in JavaScript moves all variable declarations to the top of their scope before code execution. This means that no matter where we declare a variable in our code, it will be accessible as if it were declared at the top of the scope.

For example, when we write code like this:

```js
function hoist() {
  console.log(x)  // outputs undefined, not a ReferenceError
  var x = 25
  console.log(x)  // outputs 25
}
```

Internally, the JS engine actually sees this:

```js
function hoist() {
  var x
  console.log(x)  // outputs undefined, not a ReferenceError
  x = 25
  console.log(x)  // outputs 25
}
```


Here are some things to remember about hoisting:
  - Only variable declarations are hoisted, not function declarations.
  
  - Hoisting moves variable declarations to the top of the scope, but **does not** initialize them. This means variables that are hoisted will have a value of `undefined` until they're initialized.
  
  - If you're not careful, hoisting can cause **unexpected behavior**. 