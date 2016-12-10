<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 1. Introduction to Java Script

## Script block in HTML
```
<script>
  // JavaScript goes here
</script>
```
> Developers typically add their `<script>` elements directly before the `<body>` tag.
> With the introduction of the HTML5 specification, it is no longer considered good practice to set the type attribute to `text/javascript` since browsers automatically assume that any `<script>` element without a type attribute is JavaScript.

## Linking to an external JavaScript file
`<script src="MyCommonFunctions.js"></script>`
`<script src="http://www.mysite.com/MyCommonFiles.js"></script>`
> NOTE: when linking to external files, you must not put any code within opening and closing `<script>` tags, and you cannot use the self-closing syntax either.

## Comments
`//` - commenting out in JavaScript

## Document = web page
`document.bgColor = "red";` - sets web page background color to red
`;` - semicolon is used to indicate the end of statement, i.e. anything between `<script>` tags

## Display functions
`alert ()` - this function enables you to alert or inform the user about something by displaying a message box
`()` - function's parameter go inside the parentheses
`document.write()` - displays data in parentheses in browser window
`console.log()` - the same as `document.write()`
