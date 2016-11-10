# Iterators and Generators

Before going to generators, let's talk about iterators in javascript. The conventional way to iterate over any collection is as below

``` javascript
var colors = ["red", "green", "blue"];

for (var i=0, len < colors.length; i < len; i++) {
    console.log(colors[i]);
}
```

Now we can define a iterator interface to achieve the same thing. That interface consists of a method called `next()` that returns a result object. The result object has two properties, `value`, which is the next value, and `done`, which is a boolean value that's true when there are no more values to return.

First let's create an iterator in ES5 to understand the mechanics

``` javascript
function createIterator(items) {
    var i = 0;
    return {
        next: function() {
            var done = (i >= items.length);
            var value = !done ? items[i++] : undefined;
            return {
                done: done,
                value: value
            };
        }
    };
}

var iterator = createIterator(["a", "b", "c"]);

console.log(iterator.next());           // "{ value: "a", done: false }"
console.log(iterator.next());           // "{ value: "b", done: false }"
console.log(iterator.next());           // "{ value: "c", done: false }"
console.log(iterator.next());           // "{ value: undefined, done: true }"
``` 

Now instead of writing iterators for each type of collection ourselves, ES6 proposes a new type of interface called `Generator`

#### Generator function

A generator is a special kind of function that returns an iterator. Generator functions are indicated by inserting a star character (*) after the function keyword (it doesn't matter if the star is directly next to function or if there's some whitespace between them). The yield keyword is used inside of generators to specify the values that the iterator should return when next() is called. So if you want to return three different values for each successive call to next(), you can do so as follows:

``` javascript
// generator
function *simpleGenerator() {
    yield "you";
    yield "me";
    yield "out";
}

// generators are called like regular functions but return an iterator
let iterator = simpleGenerator();

console.log(iterator.next());     // {"value":"you","done":false}
console.log(iterator.next());     // {"value":"me","done":false}
console.log(iterator.next());     // {"value":"out","done":false}
console.log(iterator.next());     // {"done":true}
```

Perhaps the most interesting aspect of generator functions is that they stop execution after each yield statement, so first `yield` executes and then the function doesn't execute anything else until the iterator's next() method is called. At that point, execution resumes with the next statement after `yield "you"`, which in this case is `yield "me"`. This ability to stop execution in the middle of a function is extremely powerful and lends to some interesting uses of generator functions 

#### Loop iteration using generator

``` javascript
function *each(next){
  for(var i=0;i<=next.length;i++){
    yield next[i];
  }
}

var x = each([1,2,3]);

console.log(x.next());			//{"value":1,"done":false}
console.log(x.next());			//{"value":2,"done":false}
console.log(x.next());			//{"value":3,"done":false}
console.log(x.next());			//{"done":true}
```

#### for-of method

All iterators created by generators are called iterables. An iterable is an object with a @@iterator symbol property. The well-known @@iterator symbol specifies a function that returns an iterator for the given object. All of the collection objects, including arrays, sets, and maps, as well as strings, are iterables in ECMAScript 6 and so have a default iterator specified. 

Iterables are designed to be used with a new addition to ECMAScript: the for-of loop.

``` javascript
let values = [1, 2, 3];

for (let num of values) {
    console.log(num);
}
```

#### Accessing the default iterator

You can access the default iterator for an object using `Symbol.iterator`, for example:

``` javascript
let values = [1, 2];
let iterator = values[Symbol.iterator]();

console.log(iterator.next());           // "{ value: 1, done: false }"
console.log(iterator.next());           // "{ value: 2, done: false }"
console.log(iterator.next());           // "{ value: undefined, done: true }"
```

Knowing that Symbol.iterator specifies the default iterator, it's possible to detect if an object is iterable by using the following:

``` javascript
function isIterable(object) {
    return typeof object[Symbol.iterator] === "function";
}

console.log(isIterable(1.0));     		// false
console.log(isIterable([1, 2, 3]));     // true
console.log(isIterable("Hello"));       // true
console.log(isIterable(new Map()));     // true
console.log(isIterable(new Set()));     // true
console.log(isIterable(new WeakMap())); // false
console.log(isIterable(new WeakSet())); // false
```

The isIterable() function simply checks to see if a default iterator exists on the object and is a function. 

#### Creating Iterables

Developer-defined objects are not iterable by default, but you can make them iterable by creating a `Symbol.iterator` property containing a generator

``` javascript
let collection = {
    items: [],
    init(val){
      this.items = val;
    },
    *[Symbol.iterator]() {
        for (let item of this.items) {
            yield item;
        }
    }
};

collection.init([1,2,3])

for (let x of collection) {
    console.log(x);
}
```