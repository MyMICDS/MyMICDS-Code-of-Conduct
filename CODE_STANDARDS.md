-whether or not camel case acronyms
-tabs
-whitespace between variable names and shiz

# Coding Standards

While communication is also important, so is creating clean, consistent, and maintainable code. These guidelines should help establish clear consistency between all code written for MyMICDS.

## Coding Style

- [**ALWAYS USE TAB INDENTATION**](https://github.com/MICDS-Programming-Club/Programming-Club-Guides/blob/master/introduction/tabs_vs_spaces.md)
	- Convert all files (even if auto-generated) to tabs unless they are changed often by programs (**don't** `package.json`, **do** `.angular.cli.json`, etc.)
- Variables
	- Spaces between variable names, math operators, between elements in objects/arrays
		```javascript
		const something = (a ** 2) * 4;
		const another = [0, 1, 2, 3];
		```
		- Space at beginning/end of objects
			```javascript
			doSomething({ hello: 'world' });
			```
- Statements
	- Space between parenthesis in `if/else`, loops, and `switch`
		- Not between function name and parenthesis
	- Braces on same line and space between
		```javascript
		if (condition) {
			// ...
		} if else (condition) {
			// ...
		} else {
			// ...
		}
		```
- Clarity
	- Add parenthesis to math/complicated boolean expressions for additional clarity, even if it works without them.
		```javascript
		const mathematics = (5 * x) + 4;
		const isChecked = (checkedState === boxState);
		```

Here is sample code trying to show all rules in action. This is acceptable code:

```typescript
// JavaScript imports
const fs = require('fs');
const { ObjectID } = require('mongodb');

// TypeScript imports
import { Component } from '@angular/core';
import {
	What,
	To,
	Do,
	If,
	Imports,
	Exceed,
	Line,
	Length
} from './package';

// Always prefer declaring functions in file compared to assigning an anonymous function to a variable
// Camel case for functions and variables
// No space between function name and parameter parenthesis, but yes before curly braces
function test(x, y) {

	// Assign anonymous functions to variables only if within another function
	const iterator = i => {
		if (i >= 10) {
			return;
		}
		switch (i) {
			case 0:
				console.log('First iteration!');
				break;
			case 1:
				console.log('Second iteration!');
				break;
			default:
				console.log(multiply(i))
				// Include break even for last switch case (default or not default)
				break;
		}
		iterator(++i);
	}
	iterator(0);
}

// More basic or primitive functions should be placed lower in the code file (especially if used by other functions)
function multiply(x) {
	// Always prefer const over let or var
	const y = 2;
	// Only use let if you are (or might) change value
	let z = 1;
	if (x === 5) {
		// Put zero before decimals
		z = 0.5;
	} else if (x > 6) {
		z = 9;
	}
	return x * y * z;
}

// Class names camel case but first letter capitalized
class Something {

	// Declare instance variables first, then constructor, the methods, then static classes
	// If type is already implied from value, don't specify type (https://palantir.github.io/tslint/rules/no-inferrable-types/)
	hello = 'world';
	isChecked = false;
	direction: DIRECTION = null;

	// Notice space in between empty brackets, same line if empty
	constructor() { }

	// Keep function parameters on same line until line exceeds max length (includes functions, methods, constructors)
	method1(x: number, y = 2, z?: string) {
		// Implementation
	}

	// When line exceeds max length, each parameter should be on separate line like so:
	static method2(
		if: string,
		theres: any,
		a: boolean,
		lot?: object,
		of = {},
		parameters?: any
	) {
		// Implementation
	}

}

```

## Terminology

This should be used for naming things, comments, etc.

### Scheduling

A `class` (or `scheduleClass` where languages prohibit `class` as a keyword) contains information about a user's class. This includes class name, block period, color, teacher, etc., but does **not** refer to a specific period it meets (ex. no start or end time).

A `block` is comprised of a `class` and a `start` and `end` time.
