<a href="http://www.wrox.com/WileyCDA/WroxTitle/Beginning-JavaScript-5th-Edition.productCd-1118903331.html"><img style="height:250px" src="http://ecx.images-amazon.com/images/I/51qu0dP1bCL._SX396_BO1,204,203,200_.jpg" /></a>

# 13. Data Storage
## Cookie
### `setCookie` function
```
function setCookie(name, value, path, expires) {
  value = escape(value);
  if (!expires) {
    var now = new Date();
    now.setMonth(now.getMonth() + 6);
    expires = now.toUTCString();
  }
  if (path) {
    path = ";Path=" + path;
  }
  document.cookie = name + "=" + value + ";expires=" + expires + path; }
```

### `getCookieValue` function
```
function getCookieValue(name) {
  var value = document.cookie;
  var cookieStartsAt = value.indexOf(" " + name + "=");
  if (cookieStartsAt == -1) {
    cookieStartsAt = value.indexOf(name + "=");
  }
  if (cookieStartsAt == -1) {
    value = null;
  } else {
    cookieStartsAt = value.indexOf("=", cookieStartsAt) + 1;
    var cookieEndsAt = value.indexOf(";", cookieStartsAt);
    if (cookieEndsAt == -1) {
      cookieEndsAt = value.length;
    }
    value = unescape(value.substring(cookieStartsAt, cookieEndsAt));
  }
  return value;
}
```
