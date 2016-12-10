<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 8. Programming the browser
BOM - browser object model

![](resources/AAB2517E4D137486D2779D7ADBBE9D99.jpg)

## The `window` object
The `window` object represents the browser’s frame or window, in which your web page is contained. To some extent, it also represents the browser itself and includes a number of properties that are there simply because they don’t fit anywhere else.
`alert("Hello!");` is the same as `window.alert("Hello!");` since `window` object is a *global object*.

> NOTE: Within a web page, you shouldn’t use names for your functions or variables that conflict with names of BOM objects or their properties and methods, because any function or variable you define within the global scope actually gets appended to the `window` object.

## The `history` object
`history.back()`/`history.forward()` - back and forward to revisit pages
`history.go(-2)` - to return the user to the page before previous page
=> `go(-1)` and `back()` are equivalent

## The `location` object
`location.replace("myPage.html");` - navigate to another page: removes the current page from the history stack and replaces it with the new page, i.e. cannot go back in history
`location.href = "myPage.html";` - navigate to another page: adds it to the history of pages navigated to

## The `navigator` object
`Navigator` object contains lots of information about the browser and the operating system in which it’s running.

### The `geolocation` object
`geolocation` property to `navigator` - to enable developers to obtain and use the position of the device or computer.
```
function geoSuccess(position) {
  var crds = position.coords; //reduces the amount of code and download time
  var latitude = crds.latitude;
  var longitude = crds.longitude;
  var altitude = crds.altitude;
  var speed = crds.speed;
  var message = "You're at " + latitude + ", " + longitude
  alert(message);
}
function geoError(errorObj) {
  alert(errorObj.message);
}
navigator.geolocation.getCurrentPosition(geoSuccess, geoError);
```
|VALUE|DESCRIPTION|
|-----|-----------|
|1|Failure occurred because the page did not have permission to acquire the position of the device/computer.|
|2|An internal error occurred.|
|3|The time allowed to retrieve the device’s/computer’s position was reached before the position was obtained.|

## The `screen` object
The `screen` object property of the `window` object contains a lot of information about the display capabilities of the client machine. Its properties include the `height` and `width` properties, which indicate the vertical and horizontal range of the screen, respectively, in pixels.
Another property of the `screen` object, which you use in an example later, is the `colorDepth` property. This tells you the number of bits used for colors on the client’s screen.

## The `document` object
Via `document` object you can gain access to the HTML elements, their properties, and their methods inside your page.

### The images collection
Each of the `img` objects in a page is stored in the images collection, which is a property of the `document` object.
You use this, and other collections, as you would an array. The first image on
the page is found in the element `document.images[0]`, the second in `document.images[1]`, and so on.
`var myImage2 = document.images[1];` - assigns a reference to the `img` object

```
<img src="" width="200" height="150" alt="My Image" /> //src left blank: at the same folder
<script>
  var myImages = [ 
    "usa.gif",
    "canada.gif",
    "jamaica.gif",
    "mexico.gif"
  ];
  var imgIndex = prompt("Enter a number from 0 to 3", "");
  document.images[0].src = myImages[imgIndex];
</script>
```

### The links collection
The collection of all a objects in a page is contained within the `links` collection, much as the `img` objects are contained in the `images` collection.

------
## Feature detection
Following values are *falsey*, just about anything else is *truthy*:
- `0`
- `""` (an empty string)
- `null`
- `undefined`
- `[]` (an empty array)
- `false`

In browsers that don’t support geolocation, `navigator.geolocation` is `undefined` and is therefore falsey
```
if (typeof navigator.geolocation != "undefined") {
  // use geolocation
}
```

|STATEMENT|RESULT|
|---------|------|
|`typeof 1`|number|
|`typeof "hello"`|string|
|`typeof true`|boolean|
|`typeof []` (or any array)|object|
|`typeof {}` (or any object)|object|
|`typeof undefined`|undefined|
|`typeof null`|object|

## Browser sniffing
`navigator.appName` - this property returns the model of the browser such as “Microsoft Internet Explorer” for IE or “Netscape” for Firefox, Chrome, and Safari
`navigator.userAgent` - returns a string containing various bits of information, such as the browser version, operating system, and browser model
```
function getBrowserName() {
  var lsBrowser = navigator.userAgent;
  if (lsBrowser.indexOf("MSIE") >= 0) {
    return "MSIE";
  } else if (lsBrowser.indexOf("Firefox") >= 0) {
    return "Firefox";
  } else if (lsBrowser.indexOf("Chrome") >= 0) {
    return "Chrome";
  } else if (lsBrowser.indexOf("Safari") >= 0) {
    return "Safari";
  } else if (lsBrowser.indexOf("Opera") >= 0) {
    return "Opera";
  } else {
    return "UNKNOWN";
  }
}
function getBrowserVersion() {
  var ua = navigator.userAgent;
  var browser = getBrowserName();
  var findIndex = ua.indexOf(browser) + browser.length + 1;
  var browserVersion = parseFloat(ua.substring(findIndex, findIndex + 3));
  return browserVersion;
}
var browserName = getBrowserName();
var browserVersion = getBrowserVersion();
if (browserName == "MSIE") {
  if (browserVersion < 9) {
    document.write("Your version of IE is too old");
  } else {
    document.write("Your version of IE is fully supported");
  }
} else if (browserName == "Firefox") {
  document.write("Firefox is fully supported");
} else if (browserName == "Safari") {
  document.write("Safari is fully supported");
} else if (browserName == "Chrome") {
  document.write("Chrome is fully supported");
} else if (browserName == "Opera") {
  document.write("Opera is fully supported");
} else {
document.write("Sorry this browser version is not supported");
}
```
