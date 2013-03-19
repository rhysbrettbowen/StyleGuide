# JavaScript Style Guide #

## Linting ##

JSHint should be used to lint your javascript. See the Appendix for a .jhintrc file

## Spacing ##

- indentation with space
- indent to 4 spaces
- no blank spaces at the end of a line
- `if/else/for/while/try` should have a space between the name and parenthesis
- there should be no space (line break excepted) after an openning parenthesis or before a closing parenthesis

```
// BAD
if(true)

// GOOD
if (true)
```

- there should always be a space or new line after a comma

```
// BAD
myFn(a,b);

var obj = {a:1,b:2};

// GOOD
myFn(a, b);

var obj = {a:1, b:2};
```

## Line Breaks ##
- functions, arrays and object literals with more than one item should have each item on a new line:

```
// OKAY
var a = function(a) {return a};
var b = ['first element'];
var c = {a: 1};

// BAD
var a = function(a) {a++; return a;};
var b = ['first element', 'second element'];
var c = {a: 1, b: 2};

// GOOD
var a = function(a) {
	a++;
	return a;
};
var b = [
	'first element',
	'second element'
];
var c = {
	a: 1,
	b: 2
};

```

## semicolons ##

always.

## code blocks ##

- openning curly brace should go at the end of the line beginning the statment preceded by a space
- right curly brace should be indented to match the begginning of the line with the openning curly brace
- braces are optional but encourage for single statements

```
\\ BAD
if (statement)
{
	doStuff();
}

\\ GOOD
if (statement) {
	doSftuff();
}

\\ OKAY
if (statement)
	doStuff();
```

- else statements should go on the same line as the preceding curly brace with a space preceding or for single statements on the line after the single statement
- if either the if or else statements are more than one line, BOTH must use curly braces

```
\\ BAD
if (statement) {
	doStuff();
}
else {
	otherStuff();
}

if (statement) {
	doStuff();
}else {
	otherStuff();
}

if (statement) {
	doStuff();
	doStuffAgain();
} else
	otherStuff();


\\ GOOD
if (statement) {
	doStuff();
} else {
	otherStuff();
}

if (statement) {
	doStuff();
	doStuffAgain();
} else {
	otherStuff();
}

\\ OKAY
if (statement)
	doStuff();
else
	otherStuff();
```

## Object literals ##

- All object keys should be followed immediately by a colon then a space

```
// BAD
{a:1};
{a : 1};

// GOOD
{a: 1};
```

- object literals with more than 10 keys that wary in length by more than 4 characters should have the values aligned the the next tab stop after the longest key

```
// GOOD
{
	a:                	as.fsdf,
	abbasdf:			function() {},
	fergwerg:			'sdfsd',
	gewrf:				2344,
	erwtewrtewrgdfv:	12,
	werferf:			sdfsdf,
	ewrtwertewe:		23432,
	wertewt:			vs,
	wert:				function() {},
	werhywrtgrw:		null
};
```

- commas go at the end of the line
- properties should be declared without quotes. If quotes are needed then the property should be declared after the literal:


```
// BAD
var obj = {
	a: 1,
	'false': false
};

// GOOD
var obj = {
	a : 1
};
obj['false'] = false;
```

- access properties using dot notation if the property is *internal to the program* or not computed

*a property is internal when it was defined by another javascript file, it is external if it was json brought in by the API or typed from a user*

```
var person = {
	name: 'Jake'
};

// BAD
person['name'];

// GOOD
person.name;

var json = $.ajax(...);

// BAD
json.results;

// GOOD
json['results'];

```

## variable declaration ##

- each new variable should have it's own var

```
// BAD
var a = 0,
    b = 1;

// GOOD
var a = 0;
var b = 1;
```

- variables can only be declared in statements or code blocks if they are not used beyond the block

```
//BAD
for (var a = 0; a < 10; a++) {
	console.log(a);
}
b = a;

// GOOD
var a;
for (a = 0; a < 10; a++) {
	console.log(a);
}
b = a;

// BAD
if (test) {
	var a = 10;
} else {
	a = 20;
}
console.log(a);

// BAD
var a;
if (test) {
	a = 10;
} else {
	a = 20;
}
console.log(a);
```

- declare variables at the top of code blocks or at the top of a function

```
// GOOD
while (true) {
	var temp = a;
	a = b;
	b = temp;
}

// BAD
function() {
// other statements
	var a;
	if (test) {
		a = 10;
	} else {
		a = 20;
	}
	console.log(a);
}

// GOOD
function() {
	var a;
	// other statments
	if (test) {
		a = 10;
	} else {
		a = 20;
	}
	console.log(a);
}
```

## strings ##

- use single quotes for strings that are not designed to change, double quotes for templates and strings that will be joined

```
// BAD
var status = {
	start: "start",
	load: "loading",
	done: "finished"
};

var str = 'my name is: ' + name;

// GOOD
var status = {
	start: 'start',
	load: 'loading',
	done: 'finished'
};

var str = "my name is: " + name;
```

- long strings should be broken up on to multiple lines with pluses

```
// BAD
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// BAD
var errorMessage = 'This is a super long error that \
was thrown because of Batman. \
When you stop to think about \
how Batman had anything to do \
with this, you would get nowhere \
fast.';

// GOOD
var errorMessage = 'This is a super long error that ' +
    'was thrown because of Batman.' +
    'When you stop to think about ' +
    'how Batman had anything to do ' +
    'with this, you would get nowhere ' +
    'fast.';
```

## functions ##

- imediately invoked funtions should have brackets areound the declaration:

```
// GOOD
(function () {
	execute();
})();
```

## Naming ##

- use camelcase for naming

e.g. `myVariableName`

- constructor functions should have first letter uppercase

e.g. `MyClass`

- all caps with underscore between words for constants

e.g. `GRAVITY_ON_MARS`

- private variables should have a preceding underscore

e.g. `_myPrivateVariable`

- prefix methods with `get/set` then the variables name with first letter uppercased for accessing variables

```
var obj = {
	name: 'Fred',
	getName: function() {
		return this.name;
	},
	setName: function(name) {
		this.name = name;
	}
}
```

- prefix with `is\has` if function returns a boolean

```
var obj = {
	isSelectable: function() {
		return !this.disabled && this.selectable;
	},
	hasName: function() {
		return !!this.name;
	}
}
```

- use plural with collections
- iterator variables should be `i,j,k` and can be reused

## prototype ##

- set each value on the prototype individually or use `_.extend`

```
\\ BAD
function A() {};
A.prototype = {
	a: 1
};

\\ GOOD
function A() {};
A.prototype.a = 1;

\\ GOOD
function A() {};
_.extend(A.prototype, {
	a: 1
};
```

## Backbone Mixins ##

- prefer the use of `mixin` to `extend`
- always use an `extend` before using the mixin function
- prefer to use functional mixins to objects (so they aren't applied more than once)

## this ##

- bind a function when you need to preserve context

```
// BAD
var that = this;
var myFn = function() {
    that.talk();
};

//GOOD
var myFn = _.bind(function() {
    this.talk();
}, this);
```

## truthiness ##

- if testing that an array or object has data use _.isEmpty from underscore.extra

```
isEmpty: function(obj) {
  return !!(obj === undefined || obj === null ||
    (_.isObject(obj) && !_.keys(obj).length) ||
    (_.isString(obj) && !obj.length));
}
```

- loose equality is allowed but strict equality is preferred
- you can check for null and undefined like so:

```
undefOrNull == null;
```

## Type checking ##

- use underscore methods for type checking

## comments ##

- for comments at the start of a method use JSDoc tags (starting with /**)

```
/**
 * adds two numbers together
 */
function add(a, b) {return a + b;};
```

- optionally use Closure annotations for functions: https://developers.google.com/closure/compiler/docs/js-for-compiler
- multi-line comments should use /* */
- commented out code should use //

## Appendinx ##

.jshintrc

put this file in your root workspace so jshint can lint your work:

```
{
	"bitwise": true,
	"camelcase": false,
	"curly": false,
	"eqeqeq": false,
	"forin": false,
	"immed": true,
	"indent": 2,
	"latedef": true,
	"newcap": true,
	"noarg": true,
	"noempty": false,
	"nonew": true,
	"plusplus": false,
	"quotmark": true,
	"undef": true,
	"unused": true,
	"strict": false,
	"trailing": true,
	"maxparams": 6,
	"maxdepth": 4,
	"maxstatements": 100,
	"maxcomplexity": 10,
	"maxlen": 120,
	"asi": false,
	"boss": true,
	"debug": false,
	"eqnull": true,
	"es5": false,
	"esnext": false,
	"evil": false,
	"expr": false,
	"funcscope": false,
	"globalstrict": true,
	"iterator": false,
	"lastsemic": false,
	"laxbreak": false,
	"laxcomma": false,
	"loopfunc": false,
	"multistr": false,
	"proto": false,
	"scripturl": true,
	"smarttabs": false,
	"shadow": true,
	"sub": true,
	"supernew": true,
	"validthis": true,
	"devel": false,
	"jquery": true,
	"globals": {
		"require": true,
		"define": true,
		"Backbone": true,
	},
	"browser": true
}
```