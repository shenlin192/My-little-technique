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

##parseInt()
```
var iNum1 = parseInt(“1234blue”); //returns 1234
var iNum2 = parseInt(“0xA”); //returns 10
var iNum3 = parseInt(“22.5”); //returns 22
var iNum4 = parseInt(“blue”); //returns NaN
var iNum1 = parseInt(“AF”, 16); //returns 175
```

##Building an Object
The most commely used way is to combine a constructor(define non-functional attributes) and the prototype chain(define functional attributes)
```
function Car(sColor, iDoors, iMpg) {
this.color = sColor;
this.doors = iDoors;
this.mpg = iMpg;
this.drivers = new Array(“Mike”, “Sue”);
}
Car.prototype.showColor = function () {
alert(this.color);
};
var oCar1 = new Car(“red”, 4, 23);
var oCar2 = new Car(“blue”, 3, 25);
oCar1.drivers.push(“Matt”);
alert(oCar1.drivers); //outputs “Mike,Sue,Matt”
alert(oCar2.drivers); //outputs “Mike,Sue”
```
