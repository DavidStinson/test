# JavaScript Scope - Function and Block Scope

![Hero image](./assets/hero.png)

**Learning Objective**: Students will understand how function and block scope work in JavaScript.

## Simularities of function and block scope

Function scope and block scope behave similarly, so it makes sense to bundle these types of scope when we're thinking about them.

- **Function scope** applies to a variable declared inside a function (including its parameters).

- **Block scope** applies to a variable declared inside a block of code, such as an `if` block or a `for` loop (including any variables defined inside the `( )` of the `for` loop).

Taken together, what this means is that any variable we declare that is encased within curly braces `{ }` can only be used inside of those curly braces.

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

A significant benefit of having different scopes is that we can use the same variable names in different functions without causing conflicts or safety concerns. If there were only one scope, this would not be possible.

## Differences between function and block scope

So, if these two types of scope are similar, why do we refer to them separately?

First - variables declared with the `var` keyword do not respect block scope. This means that `var` is generally less safe and can complicate scope. Therefore, its usage is frowned upon, so we don't use it in our content, and neither should you when you write code. If you want to learn more about why you shouldn't use it, check out the [`var` Level Up](../level-up/var.md).

Second - variables in a function's scope only exist while the function executes unless the function creates a closure. Closures are a topic not in the scope of this content.
