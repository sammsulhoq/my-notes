# WDS
## _JavaScript, Basics_

[[WebDevSimplified]](https://courses.webdevsimplified.com/view/courses/javascript-simplified-beginner/521730-mindset/1510481-01-course-introduction)

JavaScript is a programming language that runs on browser using JS engine(Firefox: SpiderMonkey, Chrome: V8) available in all major browsers. Brial Doll used C++ to embed the Chrome's V8 engine and made it available for server-side implementation. This server-side version is called **Node**

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

> Interestingly, if we compare `undefined` and `null` you will get true. For example: `undefined == null` returns `true`, which makes sense since both lack values.

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