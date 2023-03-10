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

- It is a good idea to make it a habit to always close the parentheses, bracket, brace, or quote as soon as you open it.
- Code editor will usually do this for you, but I think it's a good idea to go through with the motion nonetheless.

The contents of the error message will vary depending on the type of error.
Just look for the '>' and '^' to identify where the error occurred.

## Catch Mixed Usage of Single and Double Quotes

- JavaScript allows the use of both single (') and double (") quotes to declare a string.
- Deciding which one to use is generally arbitrary.
- Having two choices is useful when a string has contractions or another piece of text within.
- Mixing up the type of quotes may close a string too early without knowing.
  - You may notice that parts of the code looks different in terms of color when a string is closed early.

``` js
let innerHtml = "<p>Click here to <a href="#Home">return home</a></p>";
```

The console will display the following error

```SyntaxError: unknown: Missing semicolon. (1:43)```

It is expecting to see a semicolon because the double quote after 'href=' closed the initial opening quote.

- It is still possible to use only one kind of quotes (single or double) by using the escape method with backslash (Refer to 'Escape Character' in Basic JavaScript)

## Catch Use of Assignment Operator Instead of Equality Operator

- Branching programs: programs that do different things if certain conditions are met.
  - It relies on if, else if and else statements in JavaScript.
  - The condition sometimes takes the form of testing whether a result is equal to a value.
- This logic, if verbalized, is "if x equals y, then..."
- In code, we use the '=' equal sign.
- But this is also the assignment operator, which can cause some confusion in programming.
- So we use '==' for equality, and '===' for strict equality.

```js
let x = 7;
let y = 9;
let result = "to come";

if (x = y) {
  result = "Equal!";
} else {
  result = "Not Equal!";
}
```

- In the above example, at first glance it looks like it is saying 'if x equals y, then return "Equal!", especially to those who do not understand JavaScript.
- (x = y) is actually assigning the value of y to x.
- So you can assign y to anything (except for 'falsy' values like false,, 0, "", NaN, undefined, or Null) and the result will return "Equal!"
- Therefore, in order for the if statement in the above code to work, it needs to use an equality (==) or a strict equality operator(===).

## Catch Missing Open and Closing Parenthesis After a Function Call

- It is a common mistake to forget to include the empty parentheses when calling a function or a method if it doesn't take any arguments.
- The result of a function call is often saved in a variable for other use in the code.
- To detect this error, log the variable value into the console and see if it returns a function reference or the result of the function return.

```js
function getNine() {
  let x = 6;
  let y = 3;
  return x + y;
}

let result = getNine;   // Missing empty parentheses
console.log(result);
```

- Console will display an error message ```[Function: getNine]```
- In the code above, 'result' is assigned to the value of the function itself, not the result of running the function.
- The message is saying that 'getNine' is supposed to be a function and it requires empty parentheses in order to get its return value.

## Catch Arguments Passed in the Wrong Order When Calling a Function

- Another common mistake is entering function's arguments in a wrong order.
- If the arguments are different types, such as arrays and integers, entering it in an incorrect order will likely throw a runtime error.
- But if the arguments are the same type - for example, all integers - then the result of the function will not make sense.

```js
function raiseToPower(b, e) {
  return Math.pow(b, e);
}

let base = 2;
let exp = 3;
let power = raiseToPower(exp, base);    // The order of base and exp are switched
console.log(power);   // console will display '9'
```

- By making the mistake of swapping the order of exp and base, the function is still executed and returns the result of 3 to the power of 2, not the expected 2 to the power of 3.
- Unfortunately, the console does not throw an obvious error message.
- It simply returns the wrong result.
- 2 to the power of 3 and 3 to the power of 2 is quite simple, and it can be caught with some attention to detail.
- But if the function is more complex, or if it's using larger numbers, it may not be so easy to detect.
- So, the lesson is: BE VIGILANT. Check your code thoroughly.

## Catch Off By One Errors When Using Indexing

- 'Off by one errors' (OBOE) usually happens when you're trying to access a specific index of a string or array, or when looping over the indices of them.
- Remember JavaScript index begins at zero, not one.
- It means that the last index is always one less than the length of the array.
- If by mistake you try to access an index equal to the array length, it will throw an "index out of range" error, or print "undefined" in the console.
- Just remember: JAVASCRIPT INDEXING BEGINS AT 'ZERO'

## Use Caution When Re-initializing Variables Inside a Loop

- Another thing to watch out for is placing variables inside a loop.
- Depending on the variable, it may need to be placed outside of the function (global scope), or inside the function (block scope).
  
Consider the following example

```js
function zeroArray (m, n) {
  let newArray = [];
  let row = [];
  for (let i = 0; i < m; i++) {
    // place 'let row = [];' here
    for (let j = 0; j < n; j++) {
      row.push(0);
    }
    newArray.push(row);
  }
  return newArray;
}

let matrix = zeroArray(3, 2);
console.log(matrix);
```

- The intention of the above code is to create 'm' number of arrays with 'n' number of zeros in each array.
- When ```function zeroArray(3, 2)``` is called, it is supposed to return 3 arrays with 2 zeros in each array ```[[0, 0], [0, 0], [0, 0]]```
- When the function runs as shown above:
  - first it will create an empty newArray and an empty row array
  - index (i) will start at zero, and increment by 1 while (i) is less than 'm' (3).
  - then for the inner loop, index (j) will begin at 0 and increment by 1 while (j) is less than 'n' (2).
  - For the specified conditions, 0 will be pushed into the row array.
  - Then that row array will be pushed into the newArray.
  - In other words, 0 will be pushed into the row array twice (j) and repeated thrice (i), resulting in 6 zeros in a newArray before it is returned.
  - This pattern will repeat three times (m value) before the function terminates, resulting in 3 separate newArray with 6 zeros each.
- At least I think that is what is happening here.

- In order for the above code to execute as intended, the 'row' variable needs to be placed after the first 'for' loop.
  - That will allow the (j) index to run and push 0 into the row array 'n' number of times and push the completed row array to the newArray. (inner loop)
  - This pattern will repeat 'm' number of times (outer loop) before the function terminates and returns the complete newArray.

## Prevent Infinite Loops with a Valid Terminal Condition

- Loops are great tools, but it may cause all sorts of problems if the terminal condition is not set properly.
- An example of an infinite loop is shown below:

  ```js
  function loopy() {
    while(true) {
      console.log("Hello, World!");
    }
  }   // DO NOT CALL THIS FUNCTION
  ```

- It's the programmer's responsibility to ensure that the terminal condition that tells the program when to break the loop is ultimately reached.
- A common mistake would incrementing or decrementing a counter variable in the wrong direction, or resetting a counter or index variable within the loop code.

Another example:

```js
function myFunc() {
  for (let i = 1; i != 4; i += 2); {
    console.log("Still going!");
  }
}
```

- In the above code, when myFunc() is called, variable 'i' will begin at '1' and increment by '2' while 'i' is not equal to '4'.
- The problem is, since 'i' begins counting at 1, an odd number, and it increments by '2', it will never equal '4'. In other words, it will never break the loop.
- to fix this problem, variable 'i' can be assigned with an even number that is less than '4' (which only leaves '2'), or '0'.
- Another method would be to modify the comparison operator so that the loop breaks when 'i' is less than or equal to '4' (i <= 4).

## Final Statement

I think the most important lesson that I could learn from this module is that ATTENTION TO DETAIL is the most effective method to preventing bugs.
Errors and bugs will be inevitable. Stay Vigilant.
