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

After React uses diffing, it then only changes the virtual objects that have change on the real DOM. React updates only the necessary parts. To summarize:
1. Entire virtual DOM gets updated
2. Diffing happens
3. Changed Objects and only Changed Objects get updated in real DOM
4. Changse on real DOM cause screen to change

##Advance JSX
Can't use "class" as that's a reserved term. Instead, use "className" (yes, include the upper camelcase) like this:

```js
ReactDOM.render(
<h1> {2+3} </h1>,
document.getElementById('app')
);
```

##Event Listeners

```js
<img onClick={myFunction} />
```

To insert conditionals, it'll look like this:

```js
if (coinToss()== 'heads' {
var img = <img src = {pics.kitty} />;
} else {
var img = <img src = {pics.doggy} />,
}
```

##Ternary Operator
> x ? y:z
This means check if x is true, then execute y, if it's false then execute z.


#Part 2: Components (reuseable code) and Props (properties)

require('react') ------------> returns a JS object with methods needed to use React.

require('react-dom') --------> returns JS object with methods to interact with DOM.

~Every component classes is like a factory that creates components. To use this, it's React.createClass

Properties/Props are passed in from the parent and they're immutable and don't change when components came alive.

##3 API's React uses a lot
1. componentDidMount: method gets called after component rendered
2. getInitialState: method runs before component gets rendered allows you to mod component's state object
3. setState: method lets you update value of state object
