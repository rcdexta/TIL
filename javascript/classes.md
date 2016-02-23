# Classes

Class declarations begin with the class keyword followed by the name of the class. The rest of the syntax looks similar to concise methods in object literals without requiring commas between them.

``` javascript
class Hero  {
  constructor(power) {
    this.power = power;
  }
  
  beHero(){
    return `I can ${this.power}`;
  }
}

let rajini = new Hero('subtract 0 from 0');
console.log(rajini.beHero());   			// I can subtract 0 from 0

console.log(rajini instanceof Hero);     // true
console.log(rajini instanceof Object);   // true

console.log(typeof Hero);                    // "function"
console.log(typeof Hero.prototype.beHero);   // "function"
```

Things to note:

* class declarations allow you to define the constructor directly inside of the class using the special `constructor` method name.
* class methods use the concise syntax, there's no need to use the function keyword. All other method names have no special meaning, so you can add as many as you want.

Just as functions have an expression form that doesn't require an identifier after function, and similarly, classes have an expression form that doesn't require an identifier after class. So the previous class can be defined as `let Hero = class { ... };`

#### Accessor properties

While own properties should be created inside of class constructors, classes allow you to define accessor properties on the prototype. To create a getter, use the keyword get followed by a space followed by an identifier; to create a setter, do the same using the keyword set. For example:

``` javascript 
class CustomHTMLElement {
    constructor(element) {
        this.element = element;
    }
    get html() {
        return this.element.innerHTML;
    }
    set html(value) {
        this.element.innerHTML = value;
    }
}
```

#### Generator methods

Generator functions can be defined inside a class as well. Let's try creating a default iterator for a class

``` javascript
class Odd {
	constructor(){
	  this.items = [1,3,4,5,7,9];
	}
	
	*[Symbol.iterator](){
	  yield *this.items;
	}
}

var odds = new Odd();
for(let x of odds){
  console.log(x);  			// 1 3 5 7 9
}
```

#### Static Members

Classes simplify the creation of static members by using the formal `static` annotation before the method or accessor property name. 

``` javascript
class Dog {
	constructor(name){
		this.name = name;
	}
	talk(){
		console.log(`I am ${this.name}. Bow wow!`);
	}
	static create(name){
		return new Dog(name);
	}
}

Dog.create('Trevor').talk(); // "I am Trevor. Bow wow!"
```

#### Inheritance

Classes make inheritance easier by using the familiar `extends` keyword to specify the function from which the class should inherit. The prototypes are automatically adjusted and you can access the base class constructor using `super()`.

``` javascript
class Rectangle {
    constructor(length, width) {
        this.length = length;
        this.width = width;
    }
    getArea() {
        return this.length * this.width;
    }
}

class Square extends Rectangle {
    constructor(length) {
		super(length, length);
    }
}

var square = new Square(3);

console.log(square.getArea());              // 9
console.log(square instanceof Square);      // true
console.log(square instanceof Rectangle);   // true
```

#### Inherited Static Members

If a base class has static members then those static members are also available on the derived class. 
