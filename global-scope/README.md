# JavaScript Scope - Global Scope

![Hero image](./assets/hero.png)

**Learning Objective**: Students will understand global scope and some of its pitfalls in JavaScript.

## Global scope

JavaScript has a single **global scope**, which can declare variables and functions accessed from anywhere in the code. Using global variables with caution is essential, as they can be modified by any part of the code, which can lead to unexpected behavior.

Any variable declared outside a function or block will live in the global scope.

Taking our previous example and moving `mainDish` to the global scope allows it to be used anywhere.

```js
let mainDish;

const chooseDinner = () => {
  let isHungry = true;

  if (isHungry) {
    // We are able to modify the global mainDish variable
    mainDish = 'meatloaf';
  } else {
    mainDish = 'corn';
  }
  // Note how variables in the global scope can be modified anywhere!

  console.log(`Dinner tonight is ${mainDish}`);
  // Output: 'Dinner tonight is Meatloaf'
}

chooseDinner();

// Because mainDish was declared in the global scope, it is available.
console.log(mainDish);
// Output: 'meatloaf'
```

## Real-world example

Scope is a tough concept, especially when you're new to coding. To help you further understand, here's a real-world example to illustrate the idea of scope:

Imagine that you are in a library. The entire library is the **global scope**. You can access anything in the library from anywhere in the library.

Now imagine that you go to the children's section. The children's section is a **local scope**. You can access anything in the children's section from inside the children's section, but you cannot access anything outside of the children's section unless you go outside the children's section, thereby re-entering **global scope**.

For example, if you want to get a book from the non-fiction section, you have to leave the children's section and go to the non-fiction section.
