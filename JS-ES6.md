# ES6 New Features #

## Let and Const ##
* Let replaces var in es6 in term of variable assignment. Let also allows for block scoping, in contrast to var.
* Const declares variables that cannot be re-assigned. Constants also allow for block scoping along with ‘let.’

## Template Literals ##
Template literals, created by a pair of back-ticks, allow for embedded-expressions using the dollar-sign and a pair of curly braces: \`${...}\`

## Operating and Destructuring  Assignment ##
**Spread Operator** as an interpolation operator for an array:
```
let a = [2, 3, 4];
let b = [1, ...a, 5, 6];
Output: 1,2,3,4,5,6
```
**Spread Operator** as a rest parameter:
```
function collect(...a){
  console.log(a); // Output 1,2,3,4,5
}
collect(1,2,3,4,5);
```
Function that requires multiple parameter could use spread operator, it will concat the parameters to form an array.

**Destructuring  Assignment** for array:
```
let array = [1,2,3,4];
let [one, two] = array;
console.log(one,two); Output: 1,2
```
**Destructuring  Assignment** for Object:
```
let obj = {name: 'bilal', lang: 'JS'};
let {name, lang} = obj;
//**OR** let name,lang;
//({name,lang}) = obj //else {} they will betreated as a code block and result error

console.log(name,lang); Output bilal JS
```
Name of string need to be same as Object's properties. So properties will be assigned to these variables.

## Arrow Functions ##
These functions doesn't create this object on their own to refer to. Instead they refer to parent's scope and they don't have their own scope.
**As an anonymous functions**
```
setTimeout(() => {
  console.log("Hello from arrow function");
},2000);
```
**Identifier for Arrow functions**
```
let mul = (x,y) => {
  console.log(x*y);
}
mul(5,6);
```
To return some short expressions like `x*y` we just remove braces *{}* and omit return keyword. Expression after arrow will be returned.
## Helper methods in ES6 ##
### map() ###

The method creates a new array with the results of calling a provided function on every element in the calling array.
```
let arr=[10,20,30];
let d_arr = arr.map((n) => n*2);
console.log(d_arr);
```
### filter() ###

The filter() method creates a new array with all elements that pass the test implemented by the provided function.
```
let arr=[10,20,30,50,70];
let d_arr = arr.filter((n) => n>30);
console.log(d_arr);
```
### String helper: repeat() ###
```
let str = `hell${"o".repeat(10)}` + " world!".repeat(2);
console.log(str);
```
### String helper: search ###
**startsWith**

```
let str = "butterfly".startsWith("butter"); //return true

```
**endsWith**

```
let str = "butterfly".endsWith("butter"); //return true
```

**includes**

```
let str = "butterfly".includes("er"); //return true
```

* Number type checking can occur through the Number.isFinite method.

* Number safety checking can occur through the Number.isSafeInteger method.

## Modules in JS ##
These are reusable piece of code which we want to interact with in other parts of our application. We export such code chunks like primitive values or functions then we import them on the other end.

```
 File1.js
const arr = [10,20,30];
 const add = (a,b) => a+b;
 export {arr, add};
```
> **Or we can set default export** export default add;

>File2.js

``` import {add, arr} from './File1';```

> **Or import default one** import add from './File1'

## Classes and Prototype difference##
<https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9>
* A class is like a blueprint — a description of the object to be created. Classes inherit from classes and create subclass relationships: hierarchical class taxonomies.
* Instances are typically instantiated via constructor functions with the `new` keyword.
* JS supports prototypal inheritance model.
* Means Classes in JS are extraction of prototypes.

## Prototype ##
```
function Vehicle(make, year) {
  this.make = make;
  this.year = year;
}


Vehicle.prototype.bio = function() {
  return `A ${this.color} ${this.make} made in ${this.year}.`;
};

let s = new Vehicle("Tesla", 2017);

s.color = "black";
```
## SETS ##
Data structure that contains non-repeated set of values.
```
 let a= new Set();
 a.add(5);
 a.add("hello");
 a.add({x:"hello",y:5});
 console.log(a);
 console.log(a.size);
 console.log(a.has("hello"));
```
--------------------
```
let numbers = [5,7,8,3,2];
let numSet= new Set(numbers);
for(let element of numSet.values()){
	console.log(element);
}//OR

let arr=numSet.values();
for(value of arr){
console.log(value);
}
```
## MAPS ##
The Map object holds key-value pairs. Any value (both objects and primitive values) may be used as either a key or a value
```
let m = new Map();
let str = "new string";
let obj = {a : "one", b: "two"};
let func = () => {console.log("Hello")};
m.set(str,"return value for string key");
m.set(obj,"return value for object key");
m.set(func,"return value for function key");

for (let [key,value] of m.entries()){
  console.log(\`${key} is pointing to ${value}\`);
}
console.log(m.get(obj));
```
<https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map>

## CLOSURE ##
A closure is the combination of a function and the lexical environment within which that function was declared.
* Closures in JavaScript and ES6 refer to functions that remember their creation environment and can further reference that environment’s independent variables.
* Lexical scoping refers to the JavaScript concept of programs keeping track of variable locations to understand in which scopes they can be accessed.
* Function factories create functions based on returning inner functions that manipulate its own arguments and the arguments of the outer function.
* Data encapsulation and private methods don’t exist natively in JavaScript but can be emulated with closures for data restriction and limited access.

**Basic Closure**
```
let call = () => {
	let secret = "Its a secret variable";
  let reveal = () => {
  	console.log(secret);
  }
  reveal();
}
call();
```
**Lexical Scoping**
```
let call = () => {
	let secret = "Its a secret variable";  
  let reveal = () => {
  	console.log(secret);
  }
  return reveal;
}

let unveil = call();
unveil();
```
In other programming languages and usually once a function finished execution the local variables are then inaccessible. So as per those standards variable ***secret*** is inaccessible, but not in the case of JS!

**Function Factories**
```
let product = (x) => {
  let m = (y) => {
  	return x * y;
  }
  return m;
}
let mul = product(5);
console.log(mul(3));
```
*OR the Shorter Version*

```
let product = (x) => (y) => x * y;
let mul = product(5);
console.log(mul(3));
```

**Private Methods**

```
const budget = () => {
	let balance = 0;
  let changeBal = (val) => {
  	return balance += val;
  }
  const deposit20 = () => changeBal(20);
  const check = () => balance;

  return {
  	deposit20: deposit20,
   check: check
  }
}
let newAccount = budget();
newAccount.deposit20(); //Since deposit20 key holds a function so we call it as a function
console.log(newAccount.check());
```
## Generators ##
* Generators break the typical “run to completion” model of normal functions and can start, pause, and reset.
* Generators use the syntax of a normal function, but have an asterisk following the function keyword: function* generator { … } .
* The generator yield keyword signals when to ‘pause’ the function and return its current state.
* Generator instances don’t use the new keyword like the typical function prototype or Object.
* Using the generator’s special next() method allows us to access its yielded state.
* Passing values to the next() method introduces a way for generators to reset, or complete their runtime.
* An iterator in JavaScript demonstrates a type of object that can access values in a collection one at a time.
* A generatorcan provide a convenient and complex alternative to iterators.
```
function* countMaker() {
  let count = 0;    while(count < 3)
  	yield count += 1;
}
let countGen = countMaker();
console.log(countGen.next().value);
console.log(countGen.next().value);
console.log(countGen.next().value);
```
**Reset the Generators**

```
function* countMaker() {
  let count = 0;  
  while(true){
  	count += 1;
    let reset = yield count;
    if(reset){
    	count = 0;
    }
  }  	
}

let countGen = countMaker();
console.log(countGen.next().value);
console.log(countGen.next().value);
console.log(countGen.next(true).value);
console.log(countGen.next().value);
```
**Iterator vs Generator**

```
/* Iterator

function arrayIterator(array) {
  let index = 0;
  return {
    next: () => {
      if(index < array.length){
        let next = array[index];
        index += 1;
        return next;
      }
    }

  }
}

let it = arrayIterator([1,2,3]);
console.log(it.next());
console.log(it.next());
console.log(it.next());
*/
function* arrayIterator() {
 	/*
		for (let elem of arguments){
	    yield elem;
	  }
    */    

    yield* arguments;
}  

let it = arrayIterator(1,2,3);
console.log(it.next().value);
console.log(it.next().value);
console.log(it.next().value);
```
