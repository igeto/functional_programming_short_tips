# Functional programming short tips
---
## Basic concepts of functional programming

### 1. Purity
An idea that functions in programming shouldn’t have side effects and should instead behave like functions in mathematics. A mathematical function is a type of equation that has at least one independent variable and one dependent variable, such as:
```
y = x + 5
f(x) = x + 5
f(2) = 2 + 5
f(2) = 7
```
where there is only one value of y for each value of x, and it is always the same. So no matter how many times you pass the number 2 to f(x), you will always end up with 7.

### 2. Immutability
An idea that we shouldn’t use variables — values that can change. Instead we should use constants, values that cannot change. Although we might still call them “variables” because that’s an established term, they are variables in name only, as they cannot variate. For our purposes this means that we must create a new constant every time we need to store a value.

This is the same as in math, where you can’t do something like
```
x = x + 1
```
Instead you would do
```
y = x + 1
```
### 3. (a) Functions as first class citizens
A first class citizen in a programming language is any sort of entity that supports all of the operations that are commonly available to other entities. This means that for a function to be a first class citizen it has to be able to be treated as a value. In JavaScript we can assign functions to variables or perform operations on them, where the result of that function’s execution will be used when the operation runs.

### 3. (b) Higher order functions
A higher order function is a function that can can accept other functions as parameters and also return functions as results. Once again this is possible because functions are first class citizens in JavaScript.

### 4. Closures
A closure is a function that resides inside another function, and has access to the parent function’s variables. This is because a function remembers the environment (scope) in which it was created. As such it can use the variables of that scope even after the scope itself was destroyed.
```
function foo() {
  const x = 5;
  function bar() {
    console.log(x + 2);
  }
  setTimeout(() => { bar() }, 2000);
}
```
Here bar() runs 2 seconds after foo() was last used. It’s entirely possible that foo() has already been deleted from memory by a garbage collector, and yet bar() remembers the value of x — a variable that was declared within the scope of foo() and disappeared with it.

### 5. Referential transparency
Any function should be able to be replaced by what it would return when it runs. If we have a function foo() that returns a number (5 for example) there should be no difference between writing
```
const x = foo() * 2;
```
and
```
const x = 5 * 2;
```
This goes back to the idea of Purity, where a function should always return the same result if given the same input, and should not have any side effects.

Examples:
```
.map() .reduce()
```
---
## Advanced Topics
Generally these are not applicable. If you are dealing with these, you are probably way more advanced that the people for whom this writeup was meant. I'm including them here just to provide definitions, so that if new developers see these terms in some other tutorials they would know what is being talked about.

### 1. Currying
A pattern that was developed to compensate for the shortcomings of really old languages that only supported a single parameter per function. Now used out of habit and not actually supported by JS. When people speak of currying in JS they really just mean using closures.

### 2. Function composition
A pattern one would use if one wanted to prevent the consumers of the code from chaining top-level functions and potentially shooting themselves in the foot. Composed functions would only expose themselves and then enforce the sequence of operations.
