# Maps

The ECMAScript 6 Map type is an ordered list of key-value pairs where both the key and the value can be of any type. Keys are considered to be the same by using Object.is(), so you can have both a key of 5 and a key of "5" because they are different types.

#### Basic operations

``` javascript
let map = new Map();
map.set("name", "James Bond");
map.set("age", 99);

console.log(map.get("name"));       // "James Bond"
console.log(map.get("age"));        // 99

console.log(map.has("weight"));     //false

map.delete("name");

console.log(map.size);              //1
console.log(map.get("name"));        //undefined

map.clear();
```

#### Initialization

You can use the following syntactic sugar to initiate a map with key value pairs

``` javascript
let map = new Map([ ["name", "James Bond"], ["age", 99]]);
```

#### Iteration

The `forEach` method works similar to array and sets. It has a callback function with three parameters: `value`, `key` and the `owner map`.

``` javascript
let map = new Map([ ["name", "James Bond"], ["age", 99]]);
map.forEach(function(value, key, ownerMap) {
    console.log(key + " " + value);
    console.log(ownerMap === map);
});
// name James Bond
// true
// age 99
// true
```

