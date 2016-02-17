# Objects

Objects are created in Javascript using the `Object Literal` syntax.

``` javascript
var person = {firstname: "James", lastname: "Bond"}
person.firstname; //James
person['lastname']; //Bond
```

#### Concise Methods

ECMAScript 6 also improves the syntax for assigning methods to object literals.

``` javascript
//ES5
var Dog = {
  name: 'Terry',
  greet: function(){
    return "Bow Wow";
  }
};
//ES6
var Dog = {
  name: 'Terry',
  greet(){
    return "Bow Wow";
  }
};

var pet = Object.create(Dog);
pet.greet(); //Bow Wow
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
#### More Powerful Prototypes

You can get and set the prototype of an object using the `getPrototypeOf()` and `setPrototypeOf()` methods

``` javascript
let Dog = {
  greet() {
    return "bow wow";
  }
}

let Cat = {
  greet() {
    return "meow meow";
  }
}

let pet = Object.create(Dog);
pet.greet();                                        //bow wow
console.log(Object.getPrototypeOf(pet) == Dog);     //true
Object.setPrototypeOf(pet, Cat);
pet.greet();                                        //meow meow
```

You can use the `super` keyword to access prototype methods like

``` javascript
let talkingPet = {
  greet() {
    return `I can ${super.greet()}`;
  }
}

Object.setPrototypeOf(talkingPet, Cat);
talkingPet.greet();                       //I can meow meow
```
