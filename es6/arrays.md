# Arrays

An array can be created in javascript using the following syntax

``` javascript
var odd = [1,3,5,7,9];
var even = new Array(2,4,6,8);
var empty = new Array(4);

even; //[2,4,6,8]
empty; //[null,null,null,null]
```

#### Destructuring

Array destructuring syntax is very similar to object destructuring; it just uses array literal syntax instead of object literal syntax. The destructuring operates on positions within an array, rather than the named properties that are available in objects.

``` javascript
let colors = ['red', 'blue', 'yellow'];

let [firstColor, secondColor] = colors;
let [, , thirdColor] = colors;
thirdColor; 							//yellow
let [, , thirdColor, otherColor='cyan'] = colors;
otherColor;							//cyan
```

##### Nested Destructuring

``` javascript
let colors = [ "red", [ "green", "lightgreen" ], "blue" ];

let [ firstColor, [ secondColor ] ] = colors;
firstColor;        // "red"
secondColor;       // "green"
```

##### Rest Items 

You can use the rest operator `...` to assign the remaining items in an array to  a particular variable

``` javascript
let numbers = [1,5,8,3,4];

let [first, ...rest] = numbers;
rest; //[5,8,3,4]
```

You can clone an array easily in ES6 using the rest operator.

``` javascript
let primes = [2,3,5,7,11];
let [..newPrimes] = primes;
```