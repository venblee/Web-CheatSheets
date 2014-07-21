Primitive (value) vs Object (refs)
==================================

ref: 
http://code.tutsplus.com/tutorials/javascript-objects--net-35979
http://modernweb.com/2013/12/23/45-useful-javascript-tips-tricks-and-best-practices/

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


Points
======

false value
-----------

undefined, null, 0, false, NaN, '' (empty string) are all falsy.


Equality
--------

== : perform autocast (autoboxing), slower
=== : type & value equality, faster

```
[10] === 10    // is false
[10]  == 10    // is true
'10' == 10     // is true
'10' === 10    // is false
 []   == 0     // is true
 [] ===  0     // is false
 '' == false   // is true but true == "a" is false
 '' ===   false // is false 
```

Snippets
========

IIFE
----

Function which execute itself when created (way to implement private scoping)

```
(function(){
    // some private code that will be executed automatically
})();  
```

```
(function(a,b){
    var result = a+b;
    return result;
})(10,20)
```

string.trim() "cleaning"
------------------------

string.trim() is available in js 1.8, however if not supported below is a function to do the job

```
String.prototype.trim = function(){return this.replace(/^\s+|\s+$/g, "");};  
```

Check/iterate object properties
-------------------------------

```
for (var name in obj) {  
    if (obj.hasOwnProperty(name)) { 
        // do something with name                    
    }  
}
```


OOP
===

typeof, constructor, instanceof
-------------------------------

- typeof : a JavaScript unary operator used to  return a string that represents the primitive type of a variable,  don’t forget that typeof null will return “object”, and for the majority of object types (Array, Date, and others) will return also “object”.
- constructor : is a property of the internal prototype property, which could be overridden by code.
- instanceof : is another JavaScript operator that check in all the prototypes chain the constructor it returns true if it’s found and false if not.


Best pratices
=============




