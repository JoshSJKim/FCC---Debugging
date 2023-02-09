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

## Catch Misspelled Variable and Function Names

- ``` console.log() ``` and ``` typeof ``` are two primary methods to perform interim checks on values and types of program output.
- One of the most common type of bugs is spelling error.
- Misspelled variables will cause a 'reference error'.
- JavaScript variable and function names are case sensitive.

The following error is commonly seen ``` ReferenceError: ("misspelled-variable") is not defined ```

In such cases, console.log() is a useful tool to identify where the spelling error occurred.

## Catch Unclosed Parentheses, Brackets, Braces and Quotes

- All parentheses, brackets, braces, and quotes must have an opening and closing pair.
- If either one of the pair is missing, the console will display a ``` SyntaxError ```

The following code is missing some of its pairs

```js
let myArray = [1, 2, 3;
let arraySum = myArray.reduce((previous, current =>  previous + current);
console.log(`Sum of array values is: ${arraySum}`);
```

The console displays something like this
``` SyntaxError: unknown: Unexpected token, expected "," (1:22) ```
Based on the pattern of the array, it is expecting to see another "," since it doesn't assume that the contents of the array is complete.

It also displays where the error occurred with the '>' to identify the line and '^' to identify the position.
```> 1 | let myArray = [1, 2, 3;```
                            ```^```
- The '^' would normally be exactly where the expected character is. Kind of hard to express it exactly on markdown file.

Note that the console displays only one error at a time.
Once the current error is fixed, it will identify the next error in the code, if found.

If there is a missing closing pair of a quote, the console will display ``` SyntaxError: unknown: Unterminated string constant ```

The contents of the error message will vary depending on the type of error.
Just look for the '>' and '^' to identify where the error occurred.
