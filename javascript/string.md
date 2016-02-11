## Strings

#### Basic Operations

In addition to basic javascript operations on string, please find the additional methods introduced in ES6

``` javascript
var name = "James Bond";
name.startsWith("James")  //true
name.endsWith("nd")       //true
name.includes("Bon")      //true
"hi".repeat(5)             //hihihihihi
```

#### Template Literals

This is a just a regular string delimited by a backtick (`` ` ``) instead of double or single quotes

``` javascript
let str = `Tada`
str         //"Tada"
str.length  //4
typeof str  //"String
```

Backtick itself can be escaped using backslash like this `` `\`Ben\` Venuto!` ``;

### Multiline strings

``` javascript
let message = `This is a loooong
string`;
message           //"This is a loooong\nstring'
message.length    //24
```

#### Substitutions

Substitutions are delimited by an opening `${` and a closing `}` that can have any JavaScript expression inside. 

``` javascript
let greeting = "Vanakkam"
console.log(`${greeting} Chennai`)      //"Vanakkam Chennai"
console.log(`2 + 2 = ${2+2}`)           //"2 + 2 = 4
```

