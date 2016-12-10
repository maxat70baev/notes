<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 10. Events
## Connecting code to events
### Handling events via HTML attributes
`onclick` - an attribute similar to `href`
`ondbclick` - on double-click
`onmouseover` - on hover

Example of displaying random images with Object Property Event Handlers and the Event Object
```
<body>
  <img src="usa.gif" onclick="changeImg(event)" />      //`onclick` attribute
  <img src="mexico.gif" onclick="changeImg(event)" />   //`onclick` attribute
  <script>
    var myImages = [
    "usa.gif", "canada.gif", "jamaica.gif", "mexico.gif"
    ];
    function changeImg(e) {  //parameter means event
      var el = e.target;
      var newImgNumber = Math.round(Math.random() * 3);
      while (el.src.indexOf(myImages[newImgNumber]) != -1) {
        newImgNumber = Math.round(Math.random() * 3);
      }
      el.src = myImages[newImgNumber];
    }
  </script>
</body>
```

### Handling events via Object Properties
Example of displaying random images with Object Property Event Handlers
```
<body>
  <img id="img0" src="usa.gif" />     //`id` instead of `onclick` attribute
  <img id="img1" src="mexico.gif" />  //`id` instead of `onclick` attribute
  <script>
    var myImages = [
      "usa.gif", "canada.gif", "jamaica.gif", "mexico.gif"
    ];
    function changeImg(e) {
      var el = e.target;
      var newImgNumber = Math.round(Math.random() * 3);
      while (el.src.indexOf(myImages[newImgNumber]) != -1) {
        newImgNumber = Math.round(Math.random() * 3);
      }
      el.src = myImages[newImgNumber];
    }
    document.getElementById("img0").onclick = changeImg;
    document.getElementById("img1").onclick = changeImg;
    //retrieve `img` objects and assign `onclick` properties
  </script>
</body>
```

## The Standard Event model
### Connecting Code to Events - the Standard Way
The `EventTarget` object de nes two methods for adding and removing event listeners (remember that an `EventTarget` is an element). The first method, `addEventListener()`, registers an event listener on the target on which it’s called.

Example of displaying random images with Standard DOM event model
```
<body>
  <img id="img0" src="usa.gif" />
  <img id="img1" src="mexico.gif" />
  
  <script>
    var myImages = [
    "usa.gif",
    "canada.gif",
    "jamaica.gif",
    "mexico.gif"
    ];
    
    function changeImg(e) {
      var el = e.target;
      var newImgNumber = Math.round(Math.random() * 3);
      while (el.src.indexOf(myImages[newImgNumber]) != -1) {
        newImgNumber = Math.round(Math.random() * 3);
      }
      el.src = myImages[newImgNumber];
    }
    
    document.getElementById("img0").addEventListener("click", changeImg);
    document.getElementById("img1").addEventListener("click", changeImg);
    //an event listener is registered for the `click` event
    //instead of using each element object’s `onclick` property, you register the `click` event handler using addEventListener()
  </script>
</body>
```

### Using Event Data
|PROPERTIES OF THE EVENT OBJECT|DESCRIPTION|
|------------------------------|-----------|
|`bubbles`|Indicates whether an event can *bubble* — passing control from one element to another starting from the event target and bubbling up the hierarchy|
|`cancelable`|Indicates whether an event can have its default action canceled|
|`currentTarget`|Identifies the current target for the event as the event traverses the DOM|
|`defaultPrevented`|Indicates whether or not `preventDefault()` has been called on the event|
|`eventPhase`|Indicates which phase of the event flow an event is in|
|`target`|Indicates which element caused the event; in the DOM event model, text nodes are a possible target of an event|
|`timestamp`|Indicates at what time the even occured|
|`type`|Indicates the name of the event|

## Native Drag and drop
### Creating a drop target
```
<head>
  <title>Chapter 10: Example 18</title>
  <style>
    .drop-zone {
    width: 300px;
    padding: 20px;
    border: 2px dashed #000;
    }
  </style>
</head>
<body>
  <div id="dropZone" class="drop-zone">Drop Zone!</div>
  <div id="dropStatus"></div>
  <script>
    function handleDragEnter(e) {
      dropStatus.innerHTML = "You're dragging something!";
    }
    var dropZone = document.getElementById("dropZone");
    var dropStatus = document.getElementById("dropStatus");
    dropZone.addEventListener("dragenter", handleDragEnter);
  </script>
</body>
```

![page347image744](resources/26212DEC0C319F19F239ED883E2FBE92.png)

|DRAG SOURCE EVENTS|DESCRIPTION|
|------------------|-----------|
|`dragenter`|Fires when the mouse is first moved over the target element while dragging|
|`dragover`|Fires on the target as the mouse moves over an element while dragging|
|`dragleave`|Fires on the target when the mouse leaves the target while dragging|
|`drop`|Fires on the target when the drop (the user releases the mouse button) occurs|

### Transferring data
`DataTransfer` object that is used to hold the the data that is being dragged during a drag-and-drop operation

Example of full Drag and Drop
```
<head>
  <style>
    [data-drop-target] {
      height: 400px;
      width: 200px;
      margin: 2px;
      background-color: gainsboro;
      float: left;
    }
    .drag-enter {
      border: 2px dashed #000;
    }
    .box {
      width: 200px;
      height: 200px;
    }
    .navy {
      background-color: navy;
    }
    .red {
      background-color: red;
    } 
  </style>
</head>
<body>
  <div data-drop-target="true">
    <div id="box1" draggable="true" class="box navy"></div>
    <div id="box2" draggable="true" class="box red"></div>
  </div>
  <div data-drop-target="true"></div>
  
  <script>
    function handleDragStart(e) {
     e.dataTransfer.setData("text", this.id);
    }
    function handleDragEnterLeave(e) {
      if (e.type == "dragenter") {
        this.className = "drag-enter";
      } else {
        this.className = "";
      }
    }
    function handleOverDrop(e) {
      e.preventDefault();
      if (e.type != "drop") {
        return;
      }
      var draggedId = e.dataTransfer.getData("text");
      var draggedEl = document.getElementById(draggedId);
      if (draggedEl.parentNode == this) {
        return;
      }
      draggedEl.parentNode.removeChild(draggedEl);
      this.appendChild(draggedEl);
      this.className = "";
    }
    var draggable = document.querySelectorAll("[draggable]");
    var targets = document.querySelectorAll("[data-drop-target]");
    for (var i = 0; i < draggable.length; i++) {
      draggable[i].addEventListener("dragstart", handleDragStart);
    }
    for (i = 0; i < targets.length; i++) {
      targets[i].addEventListener("dragover", handleOverDrop);
      targets[i].addEventListener("drop", handleOverDrop);
      targets[i].addEventListener("dragenter", handleDragEnterLeave);
      targets[i].addEventListener("dragleave", handleDragEnterLeave);
    }
  </script>
</body>

![page356image9160](resources/D550F9AD42C24D47BAD3847A5BA39F2C.png)
