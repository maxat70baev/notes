# HTML - Hyper text markup language

## General structure
```
<!DOCTYPE html>       <!--ALWAYS 1ST LINE-->
<html>                <!--ALWAYS 2ND LINE-->
  <head>
    <title>...</title>
  </head>
  <body>
    ...
  </body>
</html>               <!--ALWAYS LAST LINE-->
```

## Tags
`<tag>...</tag>` - opening and closing tags

## Metadata
`<!DOCTYPE html>` - tells the web browser to expect an HTML document
`<html>...</html>` - the root of the HTML document and parent of all other HTML elements on the webpage
`<head>...</head>` - enclose other metadata about the site, such as its title
`<title>...</title>` - contains the site's title, which is one way users can find your site through a search engine, like Google
`<meta charset="utf-8"/>` - tells the web browser which character set to use (in this case, the character set is "utf-8")

## Links
`<a href="URL">Link name</a>` - "anchor" hyperlink syntax
`<img src="URL" />` - self-closing tag of image

## Video
```
<video width="320" height="240" controls>
  <source src="video-url.mp4" type="video/mp4">
</video>
```
* `width` and `height` - set the size of the screen that displays the video
* `controls` - adds play, pause and volume control
* `source src` - sets the URL of the video to play
* `type` - specifies different video formats

## Style application
`<tag style="property: value; ...;">...</tag>` - applying style
`<strong>Text</strong>` - bold **text**
`<em>Text</em>` - italic *text*
`&copy;` - is a character code, which web browsers interpret as the copyright symbol: ©

## Lists
* Unordered list
```
<ul>
    <li>This is list item</li>
</ul>
```
* Ordered list
```
<ol>
    <li>This is list item</li>
</ol>
```

## Tables
```
<table>                           <!--GENERAL TABLE STRUTURE-->
  <thead>                         <!--TABLE HEADING-->
    <tr>                          <!--TABLE ROW-->
      <th>1st Column Heading</th> <!--TABLE HEADING-->
      <th>2nd Column Heading</th>
    </tr>
  </thead>
  <tbody>                         <!--TABLE BODY-->
    <tr>                          <!--TABLE ROW-->
      <td>First Cell</td>         <!--TABLE DATA-->
      <td>Second Cell</td>
    </tr>
  </tbody>
</table>
```
`<th colspan="n">Heading across n columns</th>` - table heading across *n* columns
`<td valign="top | middle | bottom | baseline">...</td>` - vertical align of table cell content

## Division blocks
`<div style="width:500px;height:50px;background-color:red"></div>` - div block

## Comments
`<!--COMMENT-->` - HTML
`/*COMMENT*/` - CSS

-------
# CSS - Cascading style sheets

## General CSS syntax
```
selector {
  property:value;
}
```

## CSS Properties
`width` - could be in *px* and *%*
`height` - same as width
`background-color`
`background-image:url();` - sets background image
`border`
`border-radius` - *none* = square, *5* - a bit rounded, *100* - circle
`font-family` - e.g. Verdana, serif, sans-serif
`font-size` - size can be assigned in pixels (px), rems, or ems:
* `pixel (px)`: Standard unit of measurement for sizing fonts and other HTML elements.
* `rem`: Represents the default font size for the web browser. Rems can be used to ensure that HTML elements scale in proportion to each other on various web browsers and screen sizes. On most web browsers, 1rem is equivalent to 16px, 2rem is equivalent to 32px (a doubling), 3rem is equivalent to 48px (a tripling) and so on.
* `em`: A relative value that changes in proportion to the size of the parent element. For example, if a parent element has font-size: 20px;, child elements with font-size: 1em; would be equivalent to 20px. Child elements with font-size: 0.5em; would be equivalent to 10px (a halving) and so on.

`font-weight` - **bold**, *italic*
`text-transform` - UPPERCASE, lowercase
`color` - could be in words or in hex

## Inline CSS withing HTML
```
<html>
  <head>
    <style>           <!--BETTER TO BE USED IN HEAD-->
      p {color:red;}
    </style>
  </head>
  <body></body>
</html>
```

## External CSS using link
```
<html>
  <head>
    <link type="text/css" rel="stylesheet" href="stylesheet.css" />
  </head>
  <body></body>
</html>
```
* `rel` - specifies the relationship between the current file and the file being linked to: in this case, the `rel` attribute is "stylesheet"
* `type` - specifies the type of file linked to
* `href` - provides the URL of the file being linked to

## Bordering
```
selector {
  border:1px solid black;
}
```
* In CSS, the border property's value requires three parts:
    1. `thickness`: Sets the thickness of the border, using pixels, ems, or rems.
    2. `type`: Sets the border type. Common options are solid, dotted, and dashed. There are many others.
    3. `color`: sets the border's color, using named colors, HEX, or RGB values.

## Multiple selectors
`div div p {/*CSS Stuff*/}` - grab `<p>` that are inside two `<div>`, not all `<p>`

## One selector to rule them ALL
`* {property:value;}` - applies to every element of an html

## Children
`div > p {/*CSS Stuff*/}` - grab `<p>` that are nested directly inside of `<div>`, i.e. **direct CHILDREN**

## Classes and ID's
|HTML                     |CSS                    |
|:-----------------------:|:---------------------:|
|ID                       |ID                     |
|`<p id="intro">...</p>`  |`#intro {/*CSS Stuff*/`|
|CLASS                    |CLASS                  |
|`<p class="body">...</p>`|`.body {/*CSS Stuff*/}`|
* Classes are useful when you have a **BUNCH** of elements that should receive the same styling
* ID's are great for exactly **ONE** element

## Override rule
* Certain selectors will **override** others if they have a greater specificity value, e.g. `ul li p {}` is more specific than `p {}`

## Pseudo-selectors
* Using pseudo-selectors you can control the appearance of unvisited and visited links, and even links the user is hovering over but hasn't clicked
`selector:pseudo-class_selector {property:value;}` - e.g. `a:hover|link|visited`

## First child and Nth child
* First-child - another pseudo-class selector used to apply styling to only the elements that are the first children of their parents
`selector:first-child {property:value;}`
* Nth child - obvious
`selector:nth-child(x) {property:value;}`

## CSS positioning
### Align
`text-align:center;` - text is centered
`vertical-align: baseline|bottom|middle|sub|super|text-bottom|text-top|top|±..px|±..%;` - vertical align of an element relative to its parent, surrounding text or table cell

## Display
`selector {display:value;}` - property for positiong is `display`
`selector {display:block;}` - won't let anything sit next to it, i.e. takes up the full width
`selector {display:inline-block;}` - allow other elements sit next to it on the same line
`selector {display:inline;}` - without formatting like a block, i.e. takes up as much width as it needs (not the whole line); does not maintain "box"ness => better suited for HTML elements that are blocks by default, e.g. headers and paragraphs
`selector {display:none;}` - makes an element and its content disappear entirely
`selector {display:flex; flex-wrap:wrap}` - align multiple page elements horizontally wrapping them according to the size of the browser window

### Box Model
![](https://s3.amazonaws.com/codecademy-blog/assets/ae09140c.png)
`margin:auto;` - object is centered
`margin-top|right|bottom|left:value;`
`margin:value;` - equal marging for all sides
`margin:value value;` - 1 value - top and bottom, 2 value - right and left
`margin:value value value;` - 1 - top, 2 - left and right, 3 - bottom
`margin:value value value value;` - **ALL** at once, clockwise starting from the top
`padding-top|right|bottom|left:value;` - the same as `margin` but **TEXT** is in its core
* Negative values move element in opposite direction
* The margin is a transparent area outside the border of an element

### Float
* If you have several elements all floating, they all know the others are there and don't land on top of each other
`float:right|left|top|bottom;`

### Clear
`clear:right|left|both;`
* If you tell an element to `clear:left;` it will move below any floating elements on the left side of the page

### Static vs. Relative
* Static position is default
1. **Absolute positioning** - positioned in relation to the first parent element that doesn't have `position:static;`, if there's none - relative to `<html>`
`selector {position:absolute;}`
2. **Relative positioning** - it tells the element to move relative to where it would have landed if it just had the default static positioning
`selector {position:relative;}`
3. **Fixed positioning** - anchors an element to the browser window => if you scroll up/down, the fixed element stays put even as other elements scroll past
`selector {position:fixed;}`

## CSS Summary
![](https://s3.amazonaws.com/codecademy-content/courses/ltp/img/2/css-summary.png)