<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 3. Decisions and Loops

## Decision making - the if and switch statements

### Comparison operators
|Operator symbol|Purpose|
|------|------|
|`==`|Tests if LHS is equal to RHS|
|`<`|Tests if LHS is less than RHS|
|`>`|Tests if LHS is greater than RHS|
|`<=`|Tests if LHS is less than or equal to RHS|
|`>=`|Tests if LHS is greater than or equal to RHS|
|`!=`|Tests if LHS is not equal to RHS|

### Assigning the results of comparisons
```
var age = prompt("Enter age:", "");
var isOverSixty = parseInt(age, 10) > 60;
document.write("Older than 60: " + isOverSixty);
```
> You can store the results of a comparison in a variable, the result is either true or false.

### The `if` Statement
**The `if` statement**: Using the `if` statement, you can choose to execute a block of code (defined by being in curly braces) when a condition is `true`. The `if` statement has a test condition, specified in parentheses. If this condition evaluates to `true`, the code after the `if` statement will execute.
```
if (roomTemperature > 80)                 // if test condition () is true
{
  roomTemperature = roomTemperature - 10; // then execute all the code in {}
}
```
> `{}` - *block* of code; marking out lines of code as belonging to a single block means that JavaScript will treat them all as one piece of code

### Logical Operators
|Operator|Symbol|
|---|---|
|AND|`&&`|
|OR|`∣∣`|
|NOT|`!`|
* `&&` and `||` are *bitwise operators* used in binary operations => two symbols

#### How to use NOT operator
```
if (!(degCent < 100)) {
  // Some code
}
```
> **NOT** operator reverses the logic of a result; it takes one boolean value and changes it to the other boolean value, so it changes `true` to `false` and `false` to `true` - this is sometimes called *negation*.

#### Multiple conditions inside an `if` statement
```
if (degCent > 0 && degCent < 100) {
  document.write("degCent is between 0 and 100");
}
```

### `Else` and `else if`
**The `else` statement**: If you want code to execute when the `if` statement is `false`, you can use the `else` statement that appears after the `if` statement.
```
if (myAge >= 0 && myAge <= 10) {
  document.write("myAge is between 0 and 10");
} else {
  document.write("myAge is NOT between 0 and 10");
}
```
```

if (myAge >= 0 && myAge <= 10) {
  document.write("myAge is between 0 and 10");
} else if ((myAge >= 30 && myAge <= 39) || (myAge >= 80 && myAge <= 89)) {
  document.write("myAge is between 30 and 39 " + "or myAge is between 80 and 89");
} else {
  document.write("myAge is NOT between 0 and 10, " + "nor is it between 30 and 39, nor " + "is it between 80 and 89");
}
```

### Comparing strings
`"Paul" == "Paul"` => TRUE
`"paul" == "Paul"` => FALSE, since case sensitive
`"A" < "B"` => TRUE
`"a" < "B"` => FALSE, since uppercase letters always come *before* lowercase letter

### The `switch` statement
**The `switch` statement**: This compares the result of an expression with a series of possible cases and is similar in effect to a multiple if statement.
```
switch(myName)        //variable expression being checked
{
  case "Paul":        //checking for possible values, if match is found ->
    //some code       //then execution starts below the case statement ->
    break;            //and ends at the break statment
  case "John":
    //some other code
    break;
  default:
    //default code    //this code executes when none of the case statements match
    break;
}
```
> Best way to think of `switch` is "switch to the code where the case matches"

```
switch (secretNumber) {
  case 1:         //if there is no break - execution will continue until break
  case 2:
    document.write("Too low!");
    break;

  case 3:
    document.write("You guessed the secret number!");
    break;

  default:
    document.write("You did not enter a number between 1 and 3.");
}
```
------
## Looping - the `for` and `while` statements
Looping means repeating a block of code when a condition is `true`.

### The `for` loop
**The `for` loop**: Useful for looping through code a certain number of times, the `for` loop consists of three parts: the initialization, test condition, and increment parts. Looping continues while the test condition is `true`. Each loop executes the block of code and then executes the increment part of the `for` loop before re‐evaluating the test condition to see if the results of incrementing have changed it.
* Logic of `for` statement is split into three parts:
  1. `loopCounter = 1` - *initialization*, executed once
  2. `loopCounter <=3` - *test condition*, code will keep executing for as long as this test condition evaluates to `true`
  3. `loopCounter++` - *increment*, where variables in *test condition* have their values incremented

```
var loopCounter;
for (loopCounter = 1; loopCounter <=3; loopCounter++)
{
    //execute this code
}
```

### The `for...in` loop
**The `for...in` loop**: This is useful when you want to loop through an array without knowing the number of elements in the array. JavaScript works this out for you so that no elements are missed.
`for (index in arrayName) {//some code}` - general syntax for use with arrays
```
var myArray = ["Paul", "Paula", "Pauline"];
// To access each element using a conventional `for` loop, you'd write this:
for (var loopCounter = 0; loopCounter < 3; loopCounter++) {
    document.write(myArray[loopCounter]);
}
// To do exactly the same thing with the `for...in` loop, you write this:
for (var elementIndex in myArray) {
    document.write(myArray[elementIndex]);
}
```

### The `while` loop
**The `while` loop**: This is useful for looping through some code for as long as a test condition remains `true`. It consists of a test condition and the block of code that’s executed only if the condition is `true`. If the condition is never `true`, the code never executes.
```
var degCent = 100;
while (degCent != 100) //condition - keep looping while this is still true
{
  //some code         //code looped through
}
```

### The `do...while` loop
**The `do...while` loop**: This is similar to a `while` loop, except that it executes the code once and then keeps executing the code as long as the test condition remains `true`.
```
var userAge;
do {
  userAge = prompt("Please enter your age", "") //will be executed regardless ->
} while (isNaN(userAge) == true);               //of the while statement condition
```

### The `break` and `continue` statements
The `break` statement can be used as part of the `for` and `while` loops when you want to exit the loop prematurely. On hitting a break statement, code execution stops for the block of code marked out by the curly braces and starts immediately after the closing brace.
Example of `break`:
```
var degFahren = [212, "string data", ‐459.67];
var degCent = [];
var loopCounter;
for (loopCounter = 0; loopCounter <= 2; loopCounter++) {
  if (isNaN(degFahren[loopCounter])) {
    alert("Data '" + degFahren[loopCounter] + "' at array index " + loopCounter + " is invalid");
    break;
  }
  degCent[loopCounter] = 5/9 * (degFahren[loopCounter] - 32);
}
```
The `continue` statement is similar to `break`, except that when code execution stops at that point in the loop, the loop is not broken out of but instead continues as if the end of that reiteration had been reached.
> `break` vs `continue` = `all or nothing` vs `at least something`

Example of `continue`:
```
if (isNaN(degFahren[loopCounter])) {
  alert("Data '" + degFahren[loopCounter] + "' at array index " + loopCounter + " is invalid");
  continue;
}
```
