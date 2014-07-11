Primitive (value) vs Object (refs)
----------------------------------

ref: http://code.tutsplus.com/tutorials/javascript-objects--net-35979

copy
----

```
var str = 'foo' 
var copy = str; 
str = null; 
 
str  // null
copy // 'foo'
```

equality
--------

```
var val1 = 10;
var val2 = 10;
var obj3 = new Number('10'); // A complex numeric object because new was used.
var obj4 = obj3;
 
val1 === val2 // true
 
val1 === obj3 // false (val != ref)
 
obj3 === obj4 // true (refs equals)

obj4 = 10;
 
obj3 === obj4 // false (obj4 is val, obj3 is ref)
```
