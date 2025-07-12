# L3.1 - Live + Implementation

## What is fronted?
* User-facing part of app
	* UI and UX
* Requirements
	* Avoid complex logic - application logic should be in backend
	* No data storage
	* Work with stateless nature of HTTP
		* Messages exchanged between server and view are stateless
		* Protocol is stateless itself, website can be handled to be stateful
* Desirable
	* Aesthetically pleasing
	* Responsive - no lag/latency
	* Adaptive - different screens

## Programming Styles
* Imperative: Sequence of actinos to achieve final result
	* Draw boxes for navigation, main text, fill in text, wait for clicks, etc.
	* Functions for each step, composition of functions
* Declarative: Specify desired result
	* Compiler/Interpreter knows how to achieve result
	* Function integration automated

## Flutter 
* Start thinking declaratively

UI = f(state)
* UI -> Layout of the screen
* f -> build methods
* state -> application state

## State
* Internal details of the system: memory
* Reproducibility
	* Given a "system state", the system should always respond the same way to the input
* Complexity
	* Any non-trivial application needs internal state

## System State
* Complete database of amazon, flipkart
	* Stocks of available items, prices, logged in/registered users, etc.
* All new articles ever published
* All students, courses, marks, certificates for NPTEL

Typically huge, but comprehensive, completely independent of the user interface

## Application State
Application:
* System as seen by an individual user/session
* Includes interactivity, session management
	Examples:
	* Shopping cart
	* Dashboards 
	* FYP etc

## UI state (Ephemeral State)
Ephemeral - Lasting for a very short time
* Part of the application actually seen/interacted with

Eg: Loading icons, Currently selected tab etc


## Application and UI management
* HTTP is stateless
* How to convey state between client and server?
	* Client maintains state - sends requests to server for specific items
	* Server maintains state - only specific requests allowed to client

## Example # 1 Tic-Tac-Tow
* What to display on screen?
* Who determines the display
* How should user input be collected and processed?

Will be done on Vue.js, just basic babysteps


## Vue Framework
* 