Primitive (value) vs Object (refs)
==================================

ref: 

- http://code.tutsplus.com/tutorials/javascript-objects--net-35979
- http://modernweb.com/2013/12/23/45-useful-javascript-tips-tricks-and-best-practices/
- http://developer.nokia.com/community/wiki/JavaScript_Performance_Best_Practices
- https://code.google.com/p/jslibs/wiki/JavascriptTips

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

Filter / intercept a function call
----------------------------------
```
function bar(a, b, c, d, e, f) {

  Print(a, b, c, d, e, f)
}

function foo() {

  bar.apply(this, arguments);
}

foo(1, 2, 3, 4, 5, 6); // prints: 123456
```

Remove an item by value in an Array object
------------------------------------------
```
var arr = ['a', 'b', 'c', 'd'];
var pos = arr.indexOf( 'c' );
pos > -1 && arr.splice( pos, 1 );
Print( arr ); // prints: a,b,d
```

Destructuring assignments
-------------------------

```
 var { a:x, b:y } = { a:7, b:8 };
 Print(x); // prints: 7
 Print(y); // prints: 8
```

Generator Expressions
---------------------

extracts index names
```
[ y for ( y in [5,6,7,8,9] ) ] // is [0,1,2,3,4]
```

extracts values

```
[ y for each ( y in [5,6,7,8,9] ) ] // is [5,6,7,8,9]
```

Expression closure
------------------

inline function, return implicit
```
function(x) x * x;
```


IIFE
----

Function which execute itself when created (way to implement private scoping)

```
(function(){
    // some private code that will be executed automatically
})();  
```

Samples
```
(function(a,b){
    var result = a+b;
    return result;
})(10,20)
```

Usage
```
(function foo() {
  Print( foo.name );
})(); // prints: foo
foo(); // raise a ReferenceError

!function foo() {
}
foo(); // raise a ReferenceError

var bar = function foo() {
}
foo(); // raise a ReferenceError
```

string.trim() / string cleaning
-------------------------------

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

HTML escape function
--------------------
```
function escapeHTML(text) {  
    var replacements= {"<": "&lt;", ">": "&gt;","&": "&amp;", "\"": "&quot;"};                      
    return text.replace(/[<>&"]/g, function(character) {  
        return replacements[character];  
    }); 
}
```



Patterns
========

Singleton 
---------
```
function MySingletonClass() {

  if ( arguments.callee._singletonInstance )
    return arguments.callee._singletonInstance;
  arguments.callee._singletonInstance = this;

  this.Foo = function() {
    // ...
  }
}

var a = new MySingletonClass()
var b = MySingletonClass()
Print( a === b ); // prints: true
```


Factory method 
--------------

```
Complex = new function() {

        function Complex(a, b) {
                // ...
        }

        this.fromCartesian = function(real, mag) {

                return new Complex(real, imag);
        }

        this.fromPolar = function(rho, theta) {

                return new Complex(rho * Math.cos(theta), rho * Math.sin(theta));
        }
}


var c = Complex.fromPolar(1, Math.pi); // Same as fromCartesian(-1, 0);

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

primitive operations over function calls
----------------------------------------

- Usage vanilla js if possible, it's usually, but individual cases need to be test though
- Tradeoff readability - performances

```
var min = Math.min(a,b); 
A.push(v);
V.map(function(v){v.p = 1; return v;})
```

```
var min = a < b ? a : b; 
A[A.length] = v;
for (var i = 0, len = V.length; i < len; i++) {V[i].p = 1;} return V;
```
