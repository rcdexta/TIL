## Object Inspections

#### To List all the methods in an object

Use `Object.getOwnPropertyNames(object)` to get all the own properties of an object. This differs from `Object.keys` which lists only [enumerable properties](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Enumerability_and_ownership_of_properties)

``` javascript
Object.getOwnPropertyNames([1,2,3]); // ["0", "1", "2", "length"]
```

#### To deep inspect an object

1. Use `util.inspect`
``` javascript
var util = require('util');
console.log(util.inspect(err.error));
```
2. Use console directly
``` javascript
console.dir(obj);
console.log('%j',obj);
```

(1) yields a much more pretty and crisp output

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
