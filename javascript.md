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

