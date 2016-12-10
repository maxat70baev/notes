<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 6. String manipulation

## Additional string methods
### The `split()` method
The String object’s `split()` method splits a single string into an array of substrings.
```
var myString = "A,B,C";
var myTextArray = myString.split(,); //will split string between commas into separate arrays
```

### The `replace()` method
The `replace()` method searches a string for occurrences of a substring. Where it finds a match for this substring, it replaces the substring with a third string that you specify.
```
var myString = "The event will be in May, the 21st of June";
var myCleanedUpString = myString.replace("May", "June");
//"The event will be in June, the 21st of June"
```

### The `search()` method
The `search()` method enables you to search a string for a particular piece of text. If the text is found, the character position at which it was found is returned; otherwise, ‐1 is returned. The method takes only one parameter, namely the text you want to search for.
```
var myString = "Beginning JavaScript, Beginning Java, " + "Professional JavaScript";
alert(myString.search("Java")); //will show the value 10, which is the character position of the J in the first occurrence of Java, as part of the word JavaScript
```

### The `match()` method
The match() method is very similar to the search() method, except that instead of returning the position at which a match was found, it returns an array. Each element of the array contains the text of each match that is found.
```
var myString = "1997, 1998, 1999, 2000, 2001, 2002";
myMatchArray = myString.match("2000")
alert(myMatchArray.length);
```

------
## Regular expressions
Regular expressions in JavaScript are used through the `RegExp` object, which is a native JavaScript object, as are `String`, `Array`, and so on.
Two ways to create a new `RegExp` object:
1. `var myRegExp = /\b'|'\b/;` - the forward slashes (`/`) mark the start and end of the regular expression
2. `var myRegExp = new RegExp("\\b'|'\\b");`

### Simple Regular Expressions
```
var myString = "Paul, Paula, Pauline, paul, Paul";
var myRegExp = /Paul/;
myString = myString.replace(myRegExp, "Ringo");
alert(myString);
//Result is "Ringo, Paula, Pauline, paul, Paul"
```
> NOTE: By default, the `RegExp` object looks only for the  first matching pattern, in this case the  first `Paul`, and then stops. This is a common and important behavior for `RegExp` objects. Regular expressions tend to start at one end of a string and look through the characters until the  first complete match is found, then stop.

|Attribute character|Description|
|-------------------|-----------|
|`G`|**Global match**. This looks for all matches of the pattern rather than stopping after the first match is found.|
|`I`|**Pattern is case-insensitive**. For example, `Paul` and `paul` are considered the same pattern of characters.|
|`M`|**Multi-line flag**. This specifies that the special characters `^` and `$` can match the beginning and the end of the lines as well as the beginning and end of the string.|

Example:
```
var myRegExp = /Paul/gi; //global, case-insensitive
var myString = "Paul, Paula, Pauline, paul, Paul";
myString = myString.replace(myRegExp, "Ringo");
alert(myString);
//Result is "Ringo, Ringoa, Ringoine, Ringo, Ringo"
```

### Regular Expressions: special characters
#### Text, numbers, and punctuation
|CHARACTER CLASS|CHARACTER IT MATCHES|EXAMPLE|
|---------------|--------------------|-------|
|`\d`|Any digit from 0 to 9|`\d\d` matches 72, but not aa or 7a.|
|`\D`|Any character that is no a digit|`\D\D\D` matches abc, but not 123 or 8ef.|
|`\w`|Any word character; that is, A-Z, a-z, 0-9, and the underscore character (_)|`\w\w\w\w` matches Ab12, but not #$%* or Ab3@.|
|`\W`|Any non‐word character|`\W` matches @, but not a.|
|`\s`|Any whitespace character|`\s` matches tab, return, formfeed, and vertical tab.|
|`\S`|Any non‐whitespace character|`\S` matches A, but not the tab character.|
|`.`|Any single character other than the newline character (`\n`)|`.` matches a or 4 or @.|
|`[...]`|Any one of the characters between the brackets`[a‐z]` matches any character in the range a to z|`[abc]` matches a or b or c, but nothing else.|
|`[^...]`|Any one character, but not one of those inside the brackets|`[^abc]` matches any character except a or b or c. `[^a‐z]` matches any character that is not in the range a to z.|

Example: To match a telephone number in the format 1‐800‐888‐5474, the regular expression would be as follows: `\d-\d\d\d-\d\d\d-\d\d\d\d`

```
var input = prompt("Please enter a pass phrase.", "");
function isValid (text) {
  var myRegExp = /[^a-z\d ]/i;
  return !(myRegExp.test(text));
}
if (isValid(input)) {
  alert("Your passphrase contains only valid characters");
} else {
  alert("Your passphrase contains one or more invalid characters");
}
```
IS THE SAME AS:
```
function isValid2(text) {
  var returnValue = true;
  var validChars = "abcdefghijklmnopqrstuvwxyz1234567890 ";
  for (var charIndex = 0; charIndex < text.length;charIndex++) {
    if (validChars.indexOf(text.charAt(charIndex).toLowerCase()) < 0) {
      returnValue = false;
      break;
    }
  }
  return returnValue;
}
```

#### Repetition characters
|SPECIAL CHARACTER|MEANING|EXAMPLE|
|-----------------|-------|-------|
|`{n}`|Match n of the previous item.|`x{2}` matches `xx`.|
|`{n,}`|Match n or more of the previous item.|`x{2,}` matches xx, xxx, xxxx, xxxxx, and so on.|
|`{n,m}`|Match at least n and at most m of the previous item.|`x{2,4}` matches xx, xxx, and xxxx.|
|`?`|Match the previous item zero or one time.|`x?` matches nothing or x.|
|`+`|Match the previous item one or more times.|`x+` matches x, xx, xxx, xxxx, xxxxx, and so on.|
|`*`|Match the previous item zero or more times.|`x*` matches nothing, or x, xx, xxx, xxxx, and so on.|

Example: To match a telephone number in the format 1‐800‐888‐5474, the regular expression would be: `var myRegExp = /\d-\d{3}-\d{3}-\d{4}/`

#### Position characters
|POSITION CHARACTER|DESCRIPTION|
|------------------|-----------|
|`^`|The pattern must be at the start of the string, or if it’s a multi‐line string, then at the beginning of a line. For multi‐line text (a string that contains carriage returns), you need to set the multi‐line flag when defining the regular expression using `/myreg ex/m`. Note that this is only applicable to IE 5.5 and later and NN 6 and later.|
|`$`|The pattern must be at the end of the string, or if it’s a multi‐line string, then at the end of a line. For multi‐line text (a string that contains carriage returns), you need to set the multi‐line flag when defining the regular expression using `/myreg ex/m`. Note that this is only applicable to IE 5.5 and later and NN 6 and later.|
|`\b`|This matches a word boundary, which is essentially the point between a word character and a non‐word character.|
|`\B`|This matches a position that’s not a word boundary.|

Examples:
* To make sure your pattern was at the start of a line, you would type the following: `^myPattern`
* To match the same pattern, but at the end of a line, you would type the following: `myPattern$`
* Word boundaries (`\b` indicated by |):
  * |Hello||world|!,|let|'|s||look||at||boundaries||said||007|.
* Non-word boundaries (`\B` indicated by |):
  * H|e|l|l|o w|o|r|l|d!|,| l|e|t's l|o|o|k a|t| b|o|u|n|d|a|r|i|e|s s|a|i|d 0|0|7.|

```
var myString = "Paul, Paula, Pauline, paul, Paul, JeanPaul";
var myRegExp = /\bPaul\b/gi;
myString = myString.replace(myRegExp, "Ringo");
//Ringo, Paula, Pauline, Ringo, Ringo, JeanPaul => only Paul or paul will ever be matched
```

### Grouping Regular Expressions
If you want a number of expressions to be treated as a single group, you just enclose them in parentheses, for example, `/(\d\d)/`.
By grouping characters into patterns, you can use the special repetition characters to apply to the whole group of characters, rather than just one.

To match both `JavaScript` and `VBScript` using the same regular expression:
`var myRegExp = /\b(VB)?(Java)?Script\b/gi;`
1. A word boundary: `\b`
2. Zero or one instance of VB: `(VB)?`
3. Zero or one instance of Java: `(Java)?`
4. The characters Script: `Script`
5. A word boundary: `\b`

> NOTE: If you look back at the special repetition characters table, you’ll see that they apply to the item preceding them. This can be a character, or, where they have been grouped by means of parentheses, the previous group of characters.

`\b(VB|Java)Script\b` - avoid matching `VBJavaScript` by using `|` special character that is similar to OR operator

### Reusing group of characters
```
var myString = "007,007,001,002,002,003,002,004";
var myRegExp = /(\d+),\1/g;
myString = myString.replace(myRegExp, "ERROR"); alert(myString);
```
`\d` - specifies any digit character
`\d+` - means one or more of the previous character
`\1` - match the characters found in the first group defined using parentheses

------
## The string object
### The `split()` method
```
var myListString = "apple, 0.99, banana, 0.50, peach, 0.25, orange, 0.75";
var theRegExp = /[^a-z]+/i;
var myFruitArray = myListString.split(theRegExp); //retrieve only the names of the fruit and not the prices
```
After the split, the variable `myFruitArray` will contain an Array with each element containing the fruit name, as shown here:

|ARRAY ELEMENT INDEX|0|1|2|3|
|-------------|-----|------|-----|------|
|Element value|apple|banana|peach|orange|

### The `replace()` method
Each group in a regular expression is given a number from 1 to 99; any groups greater than 99 are not accessible.
To refer to a group, you write `$` followed by the group’s position.
```
var myString = "2012, 2013, 2014";
var myRegExp = /(\d{4})/g; //grouped pattern containing 4 digits
myString = myString.replace(myRegExp, "the year $1");
//result: "the year 2012, the year 2013, the year 2014"
```

### The `search()` method
The `search()` method enables you to search a string for a pattern of characters. If the pattern is found, the character position at which it was found is returned; otherwise, ‐1 is returned. The method takes only one parameter, the `RegExp` object you have created.
```
var myString = "Beginning JavaScript, Beginning Java 2, " + "Professional JavaScript";
var myRegExp = /\bJava\b/i;
alert(myString.search(myRegExp)); //output - 32, i.e. the position at which the search has located the pattern
```
> NOTE: With the search() method, the g for global is not relevant, and its use has no effect.

### The `match()` method
The match() method is very similar to the search() method, except that instead of returning the position at which a match was found, it returns an array. Each element of the array contains the text of a match made.

------
## Using the `RegExp` object's constructor
`var myRegExp = /[a-z]/;` - create `RegExp` object using the `/` and `/` characters
`var myRegExp = new RegExp("[a-z]");` - `RegExp()` constructor function
> NOTE: A very important difference when you are using this method is in how you use special regular expression characters, such as `\b`, that have a backward slash in front of them. The problem is that the backward slash indicates an escape character in JavaScript strings — for example, you may use `\b`, which means a backspace. To differentiate between `\b` meaning a backspace in a string and the `\b` special character in a regular expression, you have to put another backward slash in front of the regular expression special character. So `\b` becomes `\\b` when you mean the regular expression `\b` that matches a word boundary, rather than a backspace character.

`var myRegExp = new RegExp("hello\\b","mgi");` - add (as an optional second parameter) the special flags `m`, `g`, `i` to indicate the pattern matching should be multi‐line, global, or case‐insensitive, respectively
