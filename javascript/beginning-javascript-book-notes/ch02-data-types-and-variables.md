<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 2. Data Types and Variables

## Types of data
1. numerical = *floating-point numbers*
2. text = *string* (to be enclosed in quotation marks: " or ')
  * 'Peter O'Toole' will bring error => "Peter O'Toole" or 'Peter O\'Toole'
  * `\` - *escape character* that tells browser that the next character is not the end of the string, but part of the text
3. logic = *boolean* (true or false, yes or no)

## Escape sequences
| Escape sequences | Character represented |
|:-----------------|:----------------------|
|`\b`|Backspace|
|`\f`|Form feed|
|`\n`|New line|
|`\r`|Carriage return|
|`\t`|Tab|
|`\'`|Single quote|
|`\"`|Double quote|
|`\\`|Backslash|
|`\xNN`|NN is a hexadecimal number that identifies a character in the Latin-1 character set, e.g. `\xA9` stands for ©|
|`\uNNNN`|NN is a hexadecimal number that identifies a character in the Unicode character set, e.g. `\u00A9` stands for ©|

## Variables - storing data in memory
* Variable can be used to store temporary data that can be altered, or varied.
* Variables are case sensitive, e.g. `myVariable` is not the same as `myvariable`.
* Reserved variable names include: `var`, `with`, etc.
* Forbidden characters in variables' names: `&`, `%`.
* Names must not begin with numbers.

### Creating variables and giving them values
`var myFirstVariable;` - declare a new variable
`myFirstVariable = 101;` - assign value to a variable
`=` - *assignment operator*
`var myFirstVariable = 101;` - this is a shortcut called *initializing*
`var myFirstVariable = prompt("Enter any data")` - assign value through the prompt box

## Using data - calculations and basic string manipulation

### Calculations
`+ | - | * | /` - basic math operations
`++` - *increment* operator, increases value by one
`--` - *decrement* operator, decreases value by one
*  e.g. instead of `myVariable = myVariable + 1` you can use `myVariable++` or `++myVariable`, but:
  * `myNumber = myVariable++ * 10 + 1;` - when `++` is postfixed, it will be incremented afterward, i.e. multiply `myVariable` by 10 plus 1 and then increment `myVariable` by one, so if `myVariable = 1`, then: `1 * 10 + 1 + 1 = 12`.
  * `myNumber = ++myVariable * 10 + 1;` - when `++` is prefixed, `myVariable` will be incremented first, i.e. increment `myVariable` by one multiply `myVariable` by 10 plus 1, so if `myVariable = 1`, then: `(1 + 1) * 10 + 1 = 21`.
`+= | -= | *= | /=` - operator as a shortcut for increasing | subtracting | multiplying | dividing the value held by a variable by a set amount
* `myVar += 6;` does exactly the same thing as: `myVar = myVar + 6;`.
* `%` - "modulo", when placed between two numbers, the computer will divide the first number by the second, and then return the **remainder** of that division.

### String operations
`+` - process termed *concatenation* when used with strings

## Data type conversion functions
`parseInt()` - convert strings to an integers
`parseFloat()` - convert strings to floating-point numbers

### NaN - Not a Number
`isNan()` - checks whether something is NaN or not (if NaN => stores `true` value, if not NaN => stores `false` value)

## Arrays
Arrays similar to variables, but can hold **more than one** item/value by assigning an *index* value.

| Element Name | Value |
|:-------------|:------|
|`myArray[0]`|25|
|`myArray[1]`|35|

`var myArray = new Array();` - define array `myArray`
`var myArray = [];` - better way to create array `myArray`
=> `new Array()`= `[]`
Example: `var myArray = ["Paul", 345, "John", 112, "Bob", 99];` is similar to:
```
var myArray = [];
myArray [0] = "Paul";
myArray [1] = 345;
...
myArray [5] = 99;
```

### Multi-dimensional arrays
|INDEX|0|1|2|
|---|---|---|---|
|0|Name1|Name2|Name3|
|1|Age1|Age2|Age3|
|2|Address1|Address2|Address3|

```
var personnel = [];

personnel[0] = [];
personnel[0][0] = "Name0";
personnel[0][1] = "Age0";
personnel[0][2] = "Address0";

personnel[1] = [];
personnel[1][0] = "Name1";
personnel[1][1] = "Age1";
personnel[1][2] = "Address1";
```
