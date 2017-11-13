# ES6 New Features #

## Let and Const ##
* Let replaces var in es6 in term of variable assignment. Let also allows for block scoping, in contrast to var.
* Const declares variables that cannot be re-assigned. Constants also allow for block scoping along with ‘let.’

## Template Literals ##
Template literals, created by a pair of back-ticks, allow for embedded-expressions using the dollar-sign and a pair of curly braces: \`${...}\`

## Operating and Destructuring  Assignment ##
**Spread Operator** as an interpolation operator for an array:

>let a = [2, 3, 4];

>let b = [1, ...a, 5, 6];

>Output: 1,2,3,4,5,6

**Spread Operator** as a rest parameter:
>function collect(...a){

>  console.log(a); // Output 1,2,3,4,5

>}

>collect(1,2,3,4,5);

Function that requires multiple parameter could use spread operator, it will concat the parameters to form an array.

**Destructuring  Assignment** for array:
>let array = [1,2,3,4];

>let [one, two] = array;

>console.log(one,two); Output: 1,2

**Destructuring  Assignment** for Object:

>let obj = {name: 'bilal', lang: 'JS'};

>let {name, lang} = obj;

>//**OR** let name,lang;

>//({name,lang}) = obj //else {} they will be treated as a code block and result error

>console.log(name,lang); Output bilal JS

Name of string need to be same as Object's properties. So properties will be assigned to these variables.

## Arrow Functions ##
These functions doesn't create this object on their own to refer to. Instead they refer to parent's scope and they don't have their own scope.
**As an anonymous functions**
>setTimeout(() => {

>  console.log("Hello from arrow function");

>},2000);

**Identifier for Arrow functions**
>let mul = (x,y) => {

>  console.log(x*y);

>}

>mul(5,6);

To return some short expressions like `x*y` we just remove braces *{}* and omit return keyword. Expression after arrow will be returned.
## Helper methods in ES6 ##
### map() ###

The method creates a new array with the results of calling a provided function on every element in the calling array.
>let arr=[10,20,30];

>let d_arr = arr.map((n) => n*2);

>console.log(d_arr);

### filter() ###

The filter() method creates a new array with all elements that pass the test implemented by the provided function.

>let arr=[10,20,30,50,70];

>let d_arr = arr.filter((n) => n>30);

>console.log(d_arr);

### String helper: repeat() ###

>let str = `hell${"o".repeat(10)}` + " world!".repeat(2);

>console.log(str);

### String helper: search ###
**startsWith**
>let str = "butterfly".startsWith("butter"); //return true

**endsWith**
>let str = "butterfly".endsWith("butter"); //return true

**includes**
>let str = "butterfly".includes("er"); //return true

* Number type checking can occur through the Number.isFinite method.

* Number safety checking can occur through the Number.isSafeInteger method.

## Modules in JS ##
These are reusable piece of code which we want to interact with in other parts of our application. We export such code chunks like primitive values or functions then we import them on the other end.

> File1.js

>const arr = [10,20,30];

> const add = (a,b) => a+b;

> export {arr, add};

> **Or we can set default export** export default add;

>File2.js

> import {add, arr} from './File1';

> **Or import default one** import add from './File1'

## Classes and Prototype difference##
<https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9>
* A class is like a blueprint — a description of the object to be created. Classes inherit from classes and create subclass relationships: hierarchical class taxonomies.
* Instances are typically instantiated via constructor functions with the `new` keyword.
* JS supports prototypal inheritance model.
* Means Classes in JS are extraction of prototypes.

## Prototype ##
>function Vehicle(make, year) {

>  this.make = make;

>  this.year = year;

>}

>Vehicle.prototype.color;

>Vehicle.prototype.bio = function() {

>  return `A ${this.color} ${this.make} made in ${this.year}.`;

>};

>let s = new Vehicle("Tesla", 2017);

>s.color = "black";

## SETS ##
Data structure that contains non-repeated set of values.

> let a= new Set();

> a.add(5);

> a.add("hello");

> a.add({x:"hello",y:5});

> console.log(a);

> console.log(a.size);

> console.log(a.has("hello"));

--------------------
>let numbers = [5,7,8,3,2];

>let numSet= new Set(numbers);

>for(let element of numSet.values()){

>	console.log(element);

>}
//OR

>let arr=numSet.values();

>for(value of arr){

>console.log(value);

>}
