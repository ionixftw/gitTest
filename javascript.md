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
* camelCasing is preferable when naming variables
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
* Multi-line comments start with a slash and an asterisk and end with an asterisk and a slash

```javascript 
/* This is a multi
line comment.
Everything is alright. */
```
## Variables

* Variables start with a var in javascript
* They are case sensitive
* Letters(a-z)(A-Z), numbers(0-9), underscore(_) and dollar($) sign are allowed when naming variables
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

## Operators

* Assignment operator(=)

```javascript
var a = 1;
``` 

* Arithmetic operators(+,-,*,/)

```javascript
var a = 2 + 3;
var a = a + 4; // normal
var a += 4; // shorthand
var b = 4 - 2;
var b = b -2; // normal
var b -= 2; // shorthand
var c = 2 * 3;
var d = 6 / 3;
```
* The plus (+) arithmetic operator is the only operator that is also used in strings

```javascript
var a = 5;
var b = "3";
var sum = a + b; // 53 string
var sum2 = a - b; //2 (works because minus[-] is not used in string data types)
```

* Unary operators(++,--)
```javascript
var a = 1;
a++; // increment
a--; // decrement
// There are prefix and postfix unary operators
// Prefix operator adds 1 to the variable and then returns the new value
console.log(++a); // 2
// Postfix operator returns the original value and then adds 1
console.log(a++); // 2
console.log(a); // 3
```
## Conditional statements and logic

* If statement
    * If statement works as an on or off switch
    * If a condition is true then the code block runs

```javascript
if (typeof a == undefined) {
    alert("a is not defined");
}
```
* If else statement
    * If the first condition is not true then the else block of code will run

```javascript
if (typeof a == undefined) {
    alert("a is not defined");
} else {
    alert("a is defined");
}
```
* Equality operator (==)
* Strict equality (===)
* Less than (<)
* Greater than (>)
* Less than or equal to (<=)
* Greater than or equal to (>=)
* Not equal (!=)
* Not strict equal (!==)
* Not less than (!<)
* Not less than or equal to (!<=)
* Not greater than (!>)
* Not greater than or equal to (!>=)
* These logical statements always return a boolean (either true or false)

```javascript
// Equality operator
var a = 5, b = "5";

if ( a == b ) {
    console.log("A is equal to B"); // console shows this message
} else {
    console.log("A is not equal to B");
}
// Strict Equality
var a = 3, b = "3";
if ( a === b ) {
    console.log("A is equal to B");
} else {
    console.log("A is not equal to B"); // console shows this message
}
```


* Logical AND operator (&&)
* Logical OR operator (||)

```javascript
// Logical and combines two or more different conditions
// If both of them are true then the code block runs

if ( a == b && c == d) {
    // some code
}

// Logical or also combines two or more different conditions
// If either of them or both of them are true then the code block runs

if (a == b || c == d) {
    //some code
}

// But there is no XOR operator in javascript 

/* To check only either of them are true but not both of them are
 true we need to manually make that condition 
 combining AND and OR operators */

if ( (a == b || c == d) && ( (a == b) != (c == d) ) ) {
    // some code
}
```
* Ternary operator (Shorthand for if else)

```javascript

// normal if else
if (a == b) {
    alert("Equal!");
} else {
    alert("Not Equal!");
}

// ternary operator (shorthand if else)
// condition ? true : false;
a == b ? alert("Equal!") : alert("Not Equal!");
```

## Arrays

* Arrays are containers for multiple variables
* To create an array simply create an undefined variable and then assign values using the array literal in a coma separated list 
* Each value in the array can be a separate data type
* Array index starts at 0

```javascript
// Array literal []
var colors = ["orange", "red", "blue", "pink"];
var miscellaneous = ["orange", 5, false, "deadmau5"];
// Assigning a new value
colors[4] = "green";
// first item
var first = colors[0]; // orange
// last item 
var last = colors[colors.length - 1]; //green

```
* Arrays are objects
* So it also has properties and methods
* Array properites

```javascript
// array.length
var colors = ["orange", "red", "blue", "pink"];
console.log(colors.length); // 4
```
* Array methods

```javascript

var colors = ["orange", "red", "blue", "pink"];
// Reverse the array
colors.reverse(); // ["pink", "blue", "red", "orange"]

// Remove the first value of the array
colors.shift(); // ["blue", "red", "orange"]

// Add values to the front of the array
colors.unshift("purple", "magenta"); // ["purple", "magenta", "blue", "red", "orange"]

// Remove the last value of the array
colors.pop();// ["purple", "magenta", "blue", "red"]

// Add items at the end of the array
colors.push("white", "yellow"); // ["purple", "magenta", "blue", "red", "white", "yellow"]

// Remove n items after a specified item
// array.splice(pos, n)
colors.splice(2,1); // ["purple", "magenta", "red", "white", "yellow"]

// Copy an array
var newColor = colors.slice();

// Show the index number of a search term
// array.indexOf(search, index)
// Here index is the starting position of the search
var index = newColor.indexOf("white", 2); // 3

// Show all the items in an array as a string
// array.join(separator)

var arrayAsString = newColor.join(", "); // purple, magenta, red, white, yellow

```

## Functions

* Function separates a block of code so that it can be executed when it is called
* It helps to organize code
* It helps to create reusable code blocks
* To declare a function we use the word function followed by a name, parentheses and curly braces
* Curly braces hold the block of code that gets executed when the function is called
* We invoke a function by the function name and parentheses
* The general convention is to declare functions at the top of the js file

```javascript
// Named function
function firstFunction() {
    // block of code
}
firstFunction();

// Anonymous function
var add = function(a,b) {
    return a + b;
}
add(5 + 4); // 9
```
