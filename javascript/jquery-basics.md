[jQuery Documentation available here](http://learn.jquery.com/)

# jQuery Events

## General Setup
```
$(document).ready(function() {
    $('thingToTouch').event(function() {
        $('thingToAffect').effect();
    });
});
```

## Mouse and Keyboard Events
`.click()`
`.dblclick()`
`.hover()`
`.focus()`
`.keydown(function(key) {})`/`.keypress(function(event) {})` - every key press on a keyboard is translated into a number for the computer to use ([Key codes available here](http://help.adobe.com/en_US/AS2LCR/Flash_10.0/help.html?content=00000520.html))
Example of `.keypress()`:
```
$(document).keypress(function(event) {
  if(event.which === 109) {
    $('.dropdown-menu').toggle();
  }
});
```

Example of `.hover()`:
```
$('div').hover(
    function(){
      $(this).addClass('highlight');
   },
   function(){
      $(this).removeClass('highlight');
   }
);
```

# DOM manipulation
`.hide()` - hides the selected HTML element
`.show()` - displays an element
`.toggle()` - alternates hiding and showing an element
`.addClass()` - adds a CSS class to an element
`.removeClass()` - removes a class from an element
`.toggleClass()` - alternates adding and removing a class from an element
`.next()` - gets the next sibling
`.prev()` - gets the previous sibling
`.children()` - gets the children of the selected element

# jQuery effects
`.fadeOut(<speed>)`
`.fadeIn(<speed>)`
`.animate(<animation>, <time>)`, e.g. `.animate({left:'+=10px'},500)` - add ten pixels to the current distance from the left margin
`.slideDown()`
`.slideUp()`