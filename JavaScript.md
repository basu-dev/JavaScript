# JavaScript Basics and Core Concepts

## 1. Execution Context And Call Stack

> When JavaScript Engine comes across a JS file, it creates execution context.
> What does an exection context mean? Execution context consists of two process

1. Memory Allocation
2. Execution of Code

#### I. Memory Allocation

> During memory allocation JavaScript Engine scans whole JS file to all identifiers and
> functions and allocate memory for them in `key value pair`. During this time, the variables or identifier
> are allocated memory location and they filled with placeholder `undefined` whereas
> function statements are stored as it is.

#### II. Code Execution

> After it has assigned the memory to all the identifiers and functions in global scope, the line of code starts executing line by line.

#### <b>Working</b>

> Whenever a JS file is come across a JS Engine, it creates a global execution context even if it dosn't have any functions or identifiers or it is just a blank page and puts it in the `call stack`.

> A different Exection Context is created when function execution takes place and placed over the global execution in this case or any execution context before it and the execution context is `popped out` and destroyed after the execution of that function completes.

> So If we have function inside function and so on, the call stack during the execution of innermost function consist of global scope at the bottom, the nested functions on top of it on the order of the function call.

## 2. Hoisting in JavaScript

> Hoisting in JavaScript is the process in which JavaScript engine allocates memory for the identifiers and functions at the beginning of creation of execution context for that scope.

```js
var x = 3;
function print() {
  console.log("hello world");
}
```

> In above example, when JS engine first comes across this file, it starts formation of `Global Execution Context`, during which it allocates memory for the identifier variable `x` and stores as key value pair where key is `x` and value is `undefined`. For the function `print`, it makes key value pair as key being `print` and copies the whole function inside its `value`. which looks like:

```js
Global:
x:undefined
print:function print(){
    console.log('hello world');
}
```

|                 |                                                                                                                                                                                                             |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <b> `Note` </b> | Memory allocation takes place even before executing first line of code, and so if any errors like syntax errors occur, JavaScript engine throws error ritht away even before executing single line of code. |

#### <b>So the question is what happens when you try to access the identifier or variables before initializing it?</b>

Let's see

```js
console.log("x is ", x);
print();

var x = 3;
function print() {
  console.log("hello world");
}
```

> So here we are trying to access `x` before initializing and invoke `print` function earlier as well. So what can we expect from this?. Well the output will look like this.

```bash
x is undefined
hello world
```

<b> So what happened there?</b>

> As we discussed earlier, during `Memory Allocation` even before execution of variable `x` is assigned `undefined` so it prints `undefined` whereas in case of function `print` the whole function is already stored so even if we call function before its statement, it will work as per expected.

<b>But what if we use `let` instead of `var` or use `JavaScript Expression` or `Arrow Function` instead of normal `Function Statement`?</b>

> It will throw `Reference Error - tried to access before initialization` or something like that. We will discuss this further.

## 2. Lexical Environment And Scope Chain

> In broad terms, `Lexical Environment is the combination of local environment and Lexical Environment of its parents.` It makes not sense at all right now. But what it means is

```js
var x = 3;
function a() {
  var y = 5;
  console.log(x, y);
}
```

What will be the output of above code?

```bash
3 5
```

Pretty simple, right? But how does this happen, how can we reference to `y` even it is `out of scope` of function `a`?

> It is because the execution of function a forms a Lexical Environment with its local variables, i.e. `y` and the Lexical Environment of its parent, in this case it is the global environment which has `x`. So the `Lexical Environment` of function `a` contains both `x` and `y` so it can reference them.

### Block Scope & Shadowing

### let const vs var

### Closures

### First Class Function

### Callback Functions

### Higher Order Functions

### Garbage Collector

### Asynchronous Concepts and Event Loop

### Array Methods
