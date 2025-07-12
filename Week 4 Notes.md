# Live Session
## Declarative Rendering
* Reactivity
* Directives
* Event Handling
* Class and Style binding
* Lists and Loops

## Reactivity
* Auto update in reponse to changes in data
* Binding between model (data) and view (display)
Focus on **What** instead of **how**

## Why?
* User interaction is reactive
	* responsive to changes in input
* Change in one parameter may need multiple updates on screen
	* User logs in 
	* navigation
	* courses 
	* themes etc

## How?
* Server tracks state
	* user logged in?
	* date/time?
* Server responds with complete HTML based on present state
	* Capture different layouts, visibility in views
	* Render appropriately for each user
	* Fully server side
* Client-JS
	* Login controller retreives user model
	* Client side JS goes through each element and updates as needed 

## Vue Directives
* v-bind: one way binding - update variable, reflects on display
	* v-model: two way binding - inputs, checkboxes, etc form data
* v-on: event binding

## Class binding
* Dynamically modify class of an element
* Special support for bind-object
* Multiple classes attached based on key-values
	* If value for a given key is true, that key is applied as a class or style

## Conditional Rendering
* v-if="argument"
	* shown when argument evaluates to true
	* JS Based - changes DOM
* v-show="argument"
	* only if the show parameter evaluates to true
	* always render and present in DOM, only css display parameter changed

## Looping
* Iterate over any JS iterable
	* array, object, string etc
* Usage similar to Jinja templates
* Examples:
	* v-for="item in items"
	* v-for="value in obj"
	* v-for" (value, name) in obj"

## Loop Keys
* Looping "creates" new DOM elements
	* Vue needs some way to keep track of elements if updating needed
	* Virtual DOM diffing used to find what changes to reflect on screen
	* Vue uses heuristics to see what can be minimized
* For simple updates, simple heuristics are sufficient
	* For more complex updates, may not be easy to track what has changed or what is new
* provide a "key"
	* Key must be unique for each loop element
	* Updating item with same key will automaticallly update only relevant items
* Rule of thumb: provide a key where possible - index, ID etc

## View Model
sometimes view needs more into than needed for model or there is derived information

**Example**
* Form with username , password and repeat password
	* repeat password shouldn't be stored in the server?
* page with top comments, top posts
	* Should the top comments and posts be in model

## Vue Instance
Data binding: data os vue instance is the instance data
update to data will be reflected in the view
Update in the view can change the data

MVVM - Model, view, viewmodel (web app on browser)

### Controller:
* Convey actions to model
* Call appropriate view based on inputs and model

### View Model
Create framework for data binding
can still use controllers to invoke actions

## Computed Properties
* Often need to work with *derived* data
	* Take original data and modify it according to some function/logic
	* Examples: boolean on-off on styles depending on values in data; navigation links depending on history
* Computed properties
	* Auto update
	* cached based on their reactive dependencies
Computer "setter" also possible, need to check documentation

## Watcher
* Explicitly look for changes
* Can be used for imperative code
* For more complex logic than just updating a property
When possible, use computed property instead of watcher
* More declarative
* caching

## Caching
set variables in the compute that's stored in the background

# Components
## Reuse
* DRY principle: Don't Repeat yourself
* Same structure, formatting, repeated

## Refactor
* Change code without changing functionality
* Mainly for readability and maintainability - not functionality


## Vue component Structure
* Properties
	* passed down from parent - customize each instance
* Data:
	* Individual data of the present instance
	* Also it's own watchers, computed properties
* Template
	* How to render - possible with render functions
	* Slots

## Templates
* {{}} format - similar to Jinja
* Safety features:
	* will not interpolate text into tags
	* errors on unclosed divs
* More complex render functions possible
	* JSX - mix JS + HTML - similar to React

## Slot
* Main element of text:
	* use like reglar tag
	* properties can be defined in tag 

# Reactivity
## How does reactivity work?
* Need to track whend ata is
	* accessed
	* modified
* Add methods to objects
	* Everything in JS is an object
Object.defineProperty()

```
const data = {
	count: 10
};

const newData = {}

Object.defineProperty(newData, 'count', {
	get() { return data.count; },
	set(newValue) { data.count = newValue; }
})

console.log(newData.count);

newData.count = 20;
```

# Screencast 4.1 - Components in VueJS

Nothing new to add here, pretty much what was there in the previous 2hr cast, if anyone interested in adding notes for here, please do so. JavaScript is so incredibly boring.