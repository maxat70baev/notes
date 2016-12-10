<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 5. An object-based language

## Creating an object
```
var myDate = new Date(); //constructor for a *Date* object (*new* - operator)
```

## Using object's properties
You write the name of the variable containing (or referencing) your object, followed by a dot, and then the name of the object’s property.
Example:
`myArray.length` - access length property
> NOTE: some properties are *read-only*.

## Calling an object's methods
Using the methods of an object is very similar to using properties, in that you put the object’s variable name first, then a dot, and then the name of the method. 
Example:
`myArray.sort();`
> NOTE: As a general rule, anywhere you can use a function, you can use a method of an object.

## Primitives and objects
There are *String*, *Number*, and *Boolean* objects corresponding to the string, number, and boolean primitive data types.
Example:
```
var myString = new String("I'm a String object");
var lengthOfString = myString.length;
```

## String objects
### The `length` property
`document.write myString.length` - will return the length of the string assigned to `myString`

### The `indexOf()` and `lastIndexOf()` methods - finding a string inside another string
```
var myString = "Hello Jeremy. How are you Jeremy";

var foundAtPosition = myString.indexOf("Jeremy");
alert(foundAtPosition);
//this would return value of 6 because that is the position of the  first occurrence of "Jeremy"

foundAtPosition = myString.lastIndexOf("Jeremy");
alert(foundAtPosition);
//this would return value of 26  because that is first occurrence of "Jeremy" from the end of the string
```
> NOTE: JavaScript takes case sensitivity very seriously, both in its syntax and when making comparisons.

Example:
```
var myString = "Welcome to Wrox books. " + "The Wrox website is www.wrox.com. " + "Visit the Wrox website today. Thanks for buying Wrox";
var foundAtPosition = 0;
var wroxCount = 0;
while (foundAtPosition != -1) {
  foundAtPosition = myString.indexOf("Wrox", foundAtPosition);
  if (foundAtPosition != -1) {
    wroxCount++;
    foundAtPosition++;
    }
}
document.write("There are " + wroxCount + " occurrences of the word Wrox");
```

### The `substr()` and `substring()` methods
|Character position|0|1|2|3|4|5|6|7|8|9|
|------------------|-|-|-|-|-|-|-|-|-|-|
|Character         |J|a|v|a|S|c|r|i|p|t|
`substring()` - the method substring() accepts two parameters: the character start position and the position after the last character desired in the substring (*optional*)
`substr()` - takes two parameters, the  first being the start position of the first character you want included in your substring, the second - the length of the string of characters that you want to cut out of the longer string (*optional*)
```
var myString = "JavaScript";
var mySubString = myString.substr(0,4);
alert(mySubString);
```

### Uppercase and lowercase methods
`.toUpperCase()` - converts string to uppercase
`.toLowerCase()` - converts string to lowercase

### `charAt()` and `charCodeAt()` methods - selecting a single character
For example, to  find the last character in a string, you could use this code:
```
var myString = prompt("Enter some text", "Hello World!");
var theLastChar = myString.charAt(myString.length - 1);
document.write("The last character is " + theLastChar);
```
The `charCodeAt()` method is similar in use to the `charAt()` method, but instead of returning the character itself, it returns a number that represents the decimal character code for that character in the *Unicode character set*.

Example of checking whether the character is uppercase, lowercase, numeric or other:
```
function checkCharType(charToCheck) {
  var returnValue = "O";
  var charCode = charToCheck.charCodeAt(0);
  if (charCode >= "A".charCodeAt(0) && charCode <= "Z".charCodeAt(0)) {
    returnValue = "U";
  } else if (charCode >= "a".charCodeAt(0) && "z".charCodeAt(0)) {
    returnValue = "L";
  } else if (charCode >= "0".charCodeAt(0) && "9".charCodeAt(0)) {
    returnValue = "N";
  }
  return returnValue;
}
var myString = prompt("Enter some text", "Hello World");
switch (checkCharType(myString)) {
  case "U":
    document.write("First character was upper case");
    break;
  case "L":
    document.write("First character was lower case");
    break;
  case "N":
    document.write("First character was a number");
    break;
  default:
    document.write("First character was not a character or a number");
}
```

### The `fromCharCode()` method - converting character codes to a string
`var myString = String.fromCharCode(65,66,67);` - following line puts the string "ABC" into the variable myString

### The `trim()` method - removing leading and trailing whitespace
```
var name = prompt("Please enter your name");
name = name.trim(); //returns a new string with all leading (the start) and trailing (the end) whitespace removed
```
----------
## Array objects
### The `length` property
You can use the length property to  nd the index of the last element in the array.
```
var names = [];
names[0] = "Paul";
names[1] = "Jeremy";
names[11] = "Nick";
document.write("The last name is " + names[names.length - 1]);
```

### The `push` method
Simply pass the value you want to add to the array, and that value will be pushed to the end of the array, without needing to specify an index.
```
var names = [];
names.push("Jeremy");
names.push("Paul");
```

### The `concat` method - joining arrays
```
var names = [ "Paul", "Jeremy", "Nick" ];
var ages = [ 31, 30, 31 ];
var concatArray = names.concat(ages);
```
* Names array

|Element index|0|1|2|
|-------------|-|-|-|
|Value|Paul|Jeremy|Nick|

* Ages array

|Element index|0|1|2|
|-------------|-|-|-|
|Value|31|30|31|

* Concatenated

|Element index|0|1|2|3|4|5|
|-------------|-|-|-|-|-|-|
|Value|Paul|Jeremy|Nick|31|30|31|

### The `slice()` method - copying part of an array
The `slice()` method has two parameters:
* The index of the first element you want copied
* The index of the element marking the end of the portion you are slicing out (optional)

|Index|0|1|2|3|4|
|-----|-|-|-|-|-|
|Value|Paul|Sarah|Jeremy|Adam|Bob|
```
var names = [ "Paul", "Sarah", "Jeremy", "Adam", "Bob" ];
var slicedArray = names.slice(1,3);
```
|Index|0|1|
|-----|-|-|
|Value|Sarah|Jeremy|

### The `join()` method - converting an array into a single string
The `join()` method concatenates all the elements in an array and returns them as a string. It also enables you to specify any characters you want to insert between elements as they are joined together. The method has only *one parameter*, and that’s the string you want between elements.
```
var myShopping = [ "Eggs", "Milk", "Potatoes", "Cereal", "Banana" ];
var myShoppingList = myShopping.join("<br />");
//Now the variable myShoppingList will hold the following text: "Eggs<br />Milk<br />Potatoes<br />Cereal<br />Banana"
```

### The `sort()` method - putting your array in order
```
var names = [ "Paul", "Sarah", "Jeremy", "Adam", "Bob" ];
names.sort();
document.write("Now the names again in order <br />");
for (var index = 0; index < names.length; index++) {
document.write(names[index] + "<br />");
}
```
> NOTE: Don’t forget that the sorting is case sensitive, so Paul will come before paul. Remember that JavaScript stores letters encoded in their equivalent Unicode number, and that sorting is done based on Unicode numbers rather than actual letters. It just happens that Unicode numbers match the order in the alphabet.

### The `reverse()` method - putting your array into reverse order
Reverses the order of the array so that the elements at the back are moved to the front.

### The `indexOf()` and `lastIndexOf()` methods - finding array elements
```
var colors = [ "red", "blue", "green", "blue" ];
alert(colors.indexOf("red"));       //alerts "0"
alert(colors.lastIndexOf("blue"));  //alerts "3"
```

### Iterating through an array without loops
Methods execute a function that you define on every element while they iterate through the array.
```
function functionName(value, index, array) {
  // do something here
}
```
When executed, JavaScript passes three arguments to your function. The first is the value of the element, the second is the index of the element, and the third is the array itself.

#### The `every()`, `some()`, and `filter()` methods - testing each element
The `every()` method tests whether all elements in the array pass the test in your function.
```
var numbers = [ 1, 2, 3, 4, 5 ];
function isLessThan3(value, index, array) {
  var returnValue = false;
  if (value < 3) { returnValue = true;
  }
  return returnValue;
}
alert(numbers.every(isLessThan3));
//returns false because not every value in the array is less than 3, the result of the every() test is false

alert(numbers.some(isLessThan3));
//returns true because some of the elements in the array are less than 3.
```
The `every()` method returns `true` if, and only if, all elements in the array pass the test in your function; the `some()` method returns `true` if, and only if, some of the elements in the array pass your function’s test.

The `filter()` method executes your function on every element in the array, and if your function returns `true` for a particular element, that element is added to a new array that the `filter()` method returns.
```
var numbers = [ 1, 2, 3, 4, 5 ];
function isLessThan3(value, index, array) {
  var returnValue = false;
  if (value < 3) {
    returnValue = true;
  }
  return returnValue;
}
if (numbers.some(isLessThan3)) {
  var result = numbers.filter(isLessThan3);
  alert("These numbers are less than 3: " + result);
}
```

#### The `forEach()` and `map()` methods - operating on elements
```
var numbers = [ 1, 2, 3, 4, 5 ];
function doubleAndAlert(value, index, array) {
  var result = value * 2;
  alert(result);
}
numbers.forEach(doubleAndAlert);
```

The premise of the `map()` method is similar to that of `forEach()`. It executes a given function on every element in an array, but it also returns a new array that contains the results of the function.
```
var numbers = [ 1, 2, 3, 4, 5 ];
function doubleAndReturn(value, index, array) {
  var result = value * 2;
  return result;
}
var doubledNumbers = numbers.map(doubleAndReturn);
alert("The doubled numbers are: " + doubledNumbers);
```
> NOTE: the `map()` method does not alter the original array

-------
## The Math object
### The `abs()` method
Returns the absolute value of the number passed as its parameter.
`Math.abs(myNumber)`

### The `min()` and `max()` methods
`Math.max(21,22); //result is 22`
`Math.min(30.1,30.1); //result is 30.1`

### Rounding numbers

#### The `ceil()` method
The `ceil()` method always rounds a number up to the next largest whole number or integer. So 10.01 becomes 11, and –9.99 becomes –9 (because –9 is greater than –10). The `ceil()` method has just one parameter, namely the number you want rounded up.

#### The `floor()` method
Like the `ceil()` method, the `floor()` method removes any numbers after the decimal point, and returns a whole number or integer. The difference is that `floor()` always rounds the number down. 

#### The `round()` method
The `round()` method is very similar to `ceil()` and `floor()`, except that instead of always rounding up or always rounding down, it rounds up only if the decimal part is .5 or greater, and rounds down otherwise

|Parameter|`parseInt`|`ceil`|`floor`|`round`|
|:-------:|:--------:|:----:|:-----:|:-----:|
|10.25    |10        |11    |10     |10     |
|10.75    |10        |11    |10     |11     |
|10.5     |10        |11    |10     |11     |

### The `random()` method
The `random()` method returns a random floating‐point number in the range between 0 and 1, where 0 is included and 1 is not.
```
var diceThrow;
for (var throwCount = 0; throwCount < 10; throwCount++) {
  diceThrow = (Math.floor(Math.random() * 6) + 1);  //from 1 to 6
  document.write(diceThrow + "<br>");
}
```
```
function randomRange(myMin, myMax) {
  return Math.floor(Math.random() * (myMax - myMin +1)) + myMin;
}
```

### The `pow()` method
`Math.pow(2,8)` = $2^8$ = 256

-------
## Number objects
`var myNumber = new Number(123);` - to create a number object

### The `toFixed()` method
The `toFixed()` method cuts a number off after a certain point.
`itemCostAfterTax = itemCostAfterTax.toFixed(2);` - two decimal places by rounding up/down

-------
## Date objects
### Creating a date object
`var theDate1 = new Date();` - can be defined by passing the number of milliseconds since January 1, 1970, 00:00:00 GMT, this is how JavaScript stores date
`var theDate2 = new Date("31 January 2014");`
`var theDate3 = new Date(2014,0,31,15,35,20,20);` - year, month, day, hours, minutes, seconds, milliseconds

### Getting date values
|Method|Returns|
|------|-------|
|`getDate()`|The day of the month|
|`getDay()`|The day of the week as an integer, with Sunday as 0, Monday as 1, an so on|
|`getMonth()`|The month as an integer, with January as 0, February - 1, an so on|
|`getFullYear()`|The year as a four digit number|
|`toDateString()`|Returns the full date based on the current time zone as a human-readable string, e.g. "Wed 31 Dec 2003"|
Example:
`theMonth = myDateObject.getMonth();`

### Setting date values
|Method|Description|
|------|-----------|
|`setDate()`|The date of the month is passed in as the parameter to set the date|
|`setMonth()`|The month of the year is passed in as an integer parameter, where 0 is January, 1 - February, and so on|
|`setFullYear()`|This sets the year to the four-digit integer number passed in as a parameter|
> NOTE: After the year, date, and month have been de ned, the day is automatically set for you.

### Calculations and dates
```
var nowDate = new Date();
var currentDay = nowDate.getDate(); //current day is assigned
nowDate.setDate(currentDay + 28);   //28 days from now
```

### Getting time values
|Method|Description|
|------|-----------|
|`getHours()`|Returns hours|
|`getMinutes()`|Returns minutes|
|`getSeconds()`|Returns seconds|
|`getMilliseconds()`|Returns milliseconds|
|`toTimeString()`|Returns full time of the specified `Date` object|

### Setting time values
|Method|
|------|
|`setHours()`|
|`setMinutes()`|
|`setSeconds()`|
|`setMilliseconds()`|
```
var nowDate = new Date();
nowDate.setHours(9);
nowDate.setMinutes(57);
alert(nowDate);
nowDate.setMinutes(64);
alert(nowDate);
```
---------
## Creating your own custom objects
`var johnDoe = new Object();` - creates a new object
`var johnDoe = {};` - shortcut for creating a new object

### Assigning properties to an object
Simply use the name of the object, followed by a dot, then the name of the property, and assign it a value.
```
johnDoe.firstName = "John";
johnDoe.lastName = "Doe";
```

### Assigning methods to an object
```
johnDoe.greet = function() {
  alert("My name is " + this.firstName + " " + this.lastName);
};
johnDoe.greet();
```
> NOTE: First, notice there is no name between `function` and `()`. A function that has no name is called an *anonymous function*. Anonymous functions, in and of themselves, are a syntax error unless you assign that function to a variable.
Next, notice the use of `this` inside of the function: `this.firstName` and `this.lastName`. In JavaScript, this is a special variable that refers to the current object — the `johnDoe` object in this case. It literally means “this object.”

### Object literals
```
var johnDoe = {
  firstName : "John",
  lastName : "Doe",
  greet : function() {
    alert("My name is " + this.firstName + " " + this.lastName);
  }
};
```
> NOTE: In object literal notation, the *colon* sets the value of the property.

Example:
```
function createPerson(firstName, lastName) {
  return {
    firstName: firstName,
    lastName: lastName,
    getFullName: function() {
      return this.firstName + " " + this.lastName
    },
    greet: function(person) {
    alert("Hello, " + person.getFullName() +  ". I'm " + this.getFullName());
    }
  };
}
var johnDoe = createPerson("John", "Doe");
var janeDoe = createPerson("Jane", "Doe");
johnDoe.greet(janeDoe);
```
--------
## Creating new types of objects (reference types)
Reference types are essentially templates for an object.
Reference type consist of three things:
1. A constructor
2. Method definitions
3. Properties

### Defining a reference type
Constructor:
```
function Person(firstName, lastName) {
  this.firstName = firstName;   //not shared across instances
  this.lastName = lastName;     //not shared across instances
}
```
> NOTE: Typically, a reference type is defined with an uppercase letter. Doing so makes it easy to differentiate a function from a reference type easily and quickly.

Prototype:
```
Person.prototype.getFullName = function() {
  return this.firstName + " " + this.lastName;
};
Person.prototype.greet = function(person) {
  alert("Hello, " + person.getFullName() + ". I'm " + this.getFullName());
};
```
Every function object has a `prototype` property, but it is only useful for constructor functions. Any properties and methods you assign to Person.prototype are usable on all Person objects. In fact, they’re more than usable—they’re shared!
The function object of one `Person` object’s `getFullName` is the exact same function object on another `Person` object’s `getFullName`.
`var areSame = person1.getFullName == person2.getFullName; //true`

### Creating and using reference type instances
```
var johnDoe = new Person("John", "Doe");
var janeDoe = new Person("Jane", "Doe");
```
> NOTE: The use of the `new` keyword is very important when creating an object with a constructor. The browser does not throw an error if you do not use the `new` keyword, but your script will not work correctly. Instead of creating a new object, you actually add properties to the global `window` object. The problems caused by not using the `new` keyword can be hard to diagnose, so make sure you specify the `new` keyword when creating objects with a constructor.

`janeDoe.greet(johnDoe);` - even though `getFullName()` and `greet()` are defined on `Person.prototype`, you still call them like normal methods

> **! ! !** The main difference between reference type and plain, but custom objects is how the objects are created. Objects created from a constructor typically consume less of the computer’s memory than literal objects.
