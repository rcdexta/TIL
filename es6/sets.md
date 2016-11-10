# Sets 

#### Initialization

ECMAScript 6 adds a Set type that is an ordered list of values without duplicates.

``` javascript
let set = new Set();
set.add(3);
set.add("3");
set.size;    // 2
```

You can initialize a set from an array as well

``` javascript
let set = new Set([1,3,4,5,1,4,6]);
set.size; //5
```

#### Set methods

``` javascript
let set = new Set([2, "2", 3, 4]);

set.has(2);				//true
set.has("2");				//true

set.delete("2");
set.has("2");				//false

set.clear();
set.has("5");  			// false
set.size;  				// 0
```

#### forEach to iterate

``` javascript
let set = new Set(["a", "b"]);

set.forEach(function(value, key, ownerSet) {
    console.log(key + " " + value);
    console.log(ownerSet === set);
});

// "a" "a"
// true
// "b" "b"
// true
```

#### Set to Array

``` javascript
let set = new Set([1, 2, 3, 3, 3, 4, 5]),
    array = [...set];

array;             // [1,2,3,4,5]
```

#### Weak Sets

The Set might alternately be called a strong set because of the way it stores object references. An object stored in an instance of Set is effectively the same as storing that object inside of variable, meaning that as long as that reference exists, the variable cannot be garbage collected to free memory. 

``` javascript
let set = new WeakSet(),
    key = {};

set.add(key);

set.has(key);      // true

// remove the last strong reference to key, also removes from weak set
key = null;
```