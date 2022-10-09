# Object orianted programming in javascript

1. **Object**– An Object is a unique entity that contains properties and methods. For example “car” is a real life Object, which has some characteristics like color, type, model, horsepower and performs certain actions like drive. The characteristics of an Object are called Properties in Object-Oriented Programming and the actions are called methods. An Object is an instance of a class. Objects are everywhere in JavaScript, almost every element is an Object whether it is a function, array, or string.

There are certain features or mechanisms which makes a Language Object-Oriented like:

- Object
- Classes
- Encapsulation
- Inheritance

---

## A Method in javascript is a property of an object whose value is a function.

### Object can be created in two ways in JavaScript:

Using an Object Literal :

```

//Defining object
let person = {
    first_name:'Mukul',
    last_name: 'Latiyan',

    //method
    getFunction : function(){
        return (`The name of the person is
          ${person.first_name} ${person.last_name}`)
    },
    //object within object
    phone_number : {
        mobile:'12345',
        landline:'6789'
    }
}
console.log(person.getFunction()); // The name of the person is mukul latiyan
console.log(person.phone_number.landline); // 6789
```

- ### Using an Object Constructor:

```

//using a constructor
function person(first_name,last_name){
   this.first_name = first_name;
   this.last_name = last_name;
}
//creating new instances of person object
let person1 = new person('Mukul','Latiyan');
let person2 = new person('Rahul','Avasthi');

console.log(person1.first_name); //Mukul
console.log(`${person2.first_name} ${person2.last_name}`); // Rahul Avasthi
```

2.**Classes**- Classes are blueprint of an Object. A class can have many Objects because class is a template while Object are instances of the class or the concrete implementation.
Before we move further into implementation, we should know unlike other Object Oriented Language there are no classes in JavaScript we have only Object. To be more precise, JavaScript is a prototype based Object Oriented Language, which means it doesn’t have classes, rather it defines behaviors using a constructor function and then reuse it using the prototype.

**Note: Even the classes provided by ECMA2015 are objects.**

> "JavaScript classes, introduced in ECMAScript 2015, are primarily syntactical sugar over JavaScript’s existing prototype-based inheritance. The class syntax is not introducing a new object-oriented inheritance model to JavaScript. JavaScript classes provide a much simpler and clearer syntax to create objects and deal with inheritance."  
> –Mozilla Developer Network

Example:

```

// Defining class using es6
class Vehicle {
  constructor(name, maker, engine) {
    this.name = name;
    this.maker =  maker;
    this.engine = engine;
  }
  getDetails(){
      return (`The name of the bike is ${this.name}.`)
  }
}
// Making object with the help of the constructor
let bike1 = new Vehicle('Hayabusa', 'Suzuki', '1340cc');
let bike2 = new Vehicle('Ninja', 'Kawasaki', '998cc');

console.log(bike1.name);    // Hayabusa
console.log(bike2.maker);   // Kawasaki
console.log(bike1.getDetails());

```

3. **Inheritance** – It is a concept in which some properties and methods of an Object are being used by another Object. Unlike most of the OOP languages where classes inherit classes, JavaScript Objects inherit Objects i.e. certain features (property and methods) of one object can be reused by other Objects.

Let’s understand inheritance with an example:

```
//Inheritance example
class person{
	constructor(name){
		this.name = name;
	}
	//method to return the string
	toString(){
		return (`Name of person: ${this.name}`);
	}
}
class student extends person{
	constructor(name,id){
		//super keyword for calling the above class constructor
		super(name);
		this.id = id;
	}
	toString(){
		return (`${super.toString()},Student ID: ${this.id}`);
	}
}
let student1 = new student('Mukul',22);
console.log(student1.toString());
```

In the above example, we define an Person Object with certain properties and methods and then we inherit the Person Object in the Student Object and use all the properties and methods of the person Object as well as define certain properties and methods for the Student Object.

**Note**: The Person and Student object both have same method (i.e toString()), this is called Method Overriding. Method Overriding allows a method in a child class to have the same name and method signature as that of a parent class.
In the above code, the super keyword is used to refer to the immediate parent class’s instance variable.

---

---

## Default parameters

**Default function parameters** allow named parameters to be initialized with default values if no value or undefined is passed.

```
function multiply(a, b = 1) {
  return a * b;
}

console.log(multiply(5, 2));
// expected output: 10

console.log(multiply(5));
// expected output: 5
```

### Description:

In JavaScript, function parameters default to undefined. However, it's often useful to set a different default value. This is where default parameters can help.

In the following example, if no value is provided for b when multiply is called, b's value would be undefined when evaluating a \* b and multiply would return NaN.

```
function multiply(a, b) {
  return a * b;
}

multiply(5, 2); // 10
multiply(5); // NaN !
```

---

# Arrays - functional methods

**Map** - is a method that you can use on arrays to **create a new array** by transforming every element thanks to a callback function.
Example:

```
const numbers = [1, 2, 5, 7];

const doubles = numbers.map(function (currentNumber) {
  return currentNumber * 2;
});

console.log(doubles); // [2, 4, 10, 14]
```

map will return a **new** array, which has exactly the same size as the original array. The callback function given to map is called with every element one after the other and the return value of this callback will be the value of the elements in the new array.

**ForEach** - Map is not the only method that you can use on Arrays, another useful method is forEach.
As the name suggests forEach will do something for each element in the array.

But wait... What's the difference with map?!?

Map will generate a new array. **ForEach** is just doing an action for every array element.

**Filter** -The filter method will create a new array with only the elements that verify a condition.

Example -

```
const myArray = [3, 2, 40, 15, 20];
const greaterThanFive = myArray.filter(number => number > 5);
console.log(greaterThanFive);
// [40, 15, 20]
```

---

## Destructuring assignment

The two most used data structures in JavaScript are Object and Array.

Objects allow us to create a single entity that stores data items by key.
Arrays allow us to gather data items into an ordered list.
Although, when we pass those to a function, it may need not be an object/array as a whole. It may need individual pieces.

Destructuring assignment is a special syntax that allows us to “unpack” arrays or objects into a bunch of variables, as sometimes that’s more convenient.

### Array destructuring -

Here’s an example of how an array is destructured into variables:

```
// we have an array with the name and surname
let arr = ["John", "Smith"]

// destructuring assignment
// sets firstName = arr[0]
// and surname = arr[1]
let [firstName, surname] = arr;

alert(firstName); // John
alert(surname);  // Smith
```

Now we can work with variables instead of array members.

The rest ‘…’
Usually, if the array is longer than the list at the left, the “extra” items are omitted.

For example, here only two items are taken, and the rest is just ignored:

```
let [name1, name2] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];

alert(name1); // Julius
alert(name2); // Caesar
// Further items aren't assigned anywhere
```

If we’d like also to gather all that follows – we can add one more parameter that gets “the rest” using three dots "...":

```
let [name1, name2, ...rest] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];

// rest is array of items, starting from the 3rd one
alert(rest[0]); // Consul
alert(rest[1]); // of the Roman Republic
alert(rest.length); // 2
```

The value of rest is the array of the remaining array elements.

We can use any other variable name in place of rest, just make sure it has three dots before it and goes last in the destructuring assignment.

```
let [name1, name2, ...titles] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];
// now titles = ["Consul", "of the Roman Republic"]
```

## Object destructuring

The destructuring assignment also works with objects.

The basic syntax is:

let {var1, var2} = {var1:…, var2:…}
We should have an existing object on the right side, that we want to split into variables. The left side contains an object-like “pattern” for corresponding properties. In the simplest case, that’s a list of variable names in {...}.

For instance:

```
let options = {
  title: "Menu",
  width: 100,
  height: 200
};

let {title, width, height} = options;

alert(title);  // Menu
alert(width);  // 100
alert(height); // 200
```

Properties options.title, options.width and options.height are assigned to the corresponding variables.

The order does not matter. This works too:

```
// changed the order in let {...}
let {height, width, title} = { title: "Menu", height: 200, width: 100 }
```

The pattern on the left side may be more complex and specify the mapping between properties and variables.

If we want to assign a property to a variable with another name, for instance, make options.width go into the variable named w, then we can set the variable name using a colon:

```
let options = {
  title: "Menu",
  width: 100,
  height: 200
};

// { sourceProperty: targetVariable }
let {width: w, height: h, title} = options;

// width -> w
// height -> h
// title -> title

alert(title);  // Menu
alert(w);      // 100
alert(h);      // 200
```

The colon shows “what : goes where”. In the example above the property width goes to w, property height goes to h, and title is assigned to the same name.

For potentially missing properties we can set default values using "=", like this:

```
let options = {
  title: "Menu"
};

let {width = 100, height = 200, title} = options;

alert(title);  // Menu
alert(width);  // 100
alert(height); // 200
```

Just like with arrays or function parameters, default values can be any expressions or even function calls. They will be evaluated if the value is not provided.

In the code below prompt asks for width, but not for title:

```
let options = {
  title: "Menu"
};

let {width = prompt("width?"), title = prompt("title?")} = options;

alert(title);  // Menu
alert(width);  // (whatever the result of prompt is)
```

We also can combine both the colon and equality:

```
let options = {
  title: "Menu"
};

let {width: w = 100, height: h = 200, title} = options;

alert(title);  // Menu
alert(w);      // 100
alert(h);      // 200
```

If we have a complex object with many properties, we can extract only what we need:

```
let options = {
  title: "Menu",
  width: 100,
  height: 200
};

// only extract title as a variable
let { title } = options;

alert(title); // Menu
```

### The rest pattern “…”

What if the object has more properties than we have variables? Can we take some and then assign the “rest” somewhere?

We can use the rest pattern, just like we did with arrays. It’s not supported by some older browsers (IE, use Babel to polyfill it), but works in modern ones.

It looks like this:

```
let options = {
  title: "Menu",
  height: 200,
  width: 100
};

// title = property named title
// rest = object with the rest of properties
let {title, ...rest} = options;

// now title="Menu", rest={height: 200, width: 100}
alert(rest.height);  // 200
alert(rest.width);   // 100
```
