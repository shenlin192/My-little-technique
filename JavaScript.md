##加载

It is a good idea to place scripts at the bottom of the <body> element.<br>
This can improve page load, because script compilation can slow down the display.<br>

Placing JavaScripts in external files has some advantages:<br>

1. It separates HTML and code
2. It makes HTML and JavaScript easier to read and maintain
3. Cached JavaScript files can speed up page loads

---

Using document.write() after an HTML document is fully loaded, will delete all existing HTML:

---
##type
- void String, Number, and Boolean objects. They complicate your code and slow down execution speed.
- NaN means "not a number", but itself is a number, and typeof NaN returns number
- JavaScript objects cannot be compared.
- In JavaScript, all data types have a valueOf() and a toString() method.
