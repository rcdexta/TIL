# Objects

Objects are created in Javascript using the `Object Literal` syntax.

``` javascript
var person = {firstname: "James", lastname: "Bond"}
person.firstname; //James
person['lastname']; //Bond
```

#### Object Methods

##### Object.is()

Instead of using the equals operator `==` or the identity equals operator `===`, ES6 recommends the `Object.is()` method to avoid all the quirks with identity

``` javascript
Nan == Nan;          //false
Nan === Nan;         //false
Object.is(Nan, Nan); //true

5 == "5"            //true
Object.is(5, "5")   //false
```

##### Object.assign()

Mixins are among the most popular patterns for object composition in JavaScript. In a mixin, one object receives properties and methods from another object.

``` javascript
var person = {name: 'RC'}
var employment = {company: 'ThoughtWorks', salary: 250000}
Object.assign(person, employment);

person; //{"name":"RC","company":"ThoughtWorks","salary":250000}
```
