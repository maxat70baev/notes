<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 9. DOM Scripting
DOM scripting is the manipulation of an HTML page after it’s loaded into the browser.
## The core DOM objects
|OBJECT|DESCRIPTION|
|------|-----------|
|`Node`|Each node in the document has its own Node object.|
|`NodeList`|This is a list of Node objects.|
|`NamedNodeMap`|This provides access by name rather than by index to all the Node objects.|

## High-Level DOM objects
|OBJECT|DESCRIPTION|
|------|-----------|
|`Document`|The root node of the document|
|`DocumentType`|The DTD or schema type of the XML document|
|`DocumentFragment`|A temporary storage space for parts of the document|
|`EntityReference`|A reference to an entity in the XML document|
|`Element`|An element in the document|
|`Attr`|An attribute of an element in the document|
|`ProcessingInstruction`|A processing instruction|
|`Comment`|A comment in an XML document or HTML document|
|`Text`|Text that must form a child node of an element|
|`CDATASection`|A CDATA section within the XML document|
|`Entity`|An unparsed entity in the DTD|
|`Notation`|A notation declared within a DTD|

## DOM objects and their properties and methods
|METHODS OF THE DOCUMENT OBJECT|DESCRIPTION|
|------------------------------|-----------|
|`getElementById(idValue)`|Returns a reference (a node) of an element, when supplied with the value of the id attribute of that element|
|`getElementsByTagName(tagName)`|Returns a reference (a node list) to a set of elements that have the same tag as the one supplied in the argument|
|`querySelector(cssSelector)`|Returns a reference (a node) of the first element that matches the given CSS selector|
|`querySelectorAll(cssSelector)`|Returns a reference (a node list) to a set of elements that match the given CSS selector|

Example of `getElementById(idValue)`:
```
<h1 id="heading1">My Heading</h1>
<p id="paragraph1">This is some text in a paragraph.</p>
<script>
  var h1Element = document.getElementById("heading1"); //returns a reference
  h1Element.style.color = "red";
</script>
```
Example of `getElementsByTagName(tagName)`:
```
var tdElements = document.getElementsByTagName("td");
var length = tdElements.length;
for (var i = 0; i < length; i++) {
  tdElements[i].style.color = "red";
}
```
Example of `querySelector(cssSelector)`:
```
<p class="sub-title">This is a <span>special</span> paragraph element that contains <span>some text</span></p>.
<script>
  var firstSpan = document.querySelector(".sub-title span"); //retrieve first <span/>
  firstSpan.style.color = "red";
</script>
```
Example of `querySelectorAll(cssSelector)`:
```
var spans = document.querySelectorAll(".sub-title span"); //retrieve all spans
```

## Creating elements and text
|METHODS OF THE DOCUMENT OBJECT|DESCRIPTION|
|------------------------------|-----------|
|`createElement(elementName)`|Creates an element node with the speci ed tag name. Returns the created element|
|`createTextNode(text)`|Creates and returns a text node with the supplied text|

```
var pElement = document.createElement("p");
var text = document.createTextNode("This is some text.");
```

|PROPERTY OF THE DOCUMENT OBJECT|DESCRIPTION|
|`documentElement`|Returns a reference to the outermost element of the document (the root element; for example, `<html/>`)|

`var container = document.documentElement;` - the variable container now contains the root element, which is `<html/>`

## The Element object
|MEMBER NAME|DESCRIPTION|
|-----------|-----------|
|`tagName`|Gets the element's tag name|
|`getAttribute()`|Gets the value of an attribute|
|`setAttribute()`|Sets an attribute with a specified value|
|`removeAttribute()`|Removes a specific attribute and its value from the element|

```
<p id="paragraph1">This is some text.</p>
<script>
  var pElement = document.getElementById("paragraph1");
  pElement.setAttribute("align", "center");
  alert(pElement.getAttribute("align"));
  pElement.removeAttribute("align");
</script>
```

## The Node object
### Navigating the DOM
|PROPERTIES OF THE NODE OBJECT|DESCRIPTION|
|-----------------------------|-----------|
|`firstChild`|Returns the first child node of an element|
|`lastChild`|Returns the last child node of an element|
|`previousSibling`|Returns the previous child node of an element at the same level as the current child node|
|`nextSibling`|Returns the next child node of an element at the same level as the current child node|
|`ownerDocument`|Returns the root node of the document that contains the node (note this is not available in IE 5 or 5.5)|
|`parentNode`|Returns the element that contains the current node in the tree structure|
|`nodeName`|Returns the name of the node|
|`nodeType`|Returns the type of the node as a number|
|`nodeValue`|Gets or sets the value of the node in plaintext format|

```
<h1 id="heading1">My Heading</h1>
<p id="paragraph1">This is some text in a paragraph</p>
<script>
  var htmlElement; // htmlElement stores reference to <html>
  var headElement; // headingElement stores reference to <head>
  var bodyElement; // bodyElement stores reference to <body>
  var h1Element; // h1Element stores reference to <h1>
  var pElement; // pElement stores reference to <p>
  
  htmlElement = document.documentElement;
  headElement = htmlElement.firstChild;
  
  alert(headElement.tagName);
  
  if (headElement.nextSibling.nodeType == 3) {
    bodyElement = headElement.nextSibling.nextSibling;
  } else {
    bodyElement = headElement.nextSibling;
  }
  
  alert(bodyElement.tagName);
  
  if (bodyElement.firstChild.nodeType == 3) {
    h1Element = bodyElement.firstChild.nextSibling;
  } else {
    h1Element = bodyElement.firstChild;
  }
  
  alert(h1Element.tagName);
  h1Element.style.fontFamily = "Arial";
  
  if (h1Element.nextSibling.nodeType == 3) {
    pElement = h1Element.nextSibling.nextSibling;
  } else {
    pElement = h1Element.nextSibling;
  }
  
  alert(pElement.tagName);
  pElement.style.fontFamily = "Arial";
  
  if (pElement.previousSibling.nodeType == 3) {
    h1Element = pElement.previousSibling.previousSibling;
  } else {
    h1Element = pElement.previousSibling;
  }
  
  h1Element.style.fontFamily = "Courier";
</script>
```

### Methods of the DOM object
|METHODS OF NODE OBJECTS|DESCRIPTION|
|-----------------------|-----------|
|`appendChild(newNode)`|Adds a new `Node` object to the end of the list of child nodes. This method returns the appended node.|
|`cloneNode(cloneChildren)`|Returns a duplicate of the current node. It accepts a boolean value. If the value is `true`, the method clones the current node and all child nodes. If the value is `false`, only the current node is cloned and child nodes are left out of the clone.|
|`hasChildNodes()`|Returns `true` if a node has any child nodes and `false` if not|
|`insertBefore(newNode,referenceNode)`|Inserts a new Node object into the list of child nodes before the node stipulated by `referenceNode`. Returns the inserted node|
|`removeChild(childNode)`|Removes a child node from a list of child nodes of the `Node` object. Returns the removed node|

```
<script>
  var newText = document.createTextNode("My Heading");
  var newElem = document.createElement("h1");
  
  newElem.appendChild(newText);
  document.body.appendChild(newElem);
  
  newText = document.createTextNode("This is some text in a paragraph");
  newElem = document.createElement("p");
  
  newElem.appendChild(newText);
  document.body.appendChild(newElem);
</script>
```

## Changing appearances
### Using the style property
```
var divAdvert = document.getElementById("divAdvert");
divAdvert.style.color = "blue";
divAdvert.style.background-color = "gray"; // wrong
divAdvert.style.backgroundColor = "gray"; // correct
```

### Changing the class attribute
```
<style>
  #divAdvert {
    font: 12pt arial;
  }
  .new-style {
    font-style: italic;
    text-decoration: underline;
  }
</style>
<body>
  <div id="divAdvert">
    Here is an advertisement.
  </div>
  <script>
    var divAdvert = document.getElementById("divAdvert");
    divAdvert.className = "new-style";
  </script>
</body>
```
> NOTE: The HTML class attribute, and thus the `className` property, can contain multiple CSS class names.

## Positioning and moving content
```
var divAdvert = document.getElementById("divAdvert");
divAdvert.style.position = "absolute";
divAdvert.style.left = "100px"; // set the left position
divAdvert.style.top = "100px"; // set the right position
```

## Animation
The DOM in modern browsers exposes the `offsetTop` and `offsetLeft` properties of an HTML element object. These two properties return the calculated position relative to the element’s parent element: `offsetTop` tells you the top location, and `offsetLeft` tells you the left position. The values returned by these properties are numerical values, so you can easily check to see where your element currently is in the animation. For example:
```
var endPointX = 394;
if (element.offsetLeft < endPointX) {
  // continue animation
}
```

### Performing animation
```
<head>
  <style>  
    #divAdvert {
      position: absolute;
      font: 12px Arial;
      top: 4px;
      left: 0px;
    } 
  </style>
</head>
<body>
  <div id="divAdvert">
  Here is an advertisement.
  </div>
  <script>
    var switchDirection = false;
    function doAnimation() {
      var divAdvert = document.getElementById("divAdvert");
      var currentLeft = divAdvert.offsetLeft;
      var newLocation;
      if (!switchDirection) {
        newLocation = currentLeft + 2;
        if (currentLeft >= 400) {
          switchDirection = true;
        }
      } else {
        newLocation = currentLeft - 2;
        if (currentLeft <= 0) {
          switchDirection = false;
        }
      }
      divAdvert.style.left = newLocation + "px";
    }
    setInterval(doAnimation, 10);
  </script>
```
