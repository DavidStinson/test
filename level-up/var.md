# `var` Keyword

In addition to defining variables with `let` and `const`, there is also a *third* way to define variables in JavaScript: by using the `var` keyword.

When JavaScript was created, `var` was the only way to define variables. It's the least restrictive of the three keywords, 
and it allows us to redeclare variables and declare variables without intializing them. 

This lack of restriction can cause a lot of confusion and unintended behavior in our code, and is one of the reasons we don't use `var` (and you shouldn't either). 

Regardless of whether they are defined within a block, variables declared with  `var` always have function scope. This means they're accessible from anywhere within the function in which they were declared. 

The following code from MDN's [docs about let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) and [docs about var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var) demonstrates the differences between `let` and `var`:

```js
function varTest() {
  var x = 1
  if (true) {
    var x = 2  // same variable!
    console.log(x)  // 2
  }
  console.log(x)  // 2
}

function letTest() {
  let x = 1
  if (true) {
    let x = 2  // different variable
    console.log(x)  // 2
  }
  console.log(x)  // 1
}
```

and another example of their differences:

```js
if (true) {
	var x = "yes"
}
console.log(x) // "yes"

if (true) {
	let y = "yes"
}
console.log(y) // ReferenceError: y is not defined
```