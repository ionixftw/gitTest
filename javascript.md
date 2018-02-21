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
