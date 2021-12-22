# Java Script
## 1. Wha's is javascript?

## 2. Sintax

### 2.1 Variables

Variable definitions should always start with the keyword var. Now notice that no types are declared in JavaScript. And the reason that is because JavaScript is called a dynamically typed language. Now what that means is that the JavaScript engine figures out the type of a particular variable at runtime. And it also means that the same variable can hold different types during the life of the execution of the program. 
```js
var message= "hi";
```
So a variable can start out to be a string, then change to a number, then change to an object, and so on, and all of that is perfectly legal.

### 2.2 Function

Now the way you define a function is by using the keyword function followed by function name and followed parentheses then curly braces. 
```js
funtion a() {...}
```
Now in JavaScript, when you define a function name, it's very, very similar to defining a variable whose value is a function:
```js
var a= funtion() {...}
```
When you do it the second way, no name is defined after the function keyword. However, either syntax let's you refer to this function as a.  

The value of the function is assigned to a, not the returned result of the execution of that function. So after either of these definitions you can now invoke, otherwise known as execute, function by referring to it by it's name `a`.
#### 2.2.1 Arguments
Now you can also define `arguments` to be passed to the JavaScript function. Now the defined arguments are defined without the keyword var. In fact, if you place the key word var in the function argument definition, that will be a syntax error. 

If you want your function to `return` some value, you use the return keyword followed by whatever value it is that you want to return. If the return keyword is not followed by a value, what you're signaling to the JavaScript engine is that it should terminate the function and exit out of it without returning anything.

```js
funtion compare(x,y) {
	return x>y;
}
```

Each function or variable lives within a particular scope. In JavaScript there's really two scopes, global scope and function, or otherwise known as lexical scope. Now lexical here means that it depends on where something is physically defined.
#### 2.2.2 Global vs Lexical Scope

| Global Scope                                                                                                                      | Function (aka lexical)                                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| any other functions that are defined in a global scope and so on can get access to these globally defined functions and variables | As far as function and lexical scope, variables and functions defined here are available only within this functio and we can define functions within other functions. | 

#### 2.2.3 The Scope Chain
 In order to understand how scope chain works in JavaScript, you have to understand how a JavaScript engine executes things:
 - Everything in JavaScript is executed in an *Execution context*.
 -  function invocation creates a new *Execution context* within which that function is executed.
 -  each execution context has the following.
	 1. It's own variable environment, where it stores its newly defined functions and variables.
	 2. Special `'this'` object
	 3. gets a reference to its *Outer environment*. Meaning the execution environment within which this particular function is defined. (global scope does not have an outer environment simply because it's the most outer there is.)*
	 
Here's how scope chain works:
1. Referenced, notice referenced, not defined, variable will be searched for in its current scope first.
2. If not found, the outer reference will be searched. 
3. If not found there, the outer reference's outer reference will be searched and etc., and so on. 
4. If not found, the outer reference's outer reference will be searched, and etc., and so on. 
5. Now this will keep going until the global scope. If not found in global scope, the variable is going to be undefined. variable undefined means it's just not found.

_Example_: Suppose you executed a couple of lines of code inside the global scope. The first line defines variable x and assigns a value of 2 to the variable x and the second line executes function A. 

Now function A itself is defined in global scope and it has its own variable x that is set to 5. Now then, within function A you call function B. Function B is also defined in the global scope and all it does is just print out the to the console the value of x. 

*What will be printed out to the console?* The answer is that the result that will be x = 2 from the global scope.
![[Pasted image 20211220123606.png|550]]


Even though B is called within A and A has its own x, what actually matters, as far as resolving where x is coming from, is its *Outer reference*. And B is defined within the global scope. Therefore, the outer reference of function B is the **global scope**, not function A. 

What this means is that it does not matter where a particular function is executed. What matters as far as resolving scope of a variable is concerned is where that function is physically defined. Function B is physically defined inside the global scope. Therefore a reference of x inside function B Is going to look inside function B first. If it doesn't find it it's going to use its outer reference to look for it there and its outer reference is the global scope.

## 2.3 Javascript Types

*First of all, what is a type? *A type is ==a particular data structure==. Each language defines some built in types, and can be used to build other data structure.
Now JavaScript has 7 built-in types, 6 primitive, and one object type. 

#### 2.3.1 Object Types
*So what is an object in JavaScript? *Well in JavaScript an object is nothing more than **==a collection of name/value pairs==**. You can have one name value pair, or it can have zero name value pairs. 
But it is a collection of name value pairs.

_Example Object Type_: Here I have a person object and it has a bunch of different name value pairs. First name, Yaakov, last name Chaikin, social and so on. So first name would be the name and Yaakov would be the value and so too a value doesn't necessarily have to be a single value, it could be a **nested object**. 

So a name here, for example is `social`, the name of the property of the object. And the value of that property, is **an entire *nested* other object**, that has again, name value pairs. 
![[Pasted image 20211220160420.png|500]]
#### Assign Properties
*But how to assign properties, in other words how to create those name-value pairs?*
_Example_: We're creating a company **variable** and we're setting it to new object. Once we created a reference to an object, we're ready to create **properties** of that object. we'll say `company.name` and that property name doesn't exist yet but but the second I set it to something, it becomes a reality and now it does exist.
```js
var company= new Object();
company.name= "Facebook";
company.ceo = new Object();
company.ceo.first_name="Mark";
company.ceo.fav_color="Blue";
console.log(company);
```
![[Pasted image 20211221084336.png|300]]
#### Bracket VS Dot notation
```js
console.log("Company CEO name is" + company.ceo.first_name) // or we can use
console.log("Company CEO name is" + company["first_name"])
``` 
I can get at the company name using the bracket notation, not just the dot notation. Now Why can't I just use the dot notation? Well the reason I can't always use the dot notation, is because the dot notation will only work with whatever is a valid JavaScript identifier, or valid JavaScript, either function name, or valid JavaScript variable name.
_Example:_
```js
console.stock = 110; // it will give us an ERROR!!!!
console.log("Stock price is: "+ company.stock) // it will give us an ERROR!!!!

console["company stock is:"]=110; //OK!
console.log("Stock price is: "+ company["Stock price is:"]) //OK!!!
``` 
#### Simpler way to create Objects
How to create a simple object and how to set properties on it.
```js
// Better way: object literal
var facebook = {
	name: "Facebook",
	ceo: {
	firstName: "Mark",
	favColor: "blue"
},
"stock of company": 110
};

console.log(facebook.ceo.firstName);
```

#### 2.3.2 Primitive Types
```md
Primitive type is a type that represents a single, immutable value.
```

*So what do that mean? *

- A single value means it's **not an objec**t, remember an object is collections of name, value pairs, even simplest object there is there is a name of value pair. It's a single value.
- **Immutable** means once it's set, once that value is set **It cannot be changed**. It means that once you set it, the value of the variable becomes ==read-only==. You could certainly create another value based on an a existing value but the memory space that was allocated for the first value is not changed. Instead, you create a new memory space for the new value.

So let me run down one by one of all the primitive types that JavaScript defines:
- **Boolean**:
	 can only have two values, either true or false. And true and false are reserved keywords in JavaScript language.
- **Undefined**:
	The undefined data type signifies that ==no value has ever been set== on this particular variable of this type. This is the value that every variable gets *when the JavaScript engine sets up the variable in memory when it defined but has never been assigned any value yet.*
- **Null**:
	Now, the ==lack of value==** as opposed to undefined **which signifies the lack of definition. There's only one value that could ever set for that type and that value is the reserved keyword, null. And it's also perfectly normal and perfectly okay to explicitly in your code set a variable to the null value.	
- **Number**:
	is the only numeric type in JavaScript and it has as a double-precision 64-bit floating point. In other words, JavaScript does not have integer type. Integers in JavaScript are just a subset of doubles instead of a separate data type.
- **Strings**:
 	 it is a sequence of characters used to represent text and you can define strings either using single or double quotes.
- **ES6**

_Note_: *Is **undefined** not the same as **not defined**? * Is correct. Undefined meaning is that it has been declared, or defined, so to speak, but it has not been set to any value. So the variable has been declared and a memory space has been allocated for it, but no value has been placed in that memory space. 
![[Pasted image 20211220162614.png|700]]

### 2.4 Handling default values
```js
function order_chicken_with(side_dash){
	if (side_dish === undifined){
		side_dish="whatever";
	}
	console.log("Chicken with"+ side_dish);
}

order_chicken_with("noodles");
order_chicken_with("Undifined");
```

We could create a default value that if the value for side dish is not provided, we could substitute it with a value "whatever". Here we used the **triple equal == **which compare the type of the two variables and, if they are the same, the resoult will be `true`.

But Java Script has a short cut way of doing the same thing:
```js
side_dish= side_dish ||"whatever!"
```
*So how is this working? *Well, the reason this is working is because each and one of these values is getting **coerced **into a boolean value. So if it's false or this second statement will get evaluated. And the second statement, since it is a non-empty string, gets evaluated to true. And what the or statement does in this circumstance is actually returns the value before it was coerced.

### 2.5 Passing variables by value vs by reference
- By Value:
Given b=a, copying or passing things by the value means that changing the copied value in b, does not affect the value stored in a, and vice versa. So if I change b after I have copied the value of a into b, a stays the way it was before and b changes but does not affect a.
- By Reference:
Given b equals a, again, we're copying the contents of a into b, passing and copying by reference would mean the change in copied value in b does indeed affect the value stored in a, and visa versa. So they're kind of pointing to the same location.
#DEF : Now in JavaScript, the way it works is that **primitives are passed by value**, and **objects are passed by reference**.
BUT in reality, underneath the hood, in the JavaScript engine everything is actually passed and copied by `value`. And the difference is why one is really called passed by reference and one passed by value really comes because of the way the objects and primitives are **stored in memory**.
```js

```
_Example_: So here, on the left, we have primitives, a is equal seven, and then we're copying variable a, or the contents of variable a into variable b. And on the right, we have a variable a that is equal an object that has a property x, it will be equal 7. And then in the second line, we're copying the contents of a into b. 

So b in the end of the day, in both circumstances ends up with the same value, as a.![[Pasted image 20211221092838.png|400]]
```js

```

- ** Passed by value (used by Primitives in JS): **when we override the variable b with the value 5, what we're actually doing is replacing a different value into the same memory location that b is pointing to. In this case, 002. So, in this In this scenario, what you end up is that a is still pointing to its original location, 001, which still has number 7 in it as the value in that memory location and b is now pointing to 002, with a different value so therefore a and b have nothing to do with each other.
- **Passed by reference (used by Objects in JS):** So what's going on is that a gets again allocated a memory location. Again in this case 001 is the address and memory. And what gets put into that memory location as the value is another memory address so inside the address 001 the value in that position is another memory position that is pointing to **another point in memory**. And then the address 003 is where the value actually sits.
	
	So then when we declare variable b and we equate variable b to a, what's actually happening is that again the value of variable a, where variable a is pointing to, Is copied into variable b. Well, the value is 003. So b now, even though it's sitting at memory location 004, it's value is another memory location with a value of 003.  So what ends up happening is they're ** both pointing to a memory location 003** so finally when we update `p.x = 5`, what we are actually updating is the **memory location** of what b is pointing to and **that is 003** so **the direct value of b still stays the same, it's the value that it's pointing to that is changing. ** And since both a and b are pointing to the same value, the end result is is that both are pointing to a changed value.


![[Pasted image 20211221093000.png|350]] || ![[Pasted image 20211221093151.png|360]]

_Example_: after, we call changeObject, the original value now is changed and it's x: 5, because both of those variables were pointing toward the same memory locations so they are effecting the same values.
```js
function changeObject(objValue) {
	console.log("in changeObject...");
	console.log("before:");
	console.log(objValue);
	objValue.x = 5;
	console.log("after:");
	console.log(objValue);
}
value = { x: 7 };
changeObject(value); // objValue = value
console.log("after changeObject, orig value:");
console.log(value);
```
![[Pasted image 20211221095619.png|300]]
#SUMMARY : passed by reference is that in passed by value the values once it's changed do not affect the original value of the original variable. As opposed by reference when you change the value, the original object that's pointing to it is changed as well.

### 2.6 Function Constructors
```js
function test(){
	console.log(this);
	this.my_name= "Yaakov"
}
test();
console.log(window.my_name);
```
![[Pasted image 20211221111602.png|300]]
`this` is pointing to the global Window object. And `my_name` is pointing to the global object, window.myName or `my_name` property was created on the window object.

 If we actually wanted to kind of encapsulate some data within a particular object and use a function for it, then we would need this to point to something else. And this is where ==**Function Constructors**== come in.

It's used the first letter of the **Function Constructors** to be a capital one, and it lets me know that it's a function constructor. So it's basically just a convention to let other developers know that this is a function constructor as opposed to a regular function.

_Example_: Let's create another function, and let's call this function Circle, we're going to create circles.
```js
// Function constructors
	function Circle (radius) {
	this.radius = radius;
	this.get_area= function(){
		return Math.PI * Math.pow(this.radius, 2)
	};
};

var myCircle = new Circle(10);
console.log(myCircle);

var myOtherCircle = new Circle(20);
console.log(myOtherCircle);
```
![[Pasted image 20211221112506.png|250]]
The problem is, as we keep creating these Circle objects over and over in our code, we're going to keep creating this getArea function over and over in our code. Because every time we say new, this entire thing gets created. 

Well, for radius, it's perfectly normal, because each circle should have its own radius. We really don't need our type Circle to have its own getArea on every object that's created. It really should be just created once, and all the circles, all the instances of a Circle, should share it. And the way we could do that is by using a special property called `prototype`.

```js
// Function constructors
	function Circle (radius) {
	this.radius = radius;
}

Circle.prototype.getArea =
	function () {
	return Math.PI * Math.pow(this.radius, 2);
};

var myCircle = new Circle(10);
console.log(myCircle.getArea());

var myOtherCircle = new Circle(20);
console.log(myOtherCircle);
```
![[Pasted image 20211221112749.png|250]]
Now, you could see that the radius is here, the radius equals 10, but the getArea doesn't exist here. 

Well, where is it? Well, it's actually sitting inside of the special variable `__proto__`. ` __proto__` is something that's going to be existent on every single instance of this object. So if we, for example, create another one, var myOtherCircle. both of them are pointing to the same proto variable that have a getArea, and this getArea is actually the same location in memory as this getArea. So it doesn't get recreated over and over.	

### 2.7 Object Literals

```js
// Object literals and "this"
var literalCircle = {
	radius: 10,
	getArea: function () {
		console.log(this);
		return Math.PI * Math.pow(this.radius, 2);
		}
};
literalCircle.getArea();
console.log(literalCircle.getArea());
```
This is no longer referring to the window object or the global object, but it's actually referring to our circle class or to our literalCircle, which is an object with a radius of 10. So when an object literal gets created, this, instead of pointing to the global object, is actually pointing to the actual object that got created.
![[Pasted image 20211221115038.png|250]] || ![[Pasted image 20211221115214.png|300]]

But Why is this keyword referring to the object instead of referring like any other regular function to the global object like window?
So when that happens, when we call `var literalCircle = {`, `new Object()` is executed in the background
(`new` keyword again). And when we see the `new` keyword (implicit), the `this` variable inside of that object is now referring to the actual object and not to the outside window or outside global object. So this in fact works exactly like function constructors in terms of the `new` keyword.

_Inner Function (Before ECMAScript 6)_:

```js
// Object literals and "this"
var literalCircle = {
	radius: 10,
	getArea: function () {
		var self = this;
		console.log(this);
		var increaseRadius = function () {
			self.radius = 20;
			};
		increaseRadius();
		console.log(this.radius);
		return Math.PI * Math.pow(this.radius, 2);
		}
};
console.log(literalCircle.getArea());
```
When you have an inner function within another function, this keyword starts pointing to the global object. 
*So how do you get around this? *Well, there's a common pattern that people use to get around this, and the way you get around this is you just say ``var self = this``. ``self`` is always going to be referring to this. And this, at this point, at least, is referring to the literalCircle object.

### 2.8 Arrays
Arrays are just a collection of data.In JavaScript however, since we have dynamic typing, arrays take on pretty interesting set of properties.
```js
var array = new Array();
array[0]= "Yaakov";
array[1]=2;
array[2]=functiom(name) {
	console.log("Hello "+ name);	
};
array[3]= {course: "HTML, CSS & JS"};

console.log(array);
array[2]=array[0];
console.log(array[3].course)
```
![[Pasted image 20211221120532.png|250]]
How to loop array in `for` loops?
```js
// Short hand array creation
var names = ["Yaakov", "John", "Joe"];
console.log(names);
for (var i = 0; i < names.length; i++) {
	console.log("Hello " + names[i]);
}
```

#PROBLEM: there's something we actually haven't seen yet, And there's a special for loop that you could use to **traverse the properties of an object. **. It's a for, and you declare it as a `var` Prop in myObj. So basically it will say, I want to grab every property in my object. 
So it's very convenient for objects, because objects don't really have indices like an array does, it has properties.
```js
var names2 = ["Yaakov", "John", "Joe"];
for (var name in names2) {
	console.log("Hello " + names2[name]);
}
```
Now the reason that it will output "*Hello Hi!*", is because the `greeting` became a property of the array no different than a number zero, or number two, or number one, and so on. `Greeting` becomes a property of the array, and this for loop loops ** over the property names of the object. ** And since again, arrays are just objects in JavaScript, this `for` loop ==will loop over properties==, even over properties that really have nothing to do with the core data that we want to loop over.
```js
names2.greeting = "Hi!";

for (var name in names2) {
	console.log("Hello " + names2[name]);
}
```
![[Pasted image 20211221121620.png|300]] ||							![[Pasted image 20211221121638.png|270]]
### 2.9 Closures

```js
// Closures
function makeMultiplier (multiplier) {
	// var multiplier = 2;
	function b() {
		console.log("Multiplier is: " + multiplier);
	}
	b();
	
	return (
		function (x) {
		return multiplier * x;
	}
	);
}
var doubleAll = makeMultiplier(2);
console.log(doubleAll(10)); // gets its own exec env
```
*How does the inner function right here B know that the multiplier is 2?*

When a function is executed it gets a few things:
1. it gets it's own execution context so it's isolated from everything else. 
2. Number two, it gets a special vis variable, we spoke about that before. 
3. Number three, it gets a reference to its outer lexical environment. 

So when a variable is referenced inside of a function the first thing it does is check whether or not this variable has been defined inside of it's local lexical environment meaning has the multiplier variable been defined inside the B function? 
And the answer is it's not, it's not defined. And if it's not defined it means the next thing that the JavaScript engine does it looks at the outside lexical environment of this function. Well the outside lexical environment of this function meaning where it's defined the outside of that is the `makeMultiplier` function. And the `makeMultiplier` function has that variable, so once it finds it it goes ahead and uses it in the function B that we're executing right here.

*But how then can the `return (function(x){..})` possibly know what the multiplier variable is? *Because at the time that this is executing the makeMultiplier function is no longer in the execution stack. It's popped off the execution stack. 

Well, the reason this still works is because of **==JavaScript closures==**. Since a function like this returned from inside of this function JavaScript p==reserves its outer lexical environment memory space ==for this function.So the multiplier is something that's still sitting in memory in lexical **outside scope **of this function. 
So even when we call `doubleALL` it will go ahead and execute this function. It will create its own execution environment. It will go ahead and look for the multiplier variable in its own execution environment. It **will not find it** and it will then try to look for for this variable in its **outer lexical environment**, and the outer lexical environment memory space will still remain even though the makeMultiplier function no longer exists.
### [2.10 Fake Namespaces & Immediately Invoked Funciton Expression (IIFEs)](https://www.coursera.org/learn/html-css-javascript-for-web-developers/lecture/uz3nG/lecture-52-part-1-fake-namespaces)

#### 2.10.1 Fake Namespaces
#DEF :**==Name spaces==** are basically just a container for some functionality and for some declarations. 
The only thing is, is JavaScript doesn't really have name spaces that other languages have. However, in JavaScript we could fake name spaces very easily. Faking namespaces using JavaScript objects such that certain variables and functions can coexist in the global scope without stepping on each other's toes.

_Example_: we have two libreries and a file `app.js` that invoches these two function ``sayHello.js`` and ``sayHi.js`` inside those two files.
```js
//APP.js
sayHello();
sayHi();
```

```js
//SCRIPT1.js
	var name = "Yaakov";
	funtion sayHello(){
		console.log("Hello "+ name);
	};
```

```js
//SCRIPT2.js
	var name = "John";
	funtion sayHi(){
		console.log("Hello "+ name);
	};
```
The resoult of app.js is:
![[Pasted image 20211221151808.png|300]]
*Why is this happening?* Well, it's actually pretty simple why this is happening. If you look at our index.html, the first thing that the browser loads, is `script1.js`, that declares a variable name. And this name variable is sitting in the global scope and is also declares a function called sayHello again, in the global scope. So, when this executes, it will take whatever name variable is sitting in the global scope. 
Now, right after script one, we're loading script2.js, which again declares name in the global scope. Which basically means that at this point right here, my name = "Yaakov" gets overwritten with name = "John". One script is stepping on the toes of the other, basically. 

*So how do we solve this situation? * Well, one way of solving the situation is introduce **==name spaces==**. Let's go to script.js script1.js and instead of just saying Yaakov here, let's declare a variable called var yaakovGreeter. 
```js
//SCRIPT1.js
	var yaakovGreeter = {};
	yaakovGreeter.name = "Yaakov";
	var greeting = "Hello ";
	yaakovGreeter.sayHello = function () {
		console.log(greeting + yaakovGreeter.name);
		}
```
Now instead of just declaring name right here in the global scope, what I'll do is I'll declare name as a property of yaakovGreeter.
Now that we've converted this to a name space and now everything that we are referring to inside this, in terms of the variable names, and the functions are going to have to go through these name space object. So inside our app.js, in order to say sayHello, that's no longer going to work.
```js
//APP.js
yaakovGreeter.sayHello();
johnGreeter.sayHi();
```

But there's something you could do to go even further in order to separate the different variables that are sort of like private variables between different scripts and different execution contexts:  Immediately Invoked Funciton Expression (IIFEs).
#### 2.10.2  Immediately Invoked Funciton Expression (IIFEs)
A lot of the times when you have a bunch of functionalities sitting in a script, a lot of it is not really something that you'd necessarily, even want to put into some namespace.
So for example, if I didn't want to hard code the string saying, `"hello"`, if I wanted to, for example, declare as a regular variable. So, I just want that to be a string.
*Well, and we kind of have exactly the same problem again, don't we? *Greeting now is going to be part of the window object, part of the global object in script two and in script one is going to be again, part of the global object. So once again, I'm now going to end up with Hi Yaakov, Hi John instead of hello Yaakov, Hi John.
-->One more thing we could do is introduce something that's called ==immediately invoke function expression==.
For example, a function is:
```js
//SCRIPT1.js
var a=function(){
	console.log("Hello Coursera!");
};

a();

//SCRIPT1.js (IIFEs)
(function(){
	console.log("Hello Coursera!");
}();
```
I can invoke this function right in line by just putting parenthesis right after its declaration. So, this declaration right here is going to produce a function and the parenthesis right behind it is going to invoke it immediately. So this is what's called Immediately Invoked Function Expression, otherwise, known as IIFE.

It produces a function object and then we're taking that function object and we're just putting parentheses right behind it, and that invokes that function object.
```js
//SCRIPT1.js
(function (window) {
	var yaakovGreeter = {};
	yaakovGreeter.name = "Yaakov";
	var greeting = "Hello ";
	yaakovGreeter.sayHello = function () {
		console.log(greeting + yaakovGreeter.name);
		}
	}
window.yaakovGreeter = yaakovGreeter;
})(window);
```

```js
//APP.js
yaakovGreeter.sayHello();
johnGreeter.sayHi();

// Immediately Invoked Function Expression
// IIFE
(function (name) {
	console.log("Hello " + name);
})("Coursera!");
```

## 3. DOM Manuipulation (Document Object Model)
So the first question that comes when we start talking about DOM manipulation is *How to include the actual script.js, how to include your JavaScript library inside your HTML page?*
```html
<!--HTML file-->
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
  </head>
<body>
  <h1 id="title">Lecture 53</h1>
  
  <p>
    Say hello to 
    <input id="name" type="text">
    <button onclick="sayHello();">
      Say it!
    </button>
  </p>

  <div id="content"></div>

  <script src="js/script.js"></script>
</body>
</html>
```
The reason we're able to use `document` here is because we're in the global scope. And global scope is `window`. And `window` has an attribute, has a property called `document` in it. So when we say document, this will obviously go ahead and look on the window object to see if document is one of its properties.
```js
console.log(document.getElementById("title"));
```
Now the reason we're able to use this function called getElementById, is because document is a special object and the object name of the document is HTMLDocument. It's a special object that has a whole bunch of different methods.

What if we wanna interact with the `<button>`? We should define the `sayHello()` function.
```js
// JAVASCRIPT FILE
function sayHello() {
	var name= console.log(
		document.getElementById("name").value;
	);
	var message = "Hello "  name;
	document.querySelector("#content").textcontent = message;
}
```
There's another method that's much more generic than getElementById, because getElementById really just restricts you to be able to select things within your page by ID, but you might want to be able to select it by other things. So, the method we could use, and instead of getElementById, is called querySelector. And in this case, querySelector takes not the ID name but actually, a selector: specify with the `#`.

### 3.2 Event Handlers
Now first of all, what are event handlers? 
```md
Event handlers are basically functions that you bind using specific methods to certain events that happen in the browser. 

```
Now those events might be triggered by just a lifecycle. Meaning something like the page loaded. That's an event. Or it could be triggered by user interaction, like a user typed a character or user clipped something. So one of the most simplest ways to assign an event handler to a particular element is to just use the `on`-something attribute on that element. There's a whole bunch of these and they really have to do with keyboard and mouse events as well as focus events.
_Example_: 
```html
<button onclick="sayHello();">
```
It's apparently pointing to the window object, so why is that? Well, since this sayHello function is being defined in the global context, it makes perfect sense that when we say this, this will be pointing, again, to the global context, which is the window object.

By assigning this to this onclick attribute. We're not doing anything at all to change that context for this hello function. We actually are executing it right here. So that remains the same. However, there's a different way of doing the same thing. That is binding this function to the click-event. In this way it's called ==unobtrusive event binding==. And the reason that's called that way is because the HTML doesn't really need to know anything about your JavaScript.

```js
// Unobtrusive event binding
document.querySelector("button")
.addEventListener("click", sayHello);
```
`this` now is pointing to the actual button. So, and that makes perfect sense since we're passing the value of this function ("sayHello")into addEventListener. 
![[Pasted image 20211222092754.png|200]]
### 3.3 Event Argument

```js
function sayHello(event)
```
