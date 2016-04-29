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

---
##加速
[加速javaScript](http://www.w3schools.com/js/js_performance.asp)

##注意
alert(NaN == NaN); //outputs “false”<br>
用isNaN（）函数解决<br><br>
```
function testFunc() {  
//leave the function blank  
}  
alert(testFunc() == undefined); //outputs “true”
```
undefined is the value assigned when a variable is declared and not initialized
```
alert(null == undefined); //outputs “true”
```
null is the value used to represent an object that doesn’t exist
