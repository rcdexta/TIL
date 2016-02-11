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

#### Default Parameter values 

Now because the function invocation is allowed with lesser number of parameters than required, it becomes a hassle to check which are of the parameters have values. ECMAScript 6 makes it easier to provide default values for parameters by providing initializations that are used when the parameter isn't formally passed.

``` javascript
function powerOf(number, power = 2) {
  return Math.pow(number, power);
}
powerOf(4)      //16
powerOf(4, 3)   //64
```
