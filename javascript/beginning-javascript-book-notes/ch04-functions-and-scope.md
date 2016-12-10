<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 4. Functions and scope

## Creating your own functions
General syntax:
```
var <functionName> = function (parameter) { //declare the function and give it a name
    <reusable code>;                        //code we want to use again and again
};
<functionName> (parameter);                 //run the function
```
Example:
```
// This is what a function looks like:
var divideByThree = function (number) {
    var val = number / 3;
    console.log(val);
};
divideByThree (6)                         //divide 6 by 3 and show the result of 2
```
> NOTE: Even if the function has no parameters, you must still put the open and close parentheses after its name.

## `Return` keyword
The `return` keyword simply gives the programmer back the value that comes out of the function. So the function runs, and when the return keyword is used, the function will immediately stop running and return the value.
```
// Parameter is a number, and we do math with that parameter
var timesTwo = function(number) {
    return number * 2;
};
// Call timesTwo here!
var newNumber = timesTwo (6);
console.log(newNumber);                   //gives the result of 12
```
> When JavaScript comes across a `return` statement in a function, it treats it a bit like a `break` statement in a `for` loop — it exits the function, returning any value specified after the `return` keyword.

## Functions with multiple parameters
```
var areaBox = function(length, width) {
    return length * width;
};
areaBox(3,9);                           //would return the area of a box with a length of 3 and a width of 9
```

## Scope: global vs local variables
### Global scope
Any variables or functions declared outside of a function will be available to all JavaScript code on the page, whether that code is inside a function or otherwise — we call this *global scope*.
Example of global variable:
```
var globalVar = "hello";

var foo = function() {
    console.log(globalVar);  // prints "hello"
}
```
### Functional scope
Variables and functions declared inside a function are visible only inside that function — no code outside the function can access them. This is commonly referred to as *functional* or *local scope*, and such variable is commonly called a *local* variable.
Example of local variable:
```
var bar = function() {
    var localVar = "howdy";
}
console.log(localVar);  // error
```
> Variables not only have the scope property — where they are visible — but they also have a **lifetime**. When the function finishes executing, the variables in that function die and their values are lost, unless you return one of them to the calling code.

## Functions as values
```
function convertToCentigrade(degFahren) {
  var degCent = 5/9 * (degFahren - 32);
  return degCent;
}
var myFunction = convertToCentigrade;
var degCent = myFunction(75); // 23.88888889
var degCent2 = convertToCentigrade(75); // 23.88888889
```
> Assigning function (without parentheses) to a variable works pretty much like an alias, you can use that variable to call a corresponding function.
> This also means we can pass a function to another function’s parameter.

```
function toFahrenheit(degCent) {
      var degFahren = 9 / 5 * degCent + 32;
      document.write(degCent + " Celsius is " + degFahren + " Fahrenheit.<br/>");
    }
    function convert(converter, temperature) {
      converter(temperature);
    }
    convert(toFahrenheit, 23);
```

## Loops in functions
```
calcMultiple(firstMultiple, secondMultiple) {
  for (let i = 1; i <= secondMultiple; i++) {
      console.log(firstMultiple + "x" + i + " = " + firstMultiple * i + "</br>");
  }
}
calcMultiple(5,7);
```
