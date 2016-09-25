#Essential JS Notes

###Switch Statements

Use switch statements when you have *plenty* of conditions b/c it looks cleaner. In contrast if you need to evaluate weird complex conditions, use "if statements."

*Formula*
```js
switch(expression){
case value 1:
statement;
break;

case value 2:
statement;
break;

case value 3:
statement;
break;

default:
statement;
}
```

###Timer Functions

1. setTimeout: cool thing is to use this to detect if a user is active or not
2. setInterval: This executes at least once and loops code forever! So, to cancel looping use "clearInterval(intervalID" ....it's the equivalent of *clearTimeout*
3. requestAnimationFrame: don't need to specify a duration value. Duration is automatically calculated based on current frame rate.

*setTimeout Formula*

```js
var timeID = setTimeout(somefunction, delayinMilliseconds);
```

```js
function showAlert(){
alert("moo");
}
var timeID = setTimeout(showAlert, 5000);
```

*setInterval Formula*

```js
var intervalID = setInterval(someFunction, delayinMilliseconds)
```

```js
function drawText(){
document.querySelector("p").textContent += "#\n";
var intervalID = setInterval(drawText, 2000);
}
```

###Variable Scope
Anytime a variable is used without being declared using "var" it'll always live globally.

```js
function setState(){
state = "on";
}

setState();
alert(state);       #on
```

###Closures
allow functions to keep on working even if their environments drastically change or dissappears.
