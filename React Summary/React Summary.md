---
theme : "white"
transition: "zoom"
highlightTheme: "darkula"
logoImg: "https://raw.githubusercontent.com/evilz/vscode-reveal/master/images/logo-v2.png"
slideNumber: true
---






# ECMAScript

## ECMAScript / JavaScript

JavaScript is an implementation of the ECMAScript standard.

![:scale 100%](https://adrianmejia.com/images/history-javascript-evolution-es6.png)

[What’s the difference between JavaScript and ECMAScript?](https://www.freecodecamp.org/news/whats-the-difference-between-javascript-and-ecmascript-cba48c73a2b5/ "")

---

[The TC39 Process](https://tc39.github.io/process-document/ "")

![:scale 70%](ecmascript_tc39.png)



[tc39/proposals: Tracking ECMAScript Proposals](https://github.com/tc39/proposals "")

---

## ECMAScript Syntax

regex

object.assign



`!! function() {}`

[javascript - What does the exclamation mark do before the function? - Stack Overflow](https://stackoverflow.com/questions/3755606/what-does-the-exclamation-mark-do-before-the-function "")

```js
function foo() {console.log('a');} // undefined
!function foo() {console.log('a');} // false
function foo() {console.log('a');}() // Uncaught SyntaxError: Unexpected token )
!function foo() {console.log('a');}() 
// a
// true
!!function foo() {console.log('a');}()
// a
//false
(function foo() {console.log('a');})()
// a
// undefined
```

[Javascript “Bang, Bang. I shot you down” - Use of double bangs (!!) in Javascript.](https://medium.com/swlh/javascript-bang-bang-i-shot-you-down-use-of-double-bangs-in-javascript-7c9d94446054 "")

**the double-bang returns the boolean true/false association** of a value.

### JSON

JSON syntax is a subset of JavaScript object expression.

* no comments allowed
* `package.json`

---

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021-3100"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    },
    {
      "type": "mobile",
      "number": "123 456-7890"
    }
  ],
  "children": [],
  "spouse": null
}
```

---

### JavaScript Object

```javascript
let home = "home ";
let phone = "123456";

let aman = {
    first_name: "fname",
    'middle name': "mname",
    "last name": "lname",
    [home + "address"]: "hz",
    phone
};
JSON.stringify(aman); // "{"first_name":"fname","middle name":"mname","last name":"lname","home address":"hz","phone":"123456"}"
```

---

Array is actually a special object

```js
let arr = [1, 2, 3];
arr.hasOwnProperty(0); // true
arr[6] = 6;
arr; // [1, 2, 3, empty × 3, 6]
Object.keys(arr); // ["0", "1", "2", "6"]
Object.values(arr);
Object.entries(arr);

// `slice()` create a new array reference with the same contents
let arr1 = ["a", "b", "c", "d", "e"];
let arr2 = arr1.slice();
arr1 === arr2; // false
arr2[3] = "c1"
console.log(arr1); // ["a", "b", "c", "d", "e"]
console.log(arr2); // ["a", "b", "c", "c1", "e"]
```

`Object.assign`

```js
let target1 = {a : 1, b : 2};
let target2 = {a : 1, b : 2};
let source1 = {b : 2, c : 3};
let source2 = {b : 5, d : 6};

// Copy properties from each source to the target.
// Note: this WILL MUTATE THE TARGET!
Object.assign(target1, source1, source2);
console.log(target1);
// {a : 1, b : 5, c : 3, d : 6}

// Can be used to safely create copies if the target is a new object:
const newObject = Object.assign({}, target2, source1, source2);

// Result: newObject !== target, and target is unchanged:
console.log(newObject)
// {a : 1, b : 5, c : 3, d : 6}
target1 === newObject; // false

console.log(target2);
// {a : 1, b : 2}

// TODO shallow copy??
```







### `let`, `const`

![:scale 100%, A chart comparing the similarities and differences between const let and var](const-vs-let-vs-var.png )



---

```javascript
var a = 'a';
let b = 'b';
const c = {'c':'c'};

// global scope
window.a // "a"
window.b // undefined
window.c // undefined

// can be reassigned
a = 'a1'; // "a1"
b = 'b1'; // "b1"
c = 'c1'; // Uncaught TypeError: Assignment to constant variable.
c.c = 'd'; // {c: "d"}

// function scope
let fun = function () {
	var i = 1;
	let j = 2;
	const k = 3;
	console.log(i);
	console.log(j);
	console.log(k);
}
fun(); // 1 2 3
console.log(i); // Uncaught ReferenceError: i is not defined
console.log(j); // Uncaught ReferenceError: j is not defined
console.log(k); // Uncaught ReferenceError: k is not defined


// block scope 1
{
	var x = 4;
	let y = 5;
	const z = 6;
}
console.log(x); // 4
console.log(y); // Uncaught ReferenceError: y is not defined
console.log(z); // Uncaught ReferenceError: z is not defined

// block scope 2
for (var v = 1; v < 3; v++) {
	;
}
console.log(v); // 3
for (let l = 1; l < 3; l++) {
	;
}
console.log(l); // Uncaught ReferenceError: l is not defined
```

---

Always define variable as `const`, use `let` unless you know its reference will be changed.

[javascript - What's the difference between using "let" and "var"? - Stack Overflow](https://stackoverflow.com/questions/762011/whats-the-difference-between-using-let-and-var "")



---

### IIFE

[javascript - What does the exclamation mark do before the function? - Stack Overflow](https://stackoverflow.com/questions/3755606/what-does-the-exclamation-mark-do-before-the-function "")



### Symbol



### Function extension

#### Arrow Function (lambda)

```js
function
```

---

#### Default parameter

```js
// Evaluated at call timeSection
function append(value, array = []) {
  array.push(value);
  return array;
}
append(1); //[1]
append(2); //[2], not [1, 2]
```



[Default parameters - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters "")

---



### Object extension

```js
var foo = 'bar';
var baz = {foo};
baz // {foo: "bar"}
```

---



module

* `require` and `import`



### `class`

### decorator



### **Destructuring assignment**

[Destructuring assignment - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment "")

---

### Rest/Spread `...`

[Spread syntax - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax "")

[Rest parameters - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters "")

[tc39/proposal-object-rest-spread: Rest/Spread Properties for ECMAScript](https://github.com/tc39/proposal-object-rest-spread "")

```js
// Rest properties collect the remaining own enumerable property keys that are not already picked off by the destructuring pattern. Those keys and their values are copied onto a new object.
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
x; // 1
y; // 2
z; // { a: 3, b: 4 }

// Spread properties in object initializers copies own enumerable properties from a provided object onto the newly created object.
let n = { x, y, ...z };
n; // { x: 1, y: 2, a: 3, b: 4 }
```



---

### Functional Programming

- **map():** creates a new array with one value for each item in the original array
- **filter():** creates a new array containing only the original values where the callback returned `true`
- **forEach():** doesn't return anything, but lets you do something with each original value
- **reduce():** produces one new value based on the contents of the original array

```js
// map, reduce, filter
const values = [3, 5, 8, 10, 13];

const timesTwo = (num) => num * 2;
const doubledNumbers = values.map(timesTwo);
// [6, 10, 16, 20, 26]


const isEven = (num) => num % 2 === 0;
const evenNumbers = values.filter(isEven);
// [8, 10]


const logValue = (num) => console.log(num);
values.forEach(logValue);
// prints: 3, 5, 8, 10, 13


const addNumbers = (lastResult, currentValue) => {
    return lastResult + currentValue;
}
const sum = values.reduce(addNumbers, 0);
// 39
```

#### Pure Function

* It returns the same result if given the same arguments
* It does not cause any observable side effects



#### Immutability

#### First-class Entity

Functions as first-class entities can:

- refer to it from constants and variables
- pass it as a parameter to other functions
- return it as result from other functions

[Functional Programming Principles in Javascript](https://www.freecodecamp.org/news/functional-programming-principles-in-javascript-1b8fc6c3563f/ "")

#### `map`, `reduce`, `filter` Javascript Array Methods

```js
const numbers = [2, 4, 8, 10];
const halves = numbers.map(x => x / 2);
// halves is [1, 2, 4, 5]

const words = ["spray", "limit", "elite", "exuberant", "destruction", "present"];
const longWords = words.filter(word => word.length > 6);
// longWords is ["exuberant", "destruction", "present"]

const total = [0, 1, 2, 3].reduce((sum, value) => sum + value, 1);
// total is 7

const compose = (...fns) => x => fns.reduceRight((v, f) => f(v), x);
const add1 = n => n + 1;
const double = n => n * 2;
const add1ThenDouble = compose(
  double,
  add1
);
add1ThenDouble(2); // 6
// ((2 + 1 = 3) * 2 = 6)
```

[JavaScript Functional Programming — map, filter and reduce](https://medium.com/jsguru/javascript-functional-programming-map-filter-and-reduce-846ff9ba492d "")

[Simplify your JavaScript – Use .map(), .reduce(), and .filter()](https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d "")

---



### Module

#### CommonJS

---

#### ES6 Module



`export`

```javascript
// circle.js
const PI = 3.14;
const function circle_area(r) {
    return PI * r * r;
}
export {PI, circle_area}

export default const function(r) { // only one default export
    return 2 * PI * r;
}
```



`import`

```javascript
import length, {PI, circle_area as area} from './circle';
PI;
circle_area(2);
length(2);

import React, {Component, PropTypes} from 'react';
```

---

## Runtime Support

```shell
npm install -g es-checker
es-checker
```

---



## Debug Tricks

```js
console.info("output variable", window.Date());

```



# HTML5 and CSS



## CSS 



## Font





# Node.js



## npm (Node Package Manager)

`npm` or `yarn`

```shell
#Starting a new project
npm init === yarn init      

 #Installing all the dependencies of project
npm install === yarn or yarn install    

#Adding a dependency
npm install [package] === yarn add [package] #The  package is saved to your package.json immediately.      
npm install  [package]@[version] === yarn add [package]@[version]
npm install [package]@[tag] === yarn add [package]@[tag]

#Add a dev dependency
npm install [package] --save-dev === yarn add [package] --dev

#Upgrading a dependency
npm update [package] === yarn upgrade [package]
npm update [package]@[version] === yarn upgrade [package]@[version]
npm update [package]@[tag] === yarn upgrade [package]@[tag]

#Removing a dependency
npm uninstall [package] === yarn remove [package]

#View registry information
npm view [package] === yarn info [package]

#List installed packages
npm list === yarn list
npm list --depth === yarn list --depth=0

#Install packages globally
npm install -g [package] === yarn global addb [package]

#Run a defined package script
npm run [script] === yarn run [script]
```

[NPM vs Yarn Cheat Sheet – Red Shift](https://shift.infinite.red/npm-vs-yarn-cheat-sheet-8755b092e5cc?gi=bd42fb41317b "")



### package.json

Difference between run in command line and run script in `package.json`?

---

## npx (Node Package Executor ??)

[npx  -  npm](https://www.npmjs.com/package/npx "")

[Introducing npx: an npm package runner – Kat Marchán – Medium](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b "")

[javascript - Difference between npx and npm? - Stack Overflow](https://stackoverflow.com/questions/50605219/difference-between-npx-and-npm "")

---

## [Babel](https://babeljs.io/ "")

**A transpiler that can convert ES6 code to ES5 code.**

[Babel · Online REPL](https://babeljs.io/repl "")

[Plugins · Babel](https://babeljs.io/docs/en/plugins/ "")

[babel-preset - npm search](https://www.npmjs.com/search?q=babel-preset "")

```shell
npm install --save-dev babel-preset-latest
npm install --save-dev babel-preset-react

npm install --save-dev babel-preset-stage-0
npm install --save-dev babel-preset-stage-1
npm install --save-dev babel-preset-stage-2
npm install --save-dev babel-preset-stage-3
```

---

`.babelrc`

```javascript
{
  "presets": [
    "es2015",
    "react",
    "stage-0"
  ],
  "plugins": []
}
```

```shell
npm install --global babel-cli
babel example.js --out-file compiled.js
npm install --global babel-cli
babel-node // ES6 REPL
```



---

### babel-polyfill

> A polyfill is a piece of code (usually JavaScript on the Web) used to provide modern functionality on older browsers that do not natively support it.
>
> [Polyfill - MDN Web Docs Glossary: Definitions of Web-related terms | MDN](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill "")

---

Support new API:

Iterator, Generator, Set, Maps, Proxy, Reflect, Symbol, Promise, Object.assign

[@babel/polyfill · Babel](https://babeljs.io/docs/en/babel-polyfill "")

```javascript
import 'babel-polyfill'
// or
require('babel-polyfill')
```

---



## Webpack

### Concepts

* Entry

```js
module.exports = {
  entry: {
    app: './src/app.js',
    adminApp: './src/adminApp.js'
  }
};
```



* Output

there can be multiple `entry` points, only one `output` configuration is specified.

```js
module.exports = {
  entry: {
    app: './src/app.js',
    search: './src/search.js'
  },
  output: {
    filename: '[name].js',
    path: __dirname + '/dist'
  }
};
```

```js
module.exports = {
  //...
  output: {
    path: '/home/proj/cdn/assets/[hash]',
    publicPath: 'https://cdn.example.com/assets/[hash]/'
  }
};
```



* Plugin
* Module



#### CSS processing

* sass-loader
* postcss-loader
* css-loader
* style-loader

TODO ExtractTextPlugin("bundle.css")

DefinePlugin

HtmlWebpackPlugin



---

### Hot Module Replacement

[Hot Module Replacement](https://webpack.js.org/concepts/hot-module-replacement "")

> Hot Module Replacement (HMR) exchanges, adds, or removes modules while an application is running, without a full reload.





## ESLint

`eslint --init`



---



# React



## JSX

HTML tag must be lower-case

React component must be capitalized



## `props` and `state`

### `props`

Read: `this.props`



`props.children` : [Composition vs Inheritance – React](https://reactjs.org/docs/composition-vs-inheritance.html "")

```jsx
function FancyBorder(props) {
  return (
    <div className={'FancyBorder FancyBorder-' + props.color}>
      {props.children}
    </div>
  );
}

function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        Welcome
      </h1>
      <p className="Dialog-message">
        Thank you for visiting our spacecraft!
      </p>
    </FancyBorder>
  );
}
```

[A quick intro to React’s props.children – codeburst](https://codeburst.io/a-quick-intro-to-reacts-props-children-cb3d2fce4891 "")

### `state`

Read: `this.state.variable`

Write: `this.setState()`



---

## VirtualDOM

## Life Cycle

```graphviz
digraph {
    start [shape=circle label=< > width=0.5 style=filled]
    pkgjson [label=<package.json> shape=box]
    pkglock [label=<package-lock.json<br/>package.json> shape=box]
    pkgshrink [label=<npm-shrinkwrap.json<br/>package.json> shape=box]
    yarn [label=<yarn-lock.json<br/>package.json> shape=box]

    start -> pkgjson [label=<npm init -y> labelfontcolor="red"]
    pkgjson -> yarn [label=<yarn add pkg>]
    pkgjson -> pkglock [label=<npm install>]
    pkglock -> pkgshrink [label=<npm shrinkwrap>]
}
```

---

![React Life Cycle Process Image](react_life_cycle_process.jpg )

---

![React setState() correct usage](react_setstate_usage.png )

---

[ReactJs component lifecycle methods — A deep dive – Hacker Noon](https://hackernoon.com/reactjs-component-lifecycle-methods-a-deep-dive-38275d9d13c0 "")

![:scale 100%](react_life_cycle.png)

---

---

## Data Flow

[What Does Redux Do? (and when should you use it?)](https://daveceddia.com/what-does-redux-do/ "") ✔✔✔✔

[How Redux Works: A Counter-Example ](https://daveceddia.com/how-does-redux-work/ "") ✔✔✔✔



![:scale 100%, ](why_use_store.png)

---

![:scale 100%, Flux Pattern](flux_pattern.jpg)

---

![:scale 100%, Redux Pattern](redux_pattern.jpg)

---

![:scale 100%, Flux Versus Redux](flux_vs_redux.jpg)

---

![:scale 100%, Flux Versus Redux](flux_vs_redux_2.png)



这一部分可以参考 [自述 · GitBook](http://cn.redux.js.org/index.html "")

```js


import { createStore } from 'redux'

/**
 * 这是一个 reducer，形式为 (state, action) => state 的纯函数。
 * 描述了 action 如何把 state 转变成下一个 state。
 *
 * state 的形式取决于你，可以是基本类型、数组、对象、
 * 甚至是 Immutable.js 生成的数据结构。惟一的要点是
 * 当 state 变化时需要返回全新的对象，而不是修改传入的参数。
 *
 * 下面例子使用 `switch` 语句和字符串来做判断，但你可以写帮助类(helper)
 * 根据不同的约定（如方法映射）来判断，只要适用你的项目即可。
 */
function counter(state = 0, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

// 创建 Redux store 来存放应用的状态。
// API 是 { subscribe, dispatch, getState }。
let store = createStore(counter)

// 可以手动订阅更新，也可以事件绑定到视图层。
store.subscribe(() => console.log(store.getState()))

// 改变内部 state 惟一方法是 dispatch 一个 action。
// action 可以被序列化，用日记记录和储存下来，后期还可以以回放的方式执行
store.dispatch({ type: 'INCREMENT' })
// 1
store.dispatch({ type: 'INCREMENT' })
// 2
store.dispatch({ type: 'DECREMENT' })
// 1
```



Action

* action creator

Reducer

* `(old_state, action) => new_state`
* should be pure function, return new object instead of modifing old object
* design your own state tree, don't nest too deep

Dispatcher

Middleware

Store Enhancer



---



---

## fetch and thunk

![:scale 100%](redux_thunk_1.gif)

---

![:scale 100%](redux_thunk_2.png)

---

![:scale 100%](redux_data_flow.png)

---

[淺談 Redux Thunk](https://www.slideshare.net/ssuserc4dc6d1/redux-thunk "")

[[ Part 3 ] First Async call, redux-thunk](http://dev.basharallabadi.com/2018/09/part-3-first-async-call-redux-thunk.html "")

[Quick Start · React Redux](https://react-redux.js.org/introduction/quick-start "")

---

## Usual Component

### IntlProvider

`window.Intl`



### Provider

store

### DragNDrop

HTML5 Drag and Drop





# Component Showcase



# Debug Tools

## Chrome Developer Tools

* Elements DOM, CSS
* Console `console.info("variable name: ", var);`
* Network, check cache
* Souce debug with break point

## Fiddler



## BrowserSync  ??

[Browsersync - Time-saving synchronised browser testing](https://www.browsersync.io/ "")



# Reference

## Handy Tools

React Developer Tools: [facebook/react-devtools: An extension that allows inspection of React component hierarchy in the Chrome and Firefox Developer Tools.](https://github.com/facebook/react-devtools "")

Alternative method: bind store to window object



Redux DevTools: [zalmoxisus/redux-devtools-extension: Redux DevTools extension.](https://github.com/zalmoxisus/redux-devtools-extension "")

React Performance Devtool: [nitin42/react-perf-devtool: A browser developer tool extension to inspect performance of React components.](https://github.com/nitin42/react-perf-devtool "")

---

## ECMAScript

[JavaScript for Java Developers -- Mark Erikson](https://blog.isquaredsoftware.com/presentations/2019-05-js-for-java-devs/#/ "")

 [JavaScript 教程 - 阮一峰](https://wangdoc.com/javascript/ "") （ECMAScript 5）

[ruanyf/es6tutorial: 《ECMAScript 6入门》](https://github.com/ruanyf/es6tutorial "")

---

## React & Redux

[深入浅出React和Redux (豆瓣)](https://book.douban.com/subject/27033213/ "")

[深入浅出React和Redux (实战)-Kindle商店-亚马逊中国](https://www.amazon.cn/mn/detailApp/ref=asc_df_B071F89KXV1558664999000/?asin=B071F89KXV&tag=douban_kindle-23&creative=2384&creativeASIN=B071F89KXV&linkCode=df0 "")

[深入React技术栈-图书-图灵社区](http://www.ituring.com.cn/book/1898 "")

[Redux 中文文档 · GitBook](http://cn.redux.js.org/index.html "")，推荐

* [Action](http://cn.redux.js.org/docs/basics/Actions.html "")

Slides By Mark: [Intro to React and Redux](https://blog.isquaredsoftware.com/presentations/2018-03-redux-fundamentals/#/ "")



---

## Webpack

[Foreword](https://survivejs.com/webpack/foreword/ "")





# 其它

[    How to learn React.js in 2019 - RWieruch  ](https://www.robinwieruch.de/learn-react-js/ "")

[ReactJS Tutorial - TutorialsPoint](https://www.tutorialspoint.com/reactjs/ "")

[How to Learn React — A roadmap from beginner to advanced](https://www.freecodecamp.org/news/learning-react-roadmap-from-scratch-to-advanced-bff7735531b6/ "")

[React Redux Tutorial for Beginners: The Definitive Guide (2019)](https://www.valentinog.com/blog/redux/ "")

[React Tutorial: Introduction | Build with React JS](http://buildwithreact.com/tutorial "")，小专题教程，带练习

[Intro to React and Redux](https://blog.isquaredsoftware.com/presentations/2018-03-redux-fundamentals/#/ "")， Redux维护者的PPT，讲解很清晰，动图很有启发性，推荐

* 相关的Slides： [     Reactathon Presentation: Redux Fundamentals ·  Mark's Dev Blog  ](https://blog.isquaredsoftware.com/2018/03/presentation-reactathon-redux-fundamentals/ "")



