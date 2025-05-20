# L1.1 Review
## Review of MAD1
* What is app?
	* application to interact with computer
	* allow user to perform some tasks useful
* components
	* Backend, frontend, architecture
* Why web
	* close to universal platform
	* low barrier to entry
	* high flexibility

## Moving forward

* Advanced fronted
	* JavaScript
	* JS, API, Markup - JAMStack
	* VueJS as a candidate fronted framework
* Other topics of interest
	* Asynchronous messaging, Email
	* Mobile, standalone apps
	* Performance measurement
	* Alternatives to REST

# L1.2 - JS Origins 

## Origins
* Originally created in 1995 as scripting language
* Intended as Glue language (stick modules from other languages)
* primarily meant to assist applets  
* Evolved true web applications that behave like desktop  applications
* In practice called ECMAScript

## Implications
* Ease of use
* Highly tolerant of errors
* ambiguous syntax
* limited IO support - errors logged to console
* closely integrated with presentation layer - DOM APIs
* Asynchronous processing and the Event Loop 


## Using JS
* Note originally meant for direct scripting
* Need HTML file to load the JS
* NodeJS allows execution from command line
* most examples here used will be replit

## DOM
* Document Object Model
	* Structure of the document shown on the browser
* DOM can be manipulated through JS API
* One of the most powerful aspects of JS
* Input: clicks textboxes, mouseover
* Output: text, colours/styles, drawing

# L1.3 - Basics of JS

## Basic frontend Usage
* Frontend: Must be invoked from HTML page
	* In context of a "document"
	* will not execute if loaded directly
* Scripting language - no compilation
* loosely structured - no specific header

## Identifiers
* Reserved words:
	* if else import in instance let new return static etc.
* Literals (values):
	* true, false, null
* Others to avod
	* eum implements pachake protected interface etc.

## Statements and Expressions

```
# Statement: Piece of code that can be executed
if(...) {
	// do something
}

# Expression: Piece of code that can be executed to obtain a value to be returned
x = 10;
```

## Data Types
* Primitive data types
	* undefined, null, boolean, number string (bigint,  symbol)
* Objects
	* Compound pieces of data
* Functions
	* Can be handled like objects
	* Objects can have function
	* Function can have objects

# L1.4 Identifiers, Expressions and Variables
## Comments
* // - single line
* /* ... */ - multiline

## Identifiers
```
let x = 0;
const variable = 1;
var abc = 2;
```
### Scope:
* concepts of namespaces, defines and limits scope
* var -> declares the scope for the entire program (GLOBAL SCOPE)
```
# this below program will print
{
	var x2 = 1;
}
console.log(x2)
```
* let -> limits scope to the most recent opening and closing curly braces (BLOCK LEVEL SCOPE)
```
# this below program will run into a reference error
{
	let x2 = 1;
}
console.log(x2)
```
* Even const works the same as let but it is a constant cannot be modified later in the program

### Strings
* string has
	* console.log(s)
	* s.length
	* s[1]
	* s.substring(2,4)
#### Formatting strings
```
let s = "abc";
let st = `${s}, def` // should use backtick ` here
console.log(`Length of ${st} = ${st.length})
```

## Operators
### Arithmetic
* + - * / the usual
* + does concatenation if string is given

### Relational
* Loose equality
	* '3' == 3 -> True
* Strict equality
	* '3' === 3 -> False

# L1.5 

## Non-values
* undefined
	* usually implies not initialized
	* Default unknown state
* null
	* explicitly set to a non value
	(If initialized an array, the elements in that are undefined)

## Control flow
* Conditional execution
	* if, else
* Iteration
	* for, while
* change in flow
	* break, continue
* switch

## Functions
* Reusable block of code
* functions are objects
![[Pasted image 20250521014910.png]]
functions can have objects within them
```
add.v = {'a':  1}
console.log(add.v.a)

// will output 1
```

# L1.6 - DOM API
## Interaction
* console.log very limited
	* mostly for logging and debugging
* JS designed for document manipulation
* Inputs from DOM: mouse, text, clicks
* Outputs to DOM: manipulation of text, colours, etc.

```
//HTML
<div id='d1'> <div>
<div id='d2'> <div>

//js
const d1 = document.getElementById('d1')
d1.innerHTML = 'welcome'

# document here is a global variable, no need to declare
```