# ![JavaScript Scope - Function and Block Scope](./assets/hero.png)

**Learning Objective**: By the end of this lesson, students will be able to distinguish between function and block scope in JavaScript, identify how variables behave within these scopes, and understand the benefits and limitations of each.

## What are function and block scope?

Function scope and block scope behave similarly, so it makes sense to bundle these types of scope when we're thinking about them. Both function and block scope in JavaScript deal with where you can access a variable. Let's break it down:

- **Function scope**: When you declare a variable inside a function, it can only be accessed within that function. This includes the function's parameters as well.

- **Block scope**: Similarly, if you declare a variable inside a code block such as within an `if` statement or a `for` loop (including any variables defined inside the `( )`), you can only use that variable within that specific block.

In simpler terms, if you declare a variable inside curly braces `{ }`, whether it's part of a function or a code block, that variable can only be used within those curly braces. This helps keep your code organized and avoids conflicts between variables.

Here are a couple of examples of this:

```js
const addNums = (numA) => {
  // Inside the addNums function
  const numB = 10;

  console.log(numA + numB);
  // Output: 15
};

addNums(5);

// Outside the addNums function:
console.log(numB);
// ERROR: ReferenceError: numB is not defined
// numB is out of scope!
```

Above, you can see that `numB` isn't available outside the `addNums` function.

> ❓ Is `numA` available outside of the `addNums` function?


Let's look at another example:

```js
let isLoggedIn = true;

if (isLoggedIn) {
  // Defining username inside the if block
  const username = 'Frisco';

  console.log(username); 
  // Output: 'Frisco'
}

// Outside the if block:
console.log(username); 
// ERROR: ReferenceError: username is not defined
```

Here, you can see that `username` isn't available outside the block scope created by the `if` statement.

Let's take a look at an example that combines these two ideas:

```js
const chooseDinner = () => {
  let isHungry = true;
  let mainDish;

  if (isHungry) {
    mainDish = 'meatloaf';
  } else {
    mainDish = 'corn';
  }
  // Note how variables that are part of the outer function scope
  // (created by the function) are available to blocks inside its scope!

  console.log(`Dinner tonight is ${mainDish}`);
  // Output: 'Dinner tonight is Meatloaf'
}

chooseDinner();

// Outside of the function, the variables declared within are unavailable.
console.log(mainDish);
// ERROR: ReferenceError: mainDish is not defined
```

An important thing to remember is that variables declared outside a code block or function (e.g. `mainDish` is declared outside the `if/else` block in the example above) are accessible from within that code block or function.

A significant benefit of having different scopes is that we can use the same variable names in different functions without causing conflicts or safety concerns. If there were only one scope, this would not be possible.

## Knowledge Checks

- True/False: variables declared within a function are accessible within it.
- Can you access variables declared outside a function or code block from within the function/code block?
- If a variable is out of scope, will you receive an error?