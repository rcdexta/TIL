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
