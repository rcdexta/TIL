## Functions

Functions in JavaScript are unique in that they allow any number of parameters to be passed, regardless of the number of parameters declared in the function definition.

``` javascript
function testArgs(a,b){
  console.log(`a: ${a}`);
  console.log(`a: ${a}`);
}

testArgs(1,2)     // a: 1 b: 2
testArgs(1)       // a: 1 b: undefined
testArgs(3,4,5,6) // a: 3 b: 4
```

#### Default parameter values 

Now because the function invocation is allowed with lesser number of parameters than required, it becomes a hassle to check which are of the parameters have values. ECMAScript 6 makes it easier to provide default values for parameters by providing initializations that are used when the parameter isn't formally passed.

``` javascript
function powerOf(number, power = 2) {
  return Math.pow(number, power);
}
powerOf(4)      //16
powerOf(4, 3)   //64
```

#### Special default parameters

You can also call a function to return the default value for a parameter if it is unspecified.

``` javascript
var m = 1;
function multiplier(){
  return m++;
}
function multiply(a, b = multiplier()){
  return a * b;
}
multiply(3);         //3
multiply(3);         //6
multiply(3, 0);      //0
```

A previous parameter can repeat as default parameter as well.

``` javascript
function twice(a, b = a) {
  return a * b;
}
```

#### Rest Parameters (Variable args)

A rest parameter is indicated by three dots (...) preceding a named parameter. That named parameter becomes an Array containing the rest of the parameters passed to the function, which is where the name "rest" parameters originates.

``` javascript
function pick(object, ...keys){
  var result = {};
  for (var i = 0; i < keys.length; i++) {
    var key = keys[i];
    result[key] = object[key];
  }
  return result;
}

pick({a: 1,b: 2,c: 3},'b','c'); // {b: 2, c: 3}
```

Things to note:
* There can be only one rest parameter in a function
* And the rest parameter must be the last parameter to a function

#### Spread operator

What if you would like to pass an array as parameter to a function that accepts rest parameters. There you would use the `...` operator

``` javascript
function max(...values){
  var max = -1;
  for(var i=0;i<values.length;i++){
    max = max < values[i] ? values[i] : max;
  }
  return max;
}

var arr = [3,9,5,8,6];
max(...arr); //9
max(...arr, 11) //11
```
### Arrow Functions

One of the most interesting new parts of ECMAScript 6 is the arrow function. Arrow functions are, as the name suggests, functions defined with a new syntax that uses an "arrow" (=>). 

Simple examples:

``` javascript
var mirror = value => value;
mirror(10); //10

var diff = (a,b) => a - b;
diff(9,5) //4

//With no args, have an empty set of parantheses
var whatDay = () => "Good Day";
whatDay(); //"Good Day"

var nothing = () => {}; //valid empty function
```
Better examples:

``` javascript
var last = (...arr)  => {
  return arr[arr.length - 1];
}
last(...[1,2,3,4]); //4

var sorted = [4,3,7,1].sort((a,b) => a - b);
sorted; //[1,3,4,7]
```

#### Tail Call Optimization 

Tail recursion (or tail-end recursion) is particularly useful, and often easy to handle in implementations. Tail calls can be implemented without adding a new stack frame to the call stack. ES6 supports TCO. 

Check out this code shared in [Babel REPL](https://t.co/lRM2jFNGMs) to know how Tail Call Optimization works and how Babel Transpiler converts the recursion into iteration to make it work with ES5.


