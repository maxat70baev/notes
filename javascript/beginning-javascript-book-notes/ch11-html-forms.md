<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 11. HTML Forms
## A simple form with validation
```
<body>
  <form action="" name="form1">
    Please enter the following details:
    <p>
      Name:
      <input type="text" name="txtName" />
    </p>
    <p>
      Age:
      <input type="text" name="txtAge" size="3" maxlength="3" />
    </p>
    <p>
      <input type="button" value="Check details" name="btnCheckForm">
    </p>
  </form>
  <script>
    var myForm = document.form1;
    function btnCheckFormClick(e) {
      var txtName = myForm.txtName;
      var txtAge = myForm.txtAge;
      if (txtAge.value == "" || txtName.value == "") {
        alert("Please complete all of the form");
        if (txtName.value == "") {
          txtName.focus();
        } else {
          txtAge.focus();
          }
      } else {
        alert("Thanks for completing the form " + txtName.value);
        }
    }
    function txtAgeBlur(e) {
      var target = e.target;
      if (isNaN(target.value)) {
        alert("Please enter a valid age");
        target.focus();
        target.select();
      } 
    }
    function txtNameChange(e) {
      alert("Hi " + e.target.value);
    }
    myForm.txtName.addEventListener("change", txtNameChange);
    myForm.txtAge.addEventListener("blur", txtAgeBlur);
    myForm.btnCheckForm.addEventListener("click", btnCheckFormClick);
  </script>
</body>
```

![page373image8704](resources/6E192080845558D4F77D62F50469EFDE.png)

## New Input Types
|TYPE|DESCRIPTION|VALUE|
|----|-----------|-----|
|`color`|A control for specifying a color. The value is the color in hexadecimal format.|A hexadecimal value of the number (`#ff00ff`).|
|`date`|Used for entering the date (year, month, and day).|The date in `yyyy‐mm‐dd` format (`2014‐07‐14`).|
|`datetime`|Allows for entering the date and time based on UTC.|Not yet supported.|
|`email`|A field for editing an e-mail address. The value is automatically validated.|The text input into the field (even if invalid e-mail).|
|`month`|A control for entering month and year; no time zone.|The date in `yyyy-mm` format (`2014-07`).|
|`number`|Creates a control for numeric input, but does not prohibit alpha-character input.|The numeric data input into the field,, or an empty string if not a number.|
|`range`|Creates a native slider for imprecise numeric input.|The value of the slider.|
|`search`|A single-line text entry control.|The text input into the field. Line breaks and removed.|
|`tel`|Creates a control for telephone entry.|The text input into the field. Line breaks are removed.|
|`time`|Allows time input with no time zone.|The time in 24-hour format (15:37 for 03:37PM).|
|`url`|A control for editing absolute URLs.|The text input into the field. Line breaks and leading/trailing whitespace are removed.|
|`week`|Creates a control for entering a date consisting of a week-year number and a week number with no time zone.|The year and week number (`2014-W29`).|

### Attributes to `<input/>` elements
|`TYPE`|`DESCRIPTION`|
|------|-------------|
|`autocomplete`|Specifies that the value of the control can be automatically completed by the browser.|
|`autofocus`|Determines if the control should have focus when the page loads.|
|`form`|The ID of the associated form. If speci ed, the control can be placed anywhere in the document. If not speci ed, the control can only reside within the form.|
|`maxLength`|Specifies the maximum number of characters the user can enter for `text`, `email`, `search`, `password`, `tel`, and `url` types.
|`pattern`|A regular expression that the control’s value is checked against.|
|`placeholder`|Displays a hint to the user of what can be entered in the  field.|
|`required`|Specifies that the user must  ll in a value for the  eld before submitting the form.|
|`min`|The minimum value of the slider.|
|`max`|The maximum value of the slider.|
|`step`|The increment between values.|

```
<body>
  <form name="form1">
    <p>
      <label for="minValue">Min: </label>
      <input type="number" id="minValue" name="minValue" />
    </p>
    <p>
      <label for="maxValue">Max: </label>
      <input type="number" id="maxValue" name="maxValue" />
    </p>
    <p>
      <label for="stepValue">Step: </label>
      <input type="number" id="stepValue" name="stepValue" />
    </p>
    <p>
      <input type="range" id="slider" name="slider" />
    </p>
  </form>
  <div id="output"></div>
  <script>
    var myForm = document.form1;
    var output = document.getElementById("output");
    function formInputChange() {
      var slider = myForm.slider;
      slider.min = parseFloat(myForm.minValue.value);
      slider.max = parseFloat(myForm.maxValue.value);
      slider.step = parseFloat(myForm.stepValue.value);
      output.innerHTML = slider.value;
    }
    myForm.addEventListener("input", formInputChange);
  </script>
</body>
```
