# Javascript

## The script tag

* If you want your javascript code to run after the elements have rendered add the script tag after the end of the body

```html
<!DOCTYPE html>
<html>
    <head>
    </head>

    <body>
    </body>
    <script></script>
    <script src="/script.js"></script>
</html>
```
* To run your Javascript before the elements have rendered add the script tag inside the head
* It causes Javascript render blocking

```html
<!DOCTYPE html>
<html>
    <head>
        <script></script>
        <script src="/script.js"></script>
    </head>

    <body>
    </body>
    
</html>
```
* It happens because browsers render HTML files from top to bottom

* script has two other options other than default 
* async
    * HTML parsing is only blocked when javascript executes
    
```html
<!DOCTYPE html>
<html>
    <head>
        <script></script>
        <script src="/script.js" async></script>
    </head>

    <body>
    </body>
    
</html>
```
* defer
    * Js executes after HTML is parsed

```html
<!DOCTYPE html>
<html>
    <head>
        <script></script>
        <script src="/script.js" defer></script>
    </head>

    <body>
    </body>
    
</html>
```

## Some Javascript guidelines

* Javascript is case sensitive
* It uses camelCasing
* Variables should start with a lower case letter

```javascript
var javascriptVariable = 42;
```
* Objects and classes should start with an upper case letter

```javascript
var date = new Date();
```
* Single line comments start with two forward slashes

```javascript
// This is a single line comment
```
* Multi-line comments start with a slash and an asterisk and ends with an asterisk and a slash

```javascript 
/* This is a multi
line comment.
Everything is alright. */
```
## Variables

* Variables start with a var in javascript;
* They are case sensitive
* Letters(a-z)(A-Z), numbers(0-9), underscore(_) and dollar($) sign 
* They cannot start with a number and they cannot contain white spaces
* Uninitialized variables are undefined
* Undefined and undeclared are not the same thing

```javascript
var <variableName>;
var a;
var A;
var $A;
var a_A;
```
* To assign a value we use the equal(=) sign

```javascript
// Variable declaration
var a;
var b;
var sum;
// shorthand
var a, b, sum;
// declaration and assignment
var a = 1;
var b = 2;
// declaration and assignment shorthand
var a = 1, var b = 2;
```
* Javascript is a weakly typed language
* So we don't need to define a variable type
* A variable can store any type data

## Primitive data types in Javascript

* Data types in javascript include
    * Numeric
    * String
    * Boolean
    * null
    * undefined

```javascript
// Numeric 
var number = 3.14159265;
// String
// Use single or double quotation marks when using strings
var string = "This is a string!";
var string2 = 'This is also a string';
var string3 = "This is yet another 'string'";
var string4 = 'This is the same as string3 only the "quotation" marks are changed';
// var string5 = "This string is not going to "work"";
// Escaping with a backslash
var string6 = "But this will \"work\"";
// Boolean
var javaScript = true;
var java = false;
// Null
var empty = null;
// Undefined
// When a variable is declared but no value has been assigned to it
// Default placeholder value for any unassigned variable
var nothing; // undefined
```
* To know the variable data type use typeof

```javascript
var a = 1;
console.log(typeof a); //number
```

