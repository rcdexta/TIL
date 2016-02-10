## Object Inspections

#### To List all the methods in an object

``` javascript
Object.getOwnPropertyNames(object);
```

#### To deep inspect an object

``` javascript
var util = require('util');
console.log(util.inspect(err.error));
```

#### What type is the object

```javascript
typeof operand
typeof 37 === 'number';
typeof "" === 'string';
typeof true === 'boolean';
typeof {a:1} === 'object';
typeof new Date() === 'object';
typeof function(){} === 'function'
typeof null === 'object'; //surprise!
```
