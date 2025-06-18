# L2.1 - Intro to JS Collections

## Basic arrays
* Collection of objects of any type
* Element access
* Length
* Holes
* Iteration

## Iteration
* Go over all elements in a collection
* Concepts: 
	* Iterable: an object whose contents can be accessed sequentially
	* Itterator: Pointer to the next element
* Iterable objects:
	* Array
	* String
	* Map
	* Set
	* Browser DOM - Tree structure
* Objects: object.keys(), object.entries() - helper function 

## Iterations and Transformations
* Functions can take functions as an input
* map, filter, find
	* apply a callback function over each element of array
* Elements of functional programming: create a transformation chain

### Callback
important concept - function passed in to another function, to be called back for some purpose

## Other collections
* Maps: proper dictionaries instead of objects
* WeakMaps
* Sets

## Destructuring
* Simple syntax to split an array into multiple variables
* Easier to pass and collect arguments
* Also possible for objects

## Generators
* Functions that yield values one at a time
* Computed iterables
* Dynamically generate iterators
basically returns something from the function without ending it. It returns saves that state and then continues from there to return the rest of the values. Helps with like functions beside one another. one returns but doesn't exit, and wait for the other to return before proceeding. Both are active and running concurrently

# Java Basic Calculator
![[calculator.html]]

# L2.2 - Iterations and Destructuring

## Iterations
```
# Mode 1
let x = [1, 'b', a=>a+1];
x.length = 5;
for (let i =0; i < x.length; i++) {
	console.log('x ${x[i]} of type ${typeof(x[i])})
}

# Mode 2 - "in" iterator, skips undefined types
for (const i in x) {
	console.log('x ${x[i]} of type ${typeof(x[i])})
}

# Mode 3 - "of" iterator, prints undefined type as undefined
for (const i in x) {
	console.log('x ${i} of type ${typeof(i)})
}
```
Are objects iterable?
```
let x = ['b': 1, 'c': 3]

# mode 2 interator - in
# This will print the values in the Dictionary
for (const i in x) {
	console.log(i)
}

# Mode 3 interator - cannot iterate
for (const i of x) {
	console.log(i)
}

# New mode
for (const [k, v] of Object.entries(x)) {
	console.log(k, v);
}
```

Creating a new array with holes
```
let x = new Array(5)
x[1] = 10;
x[3] = 'hello';
for (const [k, v] of x.entries()) {
	console.log('Index ${k}, value ${v}')
}

# except for 1 and 3 rest all will print undefined
```

Spreading: spreads out the data, basically in between concatenation
```
let x = [1,2,3];
let y = [0, ...x, 4];
console.log(y)

# outputs 0,1,2,3,4,5
```

Iteration and Transformation
```
let x = [1,-2,4,5,-6]
let y = x.find(t => t < 0)
console.log(y);

# outputs
-2

# Finds the first element where the condition is correct

# Instead

console.log(x.filter(x => x < 0))

# Shouldn't use this normally under any other circumstance
# But in this context the above outputs [-2, -6]
```

Map Function: Maps to each part of an array
```
console.log(x.map(i = > i > 0 ? 1 : 0))

# output: 1, 0, 1, 1, 0
```

Another example
```
console.log(x.reduce((a,i) => a + i, 0))
# Adds the address value to the value
```

## Sorting
```
# Outputs the sorted list in a lexicography format
so the output witll look like [-2, -4, -7...]

console.log(x.sort());


# sorting a list of numbers by converting the strings to numbers using iterations

console.log(x.sort((a,b) => a-b))
```

## Destructuring
```
let x = [1,2,3]
[a, b] = x;
console.log(a, b);

outputs: 1 2
```

What in the fuck only language this is goddamn wtf
![[Pasted image 20250616222121.png]]

# L2.3 - Modularity
## Modules
* Collect related function, objects, values together
* "export" values for use by other scripts
* "import" values from other scripts, packages

### Ways of implementing
* script - direct include script inside browser
* CommonJS - introduced for server side modules
	* synchronous load: server blocks till module loaded
* AMD - Asynchronous module definition
	* Browser side modules

ECMAScript 6 and above:
* ES6 modules
	* Both servers and browsers
	* Asynchronous load

## Node Package Manager (NPM)
* node
	* command line interface for JS
	* mainly used for backed code, can also be used for testing
* npm can also be used to package modules for frontend
	* "Bundle" managers - webpack, rollup, etc

example
file 1 - module1.js
```
function sq(x) {
	return x * x; 
}

export const c = 300000000
export function energy(m) {
	return m * sq(c);
}
```
file 2 - module2.js
```
import {c, energy} from './module1.js'

# this will work
console.log(c)

# this won't work as it was not imported, just an internal function
console.log(sq(10))

# This will work as the function was imported
console.log(energy(10))

----------------
# can also rename imports
import {c as speedoflight} from ...
```
exports can also be renamed
```
const speedoflight =300000000;
function e(m) {
	return m * sq(speedoflight);
}

export {
	speedoflight as c,
	e as energy
};
```

importing default expert
```
# module2.js
import energy from './module1.js';
console.log(energy(10))

# module1.js
export default function (m) {
	
}
listen to me, you will lose this and your time, you might as well just let it go, and go back to being nice or else another of your days will be gone you crzy fuck. she's the crazier fuck that you can't win against. Literally insane person. You cannot fuckingn win. Let it go. Let it fucking go you psychopath. Bro I know you are getting that itch but please please please do not mess it up. Just let it be peaceful. please I beg you. you feel even more resentful cuz you're so tired, please shut the fuck up. please. please please nigga please. Bro shut up please. please. let it be now

```

read only variable imports
```
# module1.js
export let x  = 0
export function incx() {
	x++;
}

# module2.js
import {x, incx} from './module.js';
console.log(x);
x++;
incx();
console.log(x)
```

## Objects
* Everything is an object
* Object literals
	* Assign values to named parameters in object
* Object methods
	* Assign functions that can be called on object
* special variable this
* function methods
	* call(), apply(), bind()
* object.keys(), values(), entries()
	* use as dictionary
	* iterators

## Prototype based inheritance
* objects can have a "prototype"
* Automatically get properties of parent
* Single inheritance track (no multiple inheritance in other languages)

## Class
* Better syntax - still prototype based inheritance
* constructor must explicitly call super()
* Multiple inheritance of Mixins
	* complex to implement - out of scope here
```
xx = {'a': 1, 'b': 2};
xx.f = function(x) {
	return this.a + x;
}
```

# L2.4 - Function Methods, Prototypes and Classes
## Methods
```
# Get and set properties
let user = {
	first: 'albert',
	last: 'pinto',
	get full() {
		return this.first + ' ' + this.last;
	},
	set full(f) {
		const parts = f.split(' ');
		this.first = parts[0];
		this.last = parts[1];
	}
}
```
you can even initalize a function into a function object. WHAT? What is what? huh? what? what the fuck what in the actual fuck is wrong with the people who made this language. I get the hate for this fucking language now.
```
let xx = {
	'a': 5,
	'b': 'hello',
	'add': function (x,y) {
		return x + y + this.a;
	}
}

let z = xx.add;

# this works
console.log(z.call(3,4));

# this don't work
console.log(z.call("", 3, 4))

# this works again
console.log(z.call(xx, 3, 4))

# What in the actual fuck is this language?

# can also use an apply function
console.log(z.apply(xx, [1,2,3,4]))
# The above just spreads out the list into the arguments

# there's also a bind function
let z2 = z.bind(xx, 2)
console.log(z2(3))
```

## Prototypes
```
const x = {a: 1, inc: function() { this.a++; }};

console.log(x)
# output: same as RHS of x

const y = {__proto__: x, b: 2};

console.log(y)
# output {a:1, inc: [Function]} {b: 2}

console.log(y.a);
y.inc();
console.log(y.a);

#output: 2
```

# Classes
```
Class Animal {
	constructor(name) {
		this.name = name;
	}
	describe() {
		return this.name + this.sound
	}
}

# Inheritance works here
Class Dog extends Animal{
	constructor(name) {
		super(name);
		this.sound = "Woof";
	}
}

let d = new Dog("spike")
console.log(d.describe());
# output: spike woof

# Another type of inheritance
class Cat extends Animal {
	constructor(name) {
		super(name);
		this.sound = 'meow';
	}
	static fromJson(o) {
		# basically creating a new object, modifiyng it and then initializing into this object
		c = new Cat(o.name);
		c.sound = o.sound;
		return c;
	}
}

let x = new  Cat("Tom");
console.log(c.describe());
```

# L2.5 - Asynchrony
multiple things can happen without being in sychronous with each other.
## Function calls
* Function is like a "branch"
	* but must save present state so we can return
* Call stack
	* Keep track of chain of functions called up to now
	* Pop back up out of stack
	* Example
		* main on stack - current - calls f()
		* f() goes on stack - calls G()
		* g() goes on stack - calls h()
		* h() goes on stack - executes
		* return from h -> pop into g
		* return from g -> into f
		* f -> main

## Event Loop and Task Queue
* TAsk queue: store next task to execute
	* tasks are pushed into queue by events 
* Event loop
	* Wait for call stack to become empty
		* Pop task out of queue and push it onto stack, start executing
* Run-to-completion
	* Guarentee from JavaScript runtime
	* Each task will run to completion before next task in invoked
![[Pasted image 20250618160511.png]]

## Callbacks
* long running code
	* Will block execution till it finishes
* Push long running code into a separate thread or task
	* let main code proceed
	* Call back when completed


# L2.6 - JSON API
## Json
* Object notation - for serialization, communication
* Notation is frozen
	* Means even problem cases will remain
* Usage through JSON API

## Json API
* global namespace object JSON
* Main methods
	* JSON.stringify()
	* JSON.parse()
```
let c = new Cat("Tom");

let p = JSON.stringify(c);

# only outputs the string
console.log(p)

# outputs whole object
console.log(c)

let cc = Cat.fromJson(JSON.parse(p));
console.log(cc.describe())

```