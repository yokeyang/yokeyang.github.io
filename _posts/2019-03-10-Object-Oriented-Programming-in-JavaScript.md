---
title:  "An introduction to Object-Oriented Programming in JavaScript"
categories:
  - FrontTech
tags: 
  - Frontend
  - medium
entries_layout: grid
lang_change: true
lang: en
author_profile: true
toc: true
toc_label: "An introduction to Object-Oriented Programming in JavaScript"
toc_sticky: true
header:
  image: /assets/images/2019-03-10-An-introduction-to-Object-Oriented-Programming-in-JavaScript/01.png
  caption: "JavaScript and Object-Oriented Programming"
---
[Rainer Hahnekamp at Nov 16, 2018](https://medium.freecodecamp.org/an-introduction-to-object-oriented-programming-in-javascript-8900124e316a)

*This article is for students of JavaScript that don’t have any prior knowledge in object-oriented programming (OOP). I focus on the parts of OOP that are only relevant for JavaScript and not OOP in general. I skip polymorphism because it fits better with a static-typed language.*

## Why do you need to know this?
Have you picked JavaScript to be your first programming language? Do you want to be a hot-shot developer who works on giant enterprise systems spanning hundred-thousand lines of code or more?

Unless you learn to embrace Object-Oriented Programming fully, you will be well and truly lost.

## Different Mindsets
In football, you can play from a safe defense, you can play with high balls from the sides or you can attack like there is no tomorrow. All these strategies have the same objective: To win the game.

The same is true for programming paradigms. There are different ways to approach a problem and design a solution.

Object-oriented programming, or OOP, is THE paradigm for modern application development. It is supported by major languages like Java, C# or JavaScript.

## The Object-Oriented Paradigm
From the OOP perspective, an application is a collection of “objects” that communicate with each other. We base these objects on things in the real world, like products in inventory or employee records. Objects contain data and perform some logic based on their data. As a result, OOP code is very easy to understand. What is not so easy is deciding how to break an application into these small objects in the first place.

If you were like me when I heard it the first time, you have no clue what this actually means — it all sounds very abstract. Feeling that way is absolutely fine. It’s more important that you’ve heard the idea, remember it, and try to apply OOP in your code. Over time, you will gain experience and align more of your code with this theoretical concept.

Lesson: OOP based on real-world objects lets anyone read your code and understand what’s going on.

## Object as Centerpiece

![img][02]{: .align-center}

A simple example will help you see how JavaScript implements the fundamental principles of OOP. Consider a shopping use case in which you put products into your basket and then calculate the total price you must pay. If you take your JavaScript knowledge and code the use case without OOP, it would look like this:

```javascript
const bread = {name: 'Bread', price: 1};
const water = {name: 'Water', price: 0.25};
const basket = [];
basket.push(bread);
basket.push(bread);
basket.push(water);
basket.push(water);
basket.push(water);
const total = basket
  .map(product => product.price)
  .reduce((a, b) => a + b, 0);
console.log('one has to pay in total: ' + total);
```

The OOP perspective makes writing better code easier because we think of objects as we would encounter them in the real world. As our use case contains a basket of products, we already have two kinds of objects — the basket object and the product objects.

The OOP version of the shopping use case could be written like:

```javascript
const bread = new Product('bread', 1);
const water = new Product('water', .25)
const basket = new Basket();
basket.addProduct(2, bread);
basket.addProduct(3, water);
basket.printShoppingInfo();
```
As you can see in the first line, we create a new object by using the keyword `new` followed by the name of what’s called a class (described below). This returns an object that we store to the variable bread. We repeat that for the variable water and take a similar path to create a variable basket. After you have added these products to your basket, you finally print out the total amount you have to pay.

The difference between the two code snippets is obvious. The OOP version almost reads like real English sentences and you can easily tell what’s going on.

**Lesson**: An object modeled on real-world things consists of data and functions.

## Class as Template

![img][03]{: .align-center}

We use classes in OOP as templates for creating objects. An object is an “instance of a class” and “instantiation” is the creation of an object based on a class. The code is defined in the class but can’t execute unless it is in a live object.

You can look at classes like the blueprints for a car. They define the car’s properties like torque and horsepower, internal functions such as air-to-fuel ratios and publicly accessible methods like the ignition. It is only when a factory instantiates the car, however, that you can turn the key and drive.

In our use case, we use the Product class to instantiate two objects, bread and water. Of course, those objects need code which you have to provide in the classes. It goes like this:

```javascript
function Product(_name, _price) {
  const name = _name;
  const price = _price;
this.getName = function() {
    return name;
  };
this.getPrice = function() {
    return price;
  };
}
function Basket() {
  const products = [];
this.addProduct = function(amount, product) {
    products.push(...Array(amount).fill(product));
  };
this.calcTotal = function() {
    return products
      .map(product => product.getPrice())
      .reduce((a, b) => a + b, 0);
  };
this.printShoppingInfo = function() {
    console.log('one has to pay in total: ' + this.calcTotal());
  };
}
```

A class in JavaScript looks like a function, but you use it differently. The name of the function is the class’s name and is capitalized. Since it doesn’t return anything, we don’t call the function in the usual way like `const basket = Product('bread', 1);`. Instead, we add the keyword new like `const basket = new Product('bread', 1);`.

The code inside the function is the constructor. This code executes each time an object is instantiated. Product has the parameters `_name` and `_price`. Each new object stores these values inside it.

Furthermore, we can define functions that the object will provide. We define these function by prepending the this keyword which makes them accessible from the outside (see Encapsulation). Notice that the functions have full access to the properties.

Class Basket doesn’t require any arguments to create a new object. Instantiating a new Basket object simply generates an empty list of products that the program can fill afterwards.

**Lesson**: A class is a template for generating objects during runtime.

## Encapsulation

![img][04]{: .align-center}

You may encounter another version of how to declare a class:

```javascript
function Product(name, price) {
  this.name = name;
  this.price = price;
}
```

Mind the assignment of the properties to the variable this. At first sight, it seems to be a better version because it doesn’t require the getter (getName & getPrice) methods anymore and is therefore shorter.

Unfortunately, you have now given full access to the properties from the outside. So everybody could access and modify it:

```javascript
const bread = new Product('bread', 1);
bread.price = -10;
```
This is something you don’t want as it makes the application more difficult to maintain. What would happen if you added validation code to prevent, for example, prices less than zero? Any code that accesses the price property directly would bypass the validation. This could introduce errors that would be difficult to trace. Code that uses the object’s getter methods, on the other hand, is guaranteed to go through the object’s price validation.

Objects should have exclusive control over their data. In other words, the objects “encapsulate” their data and prevent other objects from accessing the data directly. The only way to access the data is indirect via the functions written into the objects.

Data and processing (aka logic) belong together. This is especially true when it comes to larger applications where it is very important that processing data is restricted to specifically-defined places.

Done right, OOP produces modularity by design, the holy grail in software development. It keeps away the feared spaghetti-code where everything is tightly coupled and you don’t know what happens when you change a small piece of code.

In our case, objects of class Product don’t let you change the price or the name after their initialization. The instances of Product are read-only.

`Lesson`: Encapsulation prevents access to data except through the object’s functions.

## Inheritance

![img][05]{: .align-center}

Inheritance lets you create a new class by extending an existing class with additional properties and functions. The new class “inherits” all of the features of its parent, avoiding the creation of new code from scratch. Furthermore, any changes made to the parent class will automatically be available to the child class. This makes updates much easier.

Let’s say we have a new class called Book that has a name, a price and an author. With inheritance, you can say that a Book is the same as a Product but with the additional author property. We say that Product is the superclass of Book and Book is a subclass of Product:

```javascript
function Book(_name, _price, _author) {
  Product.call(this, _name, _price);
  const author = _author;
  
  this.getAuthor = function() {
    return author;
  }
}
```

Note the additional `Product.call` along the `this` as the first argument. Please be aware: Although book provides the getter methods, it still doesn’t have direct access to the properties name and price. Book must call that data from the Product class.

You can now add a book object to the basket without any issues:

```javascript
const faust = new Book('faust', 12.5, 'Goethe');
basket.addProduct(1, faust);
```

Basket expects an object of type Product. Since book inherits from Product through Book, it is also a Product.

**Lesson**: Subclasses can inherit properties and functions from superclasses while adding properties and functions of their own.

## JavaScript and OOP
You will find three different programming paradigms used to create JavaScript applications. They are Prototype-Based Programming, Object-Oriented Programming and Functional-Oriented Programming.

The reason for this lies in JavaScript’s history. Originally, it was prototype-based. JavaScript was not intended as a language for large applications.

Against the plan of its founders, developers increasingly used JavaScript for bigger applications. OOP was grafted on top of the original prototype-based technique.

The prototype-based approach is shown below. It is seen as the “classical and default way” to construct classes. Unfortunately it does not support encapsulation.

Even though JavaScript’s support for OOP is not at the same level as other languages like Java, it is still evolving. The release of version ES6 added a dedicated `class` keyword we could use. Internally, it serves the same purpose as the prototype property, but it reduces the size of the code. However, ES6 classes still lack private properties, which is why I stuck to the “old way”.

For the sake of completeness, this is how we would write the Product, Basket and Book with ES6 classes and also with the prototype (classical and default) approach. Please note that these versions don’t provide encapsulation:

```javascript
// ES6 version
class Product {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
}
class Book extends Product {
  constructor(name, price, author) {
    super(name, price);
    this.author = author;
  }
}
class Basket {
  constructor() {
    this.products = [];
  }
  addProduct(amount, product) {
    this.products.push(…Array(amount).fill(product));
  }
  calcTotal() {
    return this.products
      .map(product => product.price)
      .reduce((a, b) => a + b, 0);
  }
  printShoppingInfo() {
    console.log('one has to pay in total: ' + this.calcTotal());
  }
}
const bread = new Product('bread', 1);
const water = new Product('water', 0.25);
const faust = new Book('faust', 12.5, 'Goethe');
const basket = new Basket();
basket.addProduct(2, bread);
basket.addProduct(3, water);
basket.addProduct(1, faust);
basket.printShoppingInfo();
//Prototype version

function Product(name, price) {
  this.name = name;
  this.price = price;
}

function Book(name, price, author) {
  Product.call(this, name, price);
  this.author = author;
}
Book.prototype = Object.create(Product.prototype);
Book.prototype.constructor = Book;

function Basket() {
  this.products = [];
}
Basket.prototype.addProduct = function(amount, product) {
  this.products.push(...Array(amount).fill(product));
};
Basket.prototype.calcTotal = function() {
  return this.products
    .map(product => product.price)
    .reduce((a, b) => a + b, 0);
};
Basket.prototype.printShoppingInfo = function() {
  console.log('one has to pay in total: ' + this.calcTotal());
};
```
**Lesson**: OOP was added to JavaScript later in its development.

## Summary
As a new programmer learning JavaScript, it will take time to appreciate Object-Oriented Programming fully. The important things to understand at this early stage are the principles the OOP paradigm is based on and the benefits they provide:

- Objects modeled on real-world things are the centerpiece of any OOP-based application.
- Encapsulation protects data from uncontrolled access.
- Objects have functions that operate on the data the objects contain.
- Classes are the templates used to instantiate objects.
- Inheritance is a powerful tool for avoiding redundancy.
- OOP is more verbose but easier to read than other coding paradigms.
- Since OOP came later in JavaScript’s development, you may come across older code that uses prototype or functional programming techniques.

## Further reading
- [https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_JS](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_JS)
- [http://voidcanvas.com/es6-private-variables/](http://voidcanvas.com/es6-private-variables/)
- [https://medium.com/@rajaraodv/is-class-in-es6-the-new-bad-part-6c4e6fe1ee65](https://medium.com/@rajaraodv/is-class-in-es6-the-new-bad-part-6c4e6fe1ee65)
- [https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance)
- [https://en.wikipedia.org/wiki/Object-oriented_programming](https://en.wikipedia.org/wiki/Object-oriented_programming)

[02]: /assets/images/2019-03-10-An-introduction-to-Object-Oriented-Programming-in-JavaScript/02.png
[03]: /assets/images/2019-03-10-An-introduction-to-Object-Oriented-Programming-in-JavaScript/03.png
[04]: /assets/images/2019-03-10-An-introduction-to-Object-Oriented-Programming-in-JavaScript/04.png
[05]: /assets/images/2019-03-10-An-introduction-to-Object-Oriented-Programming-in-JavaScript/05.png
