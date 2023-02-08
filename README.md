# FCC---Debugging

JavaScript debugging module

## Use JavaScript Console to Check the Value of a Variable

- The console.log() method displays the output of what's specified within the parentheses of the console.
- This is one of the most helpful tool debugging your code.
- Placing the console.log() at various strategic points in the code can show you the intermediate values of variables.
- It's a good idea to develop a habit of performing interim checks on your code.
- It will help narrow down the bug.
- It is also good practice to have a good idea of what the output should be rather than relying on the console.log()

## Browser Console

- The FCC console behaves a bit differently compared to the browser console.
- FCC console only displays 'log' messages, whereas the browser console will output all messages.
- When changes are made to the code, it runs automatically and shows the relevant logs.
- However, FCC console clears all messages except for the log messages.

- Use the 'inspect' tool on the browser to view the browser console.

## Use typeof to Check the Type of a Variable

- Use ``` typeof ``` to check the data structure, or type, of a variable.
- This is useful when working with multiple data types.
- Type errors are common in calculations and function calls.

Examples

```js
console.log(typeof "");     // "string"
console.log(typeof 0);      // "number
console.log(typeof []);     // "object"  NOTE: Arrays are technically objects in JavaScript
console.log(typeof {});     // "object"
```

- JavaScript recognizes seven primitive (immutable) data types:
  - Boolean
  - Null
  - Undefined
  - Number
  - String
  - Symbol (new with ES6)
  - BigInt (new with ES2020)
- And one type of mutable item: Object

```js
let seven = 7;
let three = "3";
console.log(seven + three);     // console will display 73 since 'three' is defined as a string "3"
console.log(typeof seven);      // "number"
console.log(typeof three);      // "string"
```
