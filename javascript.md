## JavaScript: Novice to Ninja, 2nd Edition

#### Preface
- Exponential growth, unrelenting barrage of new JavaScript tools and methodologies known as "JavaScript Fatigue"
- New version scheduled for release every year
- Babel (JS compiler) + Node.js (JS runtime environment, interpreter + many compilers + optimizations) helped ES6 gain huge traction
- Functions are first class members!
- Lacking though, i.e., modules and private functions don't exist yet

#### Chapter 1
- JS, the language of the web
- Nearly all web browsers can run JS
- Type checking happens at runtime
- Interpreted and compiled using an "engine"
  - Firefox, Chrome, Safari have this engine built in
  - Can also use Google V8 outside of browser
  - Some engines have JIT compiler
 
###### History of JS
- Dude hired by Netscape to write a language to enhance the early web, was about Netscape vs Microsoft
- Wrote JS in just 10 days, borrowed elements from AWK Java Perl Scheme HyperTalk and Self
- Mocha -> LiveScript -> JavaScript
- JS and Java totally unrelated but share some syntatic things.
- Released in 1995
- Microsoft reverse engineered JS and made JScript (basically the same thing as JS) and VBScript, both run inside Internet explorer
- Low barrier to entry = bad programmers. JS responsible for adverts and browser sniffing (detecting what browser you're using)

###### The Browser Wars
- NetScape Navigator 4 vs Microsoft Internet Explorer 4
- Both had proprietary features, meant JS had to be written in two versions to run in multiple browsers
- IE won, then came Firefox (2002, open source browser) and Apple's Safari (2003)
- Web Standards Project (WaSP) standardized JS and browsers, merging the branches of JS and Browsers back into one

###### Web 2.0
- Gmail, Google Maps, Flickr come along and show JS is really capable
- term Ajax (Asynchronous JavaScript and XML) is introduced, means
  - obtaining data from server in background
  - only updating certain parts of the page without full reload
  
###### Standards
- New Web war, this time for which browser is most standards compliant
- Speed of JS in browser, Chrome comes along with V8 engine and destroys competition
- Eventually, competition catches up and now all browsers are super fast

###### Node.js (2009)
- Allows server-side apps to be written in JS
- Based heavily on Google V8
- Don't even need a browser anymore, JS can be used anywhere
- Isomorphic JS, don't need a server anymore! Code can be run on client (or server)

###### JS versions
- 1996, Netscape + Sun standardized the language, called it ECMAScript
- A lot of confusion, but ECMAScript = spec, JS = language itself
- ECMAScript means all browsers and engines run JS the same way
- But actually, they don't, so implementations of JS vary from engine to engine
- JS is a superset of ECMAScript. i.e, contains non-standard features like `alert()`
- ECMAScript maintained by Technical Committee 39 (TC-39). People from:
  - Apple
  - Google
  - Microsoft
  - Mozilla, and 
  - various other experts
- ES1 (1997)
- ES2 (also 1997, no major changes)
- ES3 (1999, a lot of new features)
- ES4 (died because TC-39 couldn't come to an agreement on what to include)
- ES5 (2009, many new features, but much less ambitious than ES4)
- ES6 (2015, decided to rename to ES2015, ES2016, etc. new releases every year)

###### Future of JS
- Currently, really exciting time for JS
- SPA (single page applications) run in browser and rely heavily on JS
- PWA (progressive web apps) use web technologies to make apps that behave like one on a mobile phone ( no app store necessary)
- HTML5 games use JS extensively
- Browser extensions, Windows Desktop widgets, Chrome OS applications
- Adds interactivity to PDF docs, interact with DB, control household appliances

Browser + text editor is bare necessities, but ideally install Node.js

- open powershell
- `Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force`
- `npm install -g npm-windows-upgrade`
- `npm-windows-upgrade`

to start the node REPL (interpreter), `node` in cmd
OR, `F12` in browser
OR, https://www.es6.console.com

###### Three layers of the Web
- Nearly all web pages made up of HTML + CSS + JS
- Each layer builds on the other
- Web page should be able to function just fine with just HTML, most barebones
- Otherwise, causes 'code soup' or 'code of spaghetti'

- Graceful Degradation: building web app so it works best in modern browser but still works fine in older ones
  - like HD tv shows, work great in HD tv but still work on SD tv
- Progressive Enhancement: building web page with base functionality, then adding extra enhancements

###### Don't Break the Web
- All JS code needs to be backwards compatible
- Means JS can't do anything that isn't already possible in previous versions, only adds syntactic sugar
- Also means we can transpile JS5 code into JS3 code
- Since JS comes out new version every year, will probably need to use transpiling tool (Babel) at some point. 
- otherwise, browsers will not be able to run latest and greatest JS features
`<script src='https://unpkg.com/babel-standalone@6/babel.min.js'></script>`
`<script type='text/babel' src='main.js'></script>`

#### Chapter 2

- can use semicolons, or no semicolons - doesn't matter
- but semicolons is considered best practice
- can use as much whitespace (tabs, spaces, new lines) to separate different parts of each statement

###### Scope
- `const` and `let` are used to block scope variable declarations and assignments
- `var` is function scoped

`const` used to make primitives immutable
primitives:
- String
- Symbol
- Number
- Boolean
- Undefined
- Null

primitives are assigned by value, non-primitives assigned by reference
variables that start with _ are generally private properties/methods - do not start my own variables with _!!!

$ is used by jQuery library, do not use this for my own variables

escape character is \
so "it's me" is the same as 'it\'s me'
\n end of line
\r carriage return
\t tab
to write backslash, \\

Usually, only objects have properties and methods.
But in JS, primitive data types are wrapped in wrapper objects, so even primitives have properties and methods (kind of like Java)

good habit to use const keyword to declare variable names

Symbols are used to store string values. New Primitive in ES6. Must be unique. Used for properties to ensure property names do not clash.
###### Numbers
Numbers can be integers or floating point numbers. JS does not distinguish between ints and floats, both are just called numbers.

- _0x_ AF is hex
- _0o_ 47 is octal
- _0b_ 1010 is binary

5..toExponential();
> "5e+0"
OR

5 .toExponential();

OR

5.0.toExponential();

OR

(5).toExponential();

OR

`const number = 5;`
`number.toExponential();`

###### Rounding
- `const PI = 3.1415926;`
- `PI.toFixed(3)` >> "3.142"

###### Boolean
- all values are either truthy or falsy
- only 9 falsy values, all others are true:
  - ""
  - ''
  - ``
  - 0
  - -0
  - NaN
  - false
  - null
  - undefined

###### Equality
- hard vs soft equality
- soft equality uses coercion to compare values
- hard equality does not, so will only return true if values are the same value AND the same type
- should always use hard equality to avoid issues with JS' type coercion feature

#### Chapter 3

###### Arrays
- push(adds to end), unshift(adds to beginning), splice()
- ordered list of values
- `const myArray = [];`
- `const myArray = new Array();`
- should use literal way to do it
- not primitive - arrays are objects
- can use spread operator `...` to work with arrays or anything that is an iterator
- arrayname.splice(x, y, z); is super powerful.
  - x is which index to start at
  - y is how many entries to remove, can be zero
  - z is what to insert, optional parameter if don't want to insert anything
  - powerful, but dangerous because it permanently changes the array
  
###### Sets
- simpler than arrays because no duplicates
- also more efficient at running .includes() method
- `const list = new Set();`
- no literal way to create Sets
- `list.add(1);`
- easy way to eliminate duplicates from arrays, can Object.assign([], <setname>); to go back to array but this is not a deep clone
- <setname>.has(<itemtocheckfor>); super efficient, much faster than includes or indexOf() methods used in arrays

###### Maps
- more flexible than Objects, can use any datatype as key whereas Object can only use String
- used exclusively for storage and retrieval of values
- can use size property to find size, no such feature for Objects
- `const map = new Map();`
- no literal way to create Maps
- `const heroes = new Map( [ [ 'Clark Kent', 'Superman' ], [ 'Bruce Wayne', 'Batman' ] ] );`

###### If
- can also be written as <condition> ? (<if condition is true>) : (<if condition is false>);
- depends on readability

###### Switch
- always finish each case with a `break`, otherwise it will fall thru. May be intended, but it can be confusing and is a hack.
- can have default case at the bottom for when none of the cases are true

###### Enumerables
- Maps, Sets are enumerable
- weak maps and weak sets are not!
- Sets:
  - can use for of loop. `for (const letter of letters) {console.log(letter)};};
- Maps:
  - can also use for of loop, but over
    - mapname.entries()
    - mapname.values()
    - mapname.keys()

#### Chapter 4 Functions
- small, self contained mini program. reduces repetition, makes code easier to follow
- first-class objects

- can define in three ways:
  - literally, like `function hello() { console.log("Hello World!"); }`
  - anonymously, like `const goodbye = function() { console.log("Hello World!"); };` must end in semi-colon
  - can also use `const hi = new Function(functionbody);`, but this is bad because:
    - global scope no matter where its declared
    - function body must be a string, which makes things difficult
    
###### Return values
- can return nothing, in which case JS engines return `undefined`
- or can return something specific, to be assigned to a variable like `const message = howdy();`
  - return from howdy function assigned to message variable

###### Arguments and Parameters
- arguments are passed in during function invocation, parameters are set when function is defined
- if function takes 3 arguments and only pass in 2, third argument will be set to `undefined`
  - this may result in erroneous behavior
- if function takes 3 arguments and pass in 4, fourth argument will be ignored and function will behave normally
  - extra parameters can be accessed via arguments object, though
- ES6 added default parameters feature
- arguments is an array-like object, can be accessed like an array (arguments[0], arguments.length), but does not have slice(), join(), foreach(), etc.
- can use rest operator:
  - `function rest(...args) {for (arg of args) {console.log(arg); } }`
  - ...args will turn all the passed in arguments into an array stored in args
  - basically, it's an improved version of arguments array-like object that is actually an array
- always put default parameters after non-default, otherwise purpose is defeated!
- anonymous functions!
  - `const square = x => x*x;` \\\\one parameter
  - `const add = (x,y) => x + y;` \\\\two parameters
  - `const hello = () => alert('Hello World!');` \\\\no parameters
- arrow functions are perfect for short, anonymous functions. anything longer, better to use literal or constructor

###### Hoisting
- functions are automatically hoisted, if declared using `function` keyword
- variables are hosted if declared with `var` keyword. assignment is not hoisted, though.
  - best to declare with `const` and `let`, and not rely on hoisting
- function expressions, when assigned to variable, act just like variables
  - var variables hoisted, but function expression is not
  - const,let not hoisted at all
  
###### Callbacks
- `function sing(song,callback) { console.log("I'm singing along to ${song}."); callback(); }`
  - will invoke `callback` function 
  - can ensure callback is indeed function, `typeof(callback) === 'function';`
  - can also pass anonymous function instead of function name
    - `sing('Let It Go',()=>{ console.log("I'm standing on my head."); })`

###### forEach()
- array method, pass in an anonymous function with 3 parameters:
  - value
  - index
  - full array this is being called on, without brackets
  
###### map()
- array method, pass in function to be ran against each element in the array
- exactly like Haskell map
- `[1,2,3].map ( x=> 2*x);`
- can take 3 parameters as well, just like forEach()

###### reduce()
- array method, pass in function that takes two parameters:
  - cumulative value
  - current value in array being inspected
- `[1,2,3,4,5].reduce( (acc,val) => acc + val );`
- second parameter, the one after the callback, is the starting value for the accumulator

###### filter()
- array method, pass in function that takes a single parameter, spits out true or false
- returns array of values that pass the "filter"

#### Chapter 5 Objects
- self contained set of related values and functions
- used to keep them all in the same place, organization
- each property is a key value pair, separated by commas
- if property name doesn't follow naming rules, needs to be quoted.
  - i.e., 'real name' since it contains a space
  - but in the real world, 'real name' would just be realName or real_name
- all objects are mutable, even if declared with a const
- can create using object literal or constructor:
  - `const spiderman = {};`
    - recommended
  - `const spiderman = new Object();`
    - not recommended
- no literal way to create Sets and Maps because this is reserved for Objects!
- very similar to Maps, but Maps are more flexibile since keys for objects can only be strings
- access properties in two ways
  - dot notation - i.e., `superman.name;` preferred way
  - bracket notation - i.e., `superman['name'];` useful only if property names are nonstandard (with a space), or if need to evaluate property name


###### if properties or methods exist
- `'city' in superman;` uses `in` keyword to see if 'city' property is inside superman object
- can also use `hasOwnProperty()` method, will return false if property is inherited or if property does not exist
- `Object.keys(objectname);` returns array of all properties/methods within a given object
- can easily add new properties, i.e., `superman.city = 'Metropolis';`
- properties show up in unspecified order, never rely on properties being in certain order
- `delete superman.fly` will delete the fly property in the superman object

###### namespacing
- prevents naming collisions by using object literal pattern
- the object is the namespace, so place everything grouped into a single object, and that object serves as a namespace to prevent collisions

###### JSON
- JavaScript Object Notation
- invented by Douglas Crockford in 2001
- extremely popular lightweight data-storage format
- hits sweet spot for being both human and machine readable
- property names are double-quoted
- permitted values are:
  - double-quoted strings
  - numbers
  - true
  - false
  - null
  - arrays
  - objects
  - functions are NOT permitted, even though you can have functions in objects
- `parse()` method takes a string of data in JSON format and returns a JS object
- `stringify()` method does the opposite of parse() - takes a JS object and turns it into a JSON
  - ignores functions when stringify-ing
- 

