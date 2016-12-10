#[JavaScript Objects in Detail](http://javascriptissexy.com/javascript-objects-in-detail/)

## Creating objects
### 1. Object Literals
```
// This is an empty object initialized using the object literal notation
var myBooks = {};

// This is an object with 4 items, again using object literal
var mango = {
  color: "yellow",
  shape: "round",
  sweetness: 8,
  
  howSweetAmI: function () {
    console.log("Hmm Hmm Good");
  }
}
```

### 2. Object Constructor
```
var mango =  new Object ();
mango.color = "yellow";
mango.shape= "round";
mango.sweetness = 8;

mango.howSweetAmI = function () {
  console.log("Hmm Hmm Good");
}
```
------
## Practical patterns for creating objects
### 1. Constructor pattern for creating objects
```
function Fruit (theColor, theSweetness, theFruitName, theNativeToLand) {

    this.color = theColor;
    this.sweetness = theSweetness;
    this.fruitName = theFruitName;
    this.nativeToLand = theNativeToLand;

    this.showName = function () {
        console.log("This is a " + this.fruitName);
    }

    this.nativeTo = function () {
    this.nativeToLand.forEach(function (eachCountry)  {
       console.log("Grown in:" + eachCountry);
        });
    }

}
```
With this pattern in place, it is very easy to create all sorts of fruits. Thus:
```
var mangoFruit = new Fruit ("Yellow", 8, "Mango", ["South America", "Central America", "West Africa"]);
mangoFruit.showName(); // This is a Mango.
mangoFruit.nativeTo();
// Grown in:South America
// Grown in:Central America
// Grown in:West Africa

var pineappleFruit = new Fruit ("Brown", 5, "Pineapple", ["United States"]);
pineappleFruit.showName(); // This is a Pineapple.
```

### 2. Prototype pattern for creating objects
```
function Fruit () {

}

Fruit.prototype.color = "Yellow";
Fruit.prototype.sweetness = 7;
Fruit.prototype.fruitName = "Generic Fruit";
Fruit.prototype.nativeToLand = "USA";

Fruit.prototype.showName = function () {
console.log("This is a " + this.fruitName);
}

Fruit.prototype.nativeTo = function () {
            console.log("Grown in:" + this.nativeToLand);
}
```
And this is how we call the Fruit () constructor in this prototype pattern:
```
var mangoFruit = new Fruit ();
mangoFruit.showName(); //
mangoFruit.nativeTo();
// This is a Generic Fruit
// Grown in:USA
```
------
## How to access properties on an object
### 1. Dot notation
```
// We have been using dot notation so far in the examples above, here is another example again:
var book = {title: "Ways to Go", pages: 280, bookMark1:"Page 20"};

// To access the properties of the book object with dot notation, you do this:
console.log ( book.title); // Ways to Go
console.log ( book.pages); // 280
```

### 2. Bracket notation
```
// To access the properties of the book object with bracket notation, you do this:
console.log ( book["title"]); //Ways to Go
console.log ( book["pages"]); // 280

//Or, in case you have the property name in a variable:
var bookTitle = "title";
console.log ( book[bookTitle]); // Ways to Go
console.log (book["bookMark" + 1]); // Page 20
```
------
## Own and inherited properties
Objects have inherited properties and own properties. The own properties are properties that were defined on the object, while the inherited properties were inherited from the object’s Prototype object.
To find out if a property exists on an object (either as an inherited or an own property), you use the `in` operator:
```
// Create a new school object with a property name schoolName
var school = {schoolName:"MIT"};

// Prints true because schoolName is an own property on the school object
console.log("schoolName" in school);  // true

// Prints false because we did not define a schoolType property on the school object, and neither did the object inherit a schoolType property from its prototype object Object.prototype.
console.log("schoolType" in school);  // false
 
// Prints true because the school object inherited the toString method from Object.prototype.
console.log("toString" in school);  // true
```
Example:
```
function Animal(name, numLegs) {
  this.name = name;
  this.numLegs = numLegs;
};

function Penguin(name) {
  this.name = name;
}
Penguin.prototype = new Animal(); //Penguin class inherits properties from Animal class
```
------
## `hasOwnProperty`
To find out if an object has a specific property as one of its own property, you use the `hasOwnProperty` method.
```
// Create a new school object with a property name schoolName
var school = {schoolName:"MIT"};

// Prints true because schoolName is an own property on the school object
console.log(school.hasOwnProperty ("schoolName"));  // true
 
// Prints false because the school object inherited the toString method from Object.prototype, therefore toString is not an own property of the school object.
console.log(school.hasOwnProperty ("toString"));  // false
```
------
### Accesing and enumerating properties on objects
```
// Create a new school object with 3 own properties: schoolName, schoolAccredited, and schoolLocation.
var school = {schoolName:"MIT", schoolAccredited: true, schoolLocation:"Massachusetts"};

//Use of the for/in loop to access the properties in the school object
for (var eachItem in school) {
console.log(eachItem); // Prints schoolName, schoolAccredited, schoolLocation
}
```
------
### Deleting properties of an object
```
var christmasList = {mike:"Book", jason:"sweater" }
delete christmasList.mike; // deletes the mike property
```
------
### Serialize and deserialize objects
`JSON.stringify(christmasList);` - stringify
`JSON.parse(christmasListStr);` - deserialize