#### Chapter 6 The Document Object Model
- Allows you to access elements of a web page, add/remove elements, change order, content, attributes of elements, and styling

###### What is the DOM?
- represents an HTML document as network of connected nodes that form a tree-like structure
- not actually part of JS because it's language agnostic
- can use JS to access and modify web page using special built-in object called document

###### History of DOM
- Netscape and Microsoft had own distinct ways of alterating parts of web page
- focus was on common page elements, like images links and forms
- known as Dynamic HTML (a.k.a DOM level 0 | legacy DOM)
- World Wide Web Consortium (W3C) standardized this, created DOM level 1 in 1998
- DOM level 2 spec, created in 2000, added `getElementById()`
- DOM level 3 spec, created in 2004 -> W3C abandoned using levels after this
- now, it's a [living standard](https://www.w3.org/TR/dom/)

###### Getting Elements
- `const body = document.body;`
- `typeof body;` >> `object`
- `body.nodeType;` >> `1`
  - 1: element
  - 2: attribute
  - 3: text
  - 8: comment
  - 9: body
- `body.nodeName;` >> `"BODY"`

###### Legacy DOM methods
- document.body >> body element of a web page
- document.images >> node list of all images in document
- document.links >> node list of all <a> elements and <area> elements with href attribute
- document.anchors >> node list of all <a> elements with name attribute (no longer used in HTML, use id attribute instead)
- document.forms >> node list of all forms in document

###### Node Lists
- array-like objects, but not actually arrays
- can access using index notation, like `document.images[0]`
- also has a length property, so can interate thru
- __DOES NOT__ have splice, slice, or join
- can convert to array using `Array.from()` OR spread operator

###### getElementById()
- returns reference to element with unique id attribute, passed in as argument
- `const h1 = document.getElementById('title');`
- most commonly used method of accessing elements on a web page
- will return `null` if ID does not exist

###### getElementsByTagName()
- returns node list of all elements with provided tag name
- `const listItems = document.getElementsByTagName('li');`
- empty node list returned if no elements existed

###### getElementsByClassName()
- returns node list
- `const heroes = document.getElementsByClassName('hero');`

###### Query Selectors
- can be used on any element, not just document
- `document.querySelector()` finds first element in doc that matches a passed in CSS selector
- `document.querySelectorAll()` returns node list of all elements that matches passed in CSS selector
- very powerful methods, bc [CSS selectors](https://www.sitepoint.com/css-selectors/) are powerful
- JQeury is popular JS framework that makes it super easy to find elements using CSS-style syntax, very similar to this

###### Navigating DOM Tree
- Node objects have a bunch of properties and methods for navigating the DOM
- `childNodes` property is a NodeList of all nodes that are children of the node provided
- whitespace is treated as a node, so will often have empty #text nodes between line item nodes
- `children` property is an `HTMLCollection` of any element nodes that are children, so ignores the #text nodes
- `firstchild`
- `lastchild`
  - both first and last child can often be text nodes, so be careful
- parentNode
- nextSibling returns adjacent node of same parent, will return null if node is last child
- previousSibling
  - just like first/last child, may return text nodes, so be careful
- `nodeValue` and `textContent` properties used on a element node to find the actual text

###### Settings Element Attributes
- setAttribute changes value of element's attributes
  - `wonderWoman.setAttribute('class', 'villain');
    - if class attribute doesn't exist, adds it and sets it to villain
- `wonderWoman.getAttribute('class');`
- can alternatively do `wonderWoman.className = `villain`;`
- uses className and HTMLFor instead of class and for, since class and for are JS keywords
- using className will overwrite the class entirely, better to use classList property instead
- classList:
  - add() will add a provided class
  - remove() will remove a provided class
  - toggle() will add if it doesn't exist, remove if it does
  - contains() check if element has a particular class

###### Creating Elements
- createElement() method, takes a tag name and returns the element
- `const flash = document.createElement('li');`
- to create a text node underneath flash (since it's currently empty), `const flashText = document.createTextNode('Flash');`
  - could also just do flash.textContent = 'Flash';
- to link the text node to the element node, `flash.appendChild(flashText);`
- insertBefore() will place a new element before another
  - `heroes.insertBefore(aquaman,wonderWoman);`
  - `heroes.removeChild(aquaman);`
  - can easily add it back in since aquaman is stored in a variable
- `parent.replaceChild(new,old);`
- `heroes.innerHTML();` will return all the HTML within heroes parent as raw text
  - also writeable. but any scripts within will not execute
  - useful for inserting large amounts of HTML

###### Live Collections
- node lists returned by 
  - `document.getElementsByClassName();`
  - `document.getElementsByTagName();`
- are live, will update in real time to reflect changes to the page
- be careful when referencing stuff by index, since these live node lists may not have that element there anymore

  
