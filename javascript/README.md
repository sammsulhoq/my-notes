# WDS
## _JavaScript, Basics_

[[WebDevSimplified]](https://courses.webdevsimplified.com/view/courses/javascript-simplified-beginner/521730-mindset/1510481-01-course-introduction)

JavaScript is a programming language that runs on browser using JS engine(Firefox: SpiderMonkey, Chrome: V8) available in all major browsers. Brial Doll used C++ to embed the Chrome's V8 engine and made it available for server-side implementation. This server-side version is called **Node**

## Hoisting [>>](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
JavaScript Hoisting refers to the process whereby the interpreter appears to move the declaration of functions, variables, classes, or imports to the top of their scope, prior to execution of the code.

Note: Arrow functions defined after invoke, it won't be hoisted.

In colloquial terms, any of the following behaviors may be regarded as hoisting:

1. Being able to use a variable's value in its scope before the line it is declared. ("Value hoisting")
2. Being able to reference a variable in its scope before the line it is declared, without throwing a ReferenceError, but the value is always undefined. ("Declaration hoisting")
3. The declaration of the variable causes behavior changes in its scope before the line in which it is declared.
4. The side effects of a declaration are produced before evaluating the rest of the code that contains it.

The four function declarations above are hoisted with type 1 behavior; var declaration is hoisted with type 2 behavior; let, const, and class declarations (also collectively called lexical declarations) are hoisted with type 3 behavior; import declarations are hoisted with type 1 and type 4 behavior.

## Scope [>>](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

The scope is the current context of execution in which values and expressions are "visible" or can be referenced. If a variable or expression is not in the current scope, it will not be available for use. Scopes can also be layered in a hierarchy, so that child scopes have access to parent scopes, but not vice versa.

JavaScript has the following kinds of scopes:

1. Global scope: The default scope for all code running in script mode.
2. Module scope: The scope for code running in module mode.
3. Function scope: The scope created with a function.

In addition, variables declared with let or const can belong to an additional scope:

4. Block scope: The scope created with a pair of curly braces (a block).
```
{
  var x = 1;
}
console.log(x); // 1
```

## Closures [>>](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)

A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function's scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

```
function makeFunc() {
  const name = "Mozilla";
  function displayName() {
    console.log(name);
  }
  return displayName;
}

const myFunc = makeFunc();
myFunc();
```

## Garbage Collection
Like other programming languages, JS also deploys mechanisms to ensure that the allocated computer memory is freed so that it is not bloated with unused memory allocation. So, while the programming is executing, JS checks which variable is no longer used and it de-allocates that memory. [Read More](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_management)

## Comments
In JS, if we want to write some annotations or some plaintext which be more of information to the developer, then we use `//` or `/* ... */` to specify those things.

`//` - Single line comment
`/* */` - Multiple line comment

## Variables

There are three types of variables that can be created in JS:
- var : This creates a variable having global scope. It's value can be changed.
- let: This creates a variables having scope bound within the block it has been declared. It's value can be changed within the given scope.
- const: Created a variable whose value cannot be changed.

## DataTypes
There are 8 primitive data types available in JS:
* null
* undefined
* boolean
* number
* bigint
* string
* symbol

_Number_: A variable defined in JS with a numerical value is of type **number** always.
```
let a = 1
let b = 2.3
console.log(typeof a)       // number
console.log(typeof b)       // number
```

_String_: A variable defined in JS within single (') or double-quotes ("") is considered a string.
```
let name = 'Sammsul Hoque Choudhary'
let location = "India"
console.log(typeof name)    // string
console.log(typeof location)        // string
```

_Boolean_: A variable defined in JS with either `true` or `false` value is considered boolean.
```
let isColdToday = true
console.log(typeof isColdToday)        // true
```
If more than one boolean expression is checked, the order of execution goes from left-to-right
```
console.log(false && false || true)     // true
```

_Null_: A variable with no value is usually designated with value as **null**. PLEASE NOTE: If you check type of such variable it will return _object_.
```
let item = null
console.log(item)       // object
```

_Undefined_: An item which is not available yet, or a variable which is given a value of 'undefined', returns `undefined`.
```
let x = undefined
let name = { firstName: 'Sammsul Hoque' }
console.log(x)      // undefined
console.log(name.age)       // undefined
```

## Variable Comparison
In JS we have `>`, `<`, `>=`, `<=`, `==` and `!=` which are commonly used. But, we also have two more comparison operators `===` and `!==` which not only compares the value of the variables but also check the variable types.

Use the following link to know the comparison of commonly used expression:
https://dorey.github.io/JavaScript-Equality-Table/

> Interestingly, if we compare `undefined` and `null` you will get true. For example: `undefined == null` returns `true`, which makes sense since both lack values.

## Type Coercion [>>](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion)
Type coercion is the automatic or implicit conversion of values from one data type to another (such as strings to numbers).
```
const value1 = "5";
const value2 = 9;
let sum = value1 + value2;

console.log(sum);
```
In the above example, JavaScript has coerced the 9 from a number into a string and then concatenated the two values together, resulting in a string of `59`

## Type Conversion [>>](https://developer.mozilla.org/en-US/docs/Glossary/Type_Conversion)

Type conversion (or typecasting) means transfer of data from one data type to another. Implicit conversion happens when the compiler (for compiled languages) or runtime (for script languages like JavaScript) automatically converts data types. The source code can also explicitly require a conversion to take place.
[Check out this](https://www.freecodecamp.org/news/js-type-coercion-explained-27ba3d9a2839/)

## Functions
In JS, if we want to reuse a block of statements to be used later, we wrap then using `function`. 

```
function <functionName> (listOfArguments) {
    /// reusable logic goes here
}
```
The way of writing the function as above is called `declaring/defining a function`. If we want to see the results of the function, we need to execute it, which is also called `calling a function`. 
```
<functionName>(listOfParamters)
```
In JS, the list of parameters is mapped to the list of arguments defined in the function definition. It is mapped from left-to-right. So, if we don't pass all the parameters, JS will set the remaining ones as `undefined`
```
function user(name, age) {
    console.log(name)
    console.log(age)
}

user("Sammsul Hoq")     // Output: Sammsul Hoq, undefined
```

## Passing Functions As Arguments
When we pass a function to another function as an *argument*, it is called **callback** function. Please note, when we pass function as argument, we just pass the name and we *do not call* it.

#### Why?
Most of the time we are creating programs and applications that operate in a synchronous manner. In other words, some of our operations are started only after the preceding ones have completed. Often when we request data from other sources, such as an external API, we don’t always know when our data will be served back. In these instances we want to wait for the response, but we don’t always want our entire application grinding to a halt while our data is being fetched. These situations are where callback functions come in handy.

```
function <callback_func_def> () {}

function <main_function> (possible_list_of_args, <callback_func_as_arg>) {
    callback_func_as_arg()
}

main_function(callback_func_def)
```
#### What Are Higher Order Functions? [>>](https://www.freecodecamp.org/news/higher-order-functions-in-javascript-explained/#:~:text=Higher%20order%20functions%20are%20functions,use%20them%20in%20practical%20applications.)
> A function that takes one or more functions as arguments, or returns a function as its result. Following is the setup of Higher Order Function

```
// Referencing above example
function <main_function> (possible_list_of_args, <callback_func_as_arg>) {
    callback_func_as_arg()
}

// While calling the main function, we will have callback
main_function(paramenters, function () {
    // statment goes here
})
```
#### What is an Anonymous Function?
> An anonymous function in JavaScript is a function that has no name, or more precisely, one that lacks a name. Like the one we saw in alternative situation above.

#### Pure Functions [>>](https://www.geeksforgeeks.org/pure-functions-in-javascript/)
> A Pure Function is a function (a block of code) that always returns the same result if the same arguments are passed. It does not depend on any state or data change during a program's execution. Rather, it only depends on its input arguments. The below example will always return same result for the given 'productPrice' value.

```
function calculateGST(productPrice) {
	return productPrice * 0.05;
}
console.log(calculateGST(15))
```
#### Impure Functions [>>](https://www.geeksforgeeks.org/pure-functions-in-javascript/)
> An Impure Function is a function that doesn't returns the same result if the same arguments are passed. This happens when the function in question depends on other variables outside it's scope. following is an exmaple of impure function where the calculation depends on the value of 'tax' and that might change. So, for a given input the output will vary.

```
let tax = 20;
function calculateGST(productPrice) {
	return productPrice * (tax / 100) + productPrice;
}
console.log(calculateGST(15))
```

## Arrow Functions
ES6 defined a new way of defining the function where we assign a function to a variable name.
```
let <func_name> = (list_of_possible_args) => {
    // statements
}
```
If there is a single line in the scope of arrow function, then we can omit the *curly braces*
```
let <func_name> = (list_of_possible_args) => // single_statment
```

## Immediately Invoke Function Expression (IIFE) [>>](https://www.udacity.com/blog/2023/03/immediately-invoked-function-expressions-iife-in-javascript.html)
When we define a function and invoke it at the same place. 
To create the IIFE, we first create the function declaration: functionName(). Then, once the function is defined, we:

1. Wrap parentheses around it. This creates the function expression
2. Add a second pair of parentheses at the end to immediately invoke it

Based on what we have learnt so far, we have three ways of doing this:

```
(function functionName() {
 // function logic
}());

(function () {
 // function logic
})();

(() => {
    // function logic
})();
```

## Arrays [>>](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
The Array object, as with arrays in other programming languages, enables storing a collection of multiple items under a single variable name, and has members for performing common array operations.
Array objects cannot use arbitrary strings as element indexes (as in an associative array) but must use nonnegative integers (or their respective string form).
```
console.log(years["2"] !== years["02"]);
```
Only years['2'] is an actual array index. years['02'] is an arbitrary string property that will not be visited in array iteration.

## Shallow Copy [>>](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy)
 shallow copy of an object is a copy whose properties share the same references (point to the same underlying values) as those of the source object from which the copy was made. As a result, when you change either the source or the copy, you may also cause the other object to change too. That behavior contrasts with the behavior of a deep copy, in which the source and copy are completely independent.
 More formally, two objects o1 and o2 are shallow copies if:

1. They are not the same object (o1 !== o2).
2. The properties of o1 and o2 have the same names in the same order.
3. The values of their properties are equal.
    Their prototype chains are equal.

## Deep Copy [>>](https://developer.mozilla.org/en-US/docs/Glossary/Deep_copy)
 A deep copy of an object is a copy whose properties do not share the same references (point to the same underlying values) as those of the source object from which the copy was made. As a result, when you change either the source or the copy, you can be assured you're not causing the other object to change too. That behavior contrasts with the behavior of a shallow copy, in which changes to nested properties in the source or the copy may cause the other object to change too.

Two objects o1 and o2 are structurally equivalent if their observed behaviors are the same. These behaviors include:

1. The properties of o1 and o2 have the same names in the same order.
2. The values of their properties are structurally equivalent.
3. Their prototype chains are structurally equivalent (although when we deal with structural equivalence, these objects are usually plain objects, meaning they both inherit from Object.prototype).

## Object [>>](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)
An object is a collection of related data and/or functionality. These usually consist of several variables and functions (which are called properties and methods when they are inside objects).
```
const person = {
  name: ["Bob", "Smith"],
  age: 32,
  bio: function () {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  introduceSelf: function () {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};
```
Following are two more ways to define function in the objects:
```
const person = {
  name: ["Bob", "Smith"],
  age: 32,
  bio () {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  introduceSelf = () => {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};
```
