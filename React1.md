##React's essentials:

1. JSX
2. Components
3. Store data via props and state

##JSX

* Looks like HTML
* Syntax extension means JSX compiles html-looking stuff into regular JS
* A JSX attribute is like HTML syntax; name followed by value. e.g. my-attribute-name = "my-attribute-value"
* A single JSX element can have many attributes

##Nested JSX

*Nested JSX expressions can be saved as variables
```js
var theGoogle= (
<a href = "https://www.google.com">
<h1> "Click me, I'm google" </h1>
/>
);
```

##How to Render React

Formula:
ReactDOM.render(
firstparameter,
placement/location on the elementId
)
Like this:

```js
ReactDOM.render(
<h1> Hello World </h1>,
document.getElementById('app')
```


ReactDOM.render takes a JSX expression, creates a corresponding tree of DOM nodes, adds tree to the DOM. It only updates DOM elements that have changed. If you render same thing twice, second render does nothing!

Only updating the necessary DOM elements is a larage part popularized by only changing the virtual DOM, not changing the real DOM all the freaking time, or else that slows performance.

> Think of changing the virtual DOM as editing the blueprint as apposed to changing rooms in the whole house all the time.

![picture](http://media.lifehealthpro.com/lifehealthpro/article/2015/06/11/914-reality-vs-blueprint-515657165-738x415ts.jpg)
