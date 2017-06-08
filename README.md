# TeachMeFPinJS
A guide to Functional Programming in Javascript

I am creating this guide to help introduce the concepts of Functional Programming in an easy to learn step-by-step process using Javascript as the example language but i may expand this into other languages. 

I wanted to create this guide as i have found many different sources that teach parts of functional programming but i found them all very technical or discrete and i wanted to collate everything i have learn't. I also hope that creating this guide will help me improve my own understanding of Functional Programming :)

## Contributions and Issues
This topic isn't a small one and there are many ways to teach it so if you think there is anything that i have missed, havn't explained well or just isn't correct please feel free to open an issue or pull request. I want to do create this for the soul purpose of teaching others.

# FP Basics

## What is FP?
TODO

## What is a function? 
Lets start with the basics, this is a function:

``` javascript
var count = 1

function increment(num) { return num + 1 }

result = increment(count)
// result == 2

```

An so is this:
``` javascript
var count = 1

function increment() { count += 1 }

increment()
// count == 2
```


The key difference is the first function's result is only determined by it's inputs, nothing else outside the function can effect it. This is commonly referred to as a `Pure Function` or `Referential transparency`.

The second function however increments `count` without it being passed into the function directly. This is called a `Side Effect` and is refered to as an `Impure Function`.

A `Side Effect` is any effect a function has outside of simply outputting a value based on it's inputs. This could be either reading a mutable value or modifying a value outside itself.

At first this example seems harmless but how do we know if the `count` variable isn't also changed by another function? What if we try and call this function before the variable is declared? Many things can go wrong with impure functions so a key rule we stick to in Functional Programming is: 
> *'Most of your program should be composed of Pure Functions'*. 

Now obviously we live in the real world and side effects are something that needs to happen otherwise the program won't interact with the external world. We will cover how we handle these side effects later but we aim to keep most of our program as pure as possible as it makes the program easier to understand and reason with.

## Avoid Mutation, Be Immutable

Now some pure functional programming languages do not allow for mutation of any kind except where explicitly defined. Javascript however is a bit of a free spirit and doesn't have such discipline.

An example of this is with Javascript Arrays. Say we want to create a function that returns everything in an array but the first element. Javascript offers 2 methods that at first appear to do the same thing: `.splice()` and `.slice()`.

``` javascript
var myArrayA = [1, 2, 3]

function arrayTail(array) { return array.slice(1) }

var result = arrayTail(myArrayA)
// result == [ 2, 3 ]
```

``` javascript
var myArrayB = [1, 2, 3]

function arrayTail(array) { return array.splice(1) }

var result = arrayTail(myArrayB) 
// result == [ 2, 3 ]
```

But something misterious happens, without us knowing...
``` javascript
myArrayA === [1,2,3]
myArrayB === [2,3]
```

What!?! The second array has somehow changed after we passed it into the function. This is because the `.splice()` method actually modifies the original array while `.slice()` just returns a copy of the array.

This means that `.splice()` is impure (takes the array, modifies it and returns it) while `.slice()` is pure (takes the array, copies what it needs and returns it) and so we would be wise to avoid using `.splice()` and similar functions if we wish to continue programming functionally.

## Arrow Functions (ES6)

Before we go any further we will switch to using arrow functions in Javascript. This is a alternative, cleaner method for writing functions in javascript since ES6. All examples in the rest of the book will be using this format though there is nothing stopping you writing them in the older style(ES5).

To start simply, the following ES5 function:
``` javascript
var myFunction   (x)    { return x }
```
would be written as follows in ES6 syntax:
``` javascript
var myFunction = (x) => { return x }
```

Now at first this may seem like longer syntax but as we will see, when our functions typically take 1 parameter and just run one expression (like `x + 1`) it becomes a lot cleaner. When there is one parameter we can remove the brakets around it and when the function consists of one complete expression we can also remove the curly brackets `{}` and the `return` value as the function assumes it will always return the first expression it comes across.
``` javascript
// ES5
var myFunction   (x)    { return x + 1 }

// ES6
var myFunction = x => x + 1 
```


## First class functions

Functions in Javascript are treated as first-class citizens. This allows them to be passed around as values just like a string, number or array.

A common example is the Array.map method which takes a function as it's argument. If the map method is new, it takes a function and applies it to each of it's arguments as such:


## Topics
- FP Basics 
    - What is FP?
    
    - Immutablility
        - mutation / immutable funcs in JS
    - Composition (ramda?)
    - dot chaining and functions


    - Pointfree
    - Hindley Milner
    - Currying (why data last?)

- Array
- Alternative to Loops - map, reduce, filter
- Types vs Typeclasses (JS equiv of Objects and Methods on those objects but not OO style)
- Box - my first functor
- Maybe (list JS methods that can return null)
- Either
- IO (sync)
- Future / Task (async)
- Observables
- Promises (map and chain combo?)
- Feature
- Applicative
- Free Monads (IO DSL?)
- ADT's

- Other areas of FP
    - Languages
    - Databases
    - Faas Cloud services
    - Testing (quickcheck)

## Types
- Box, Maybe, Either, IO, Future / Task, Observable, Promise, Tuple, State

## Typeclasses
- Setoid, Semigroup, Functor, Applicative, Monad, Foldable, ChainRec

##

## Topic contents
- TDLR / Summary
- other names for the same thing
- introduce a problem, handle imperative/JS way, handle OO then FP style?
- code examples
- Image description, especially for harder concepts (like a .map image or monad)
- examples to solve w answer
- terms
- libraries
- uses in JS
- FP laws with JS example to prove it

## Sources that taught me FP that help me contribute to this
- https://github.com/hemanth/functional-programming-jargon
- https://www.pluralsight.com/courses/hardcore-functional-programming-javascript
- https://drboolean.gitbooks.io/mostly-adequate-guide/content/
- https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/
- https://github.com/stoeffel/awesome-fp-js#resources

## libraries
- https://github.com/rom-melnyk/eslint-plugin-pureness
- eslint cleanJS
- folktale
- ramda fantasy
- https://github.com/ramda/ramda-fantasy