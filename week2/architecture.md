#Architecture: Structuring Your Code

Information on file structure and best practices, covering CSS, Javascript and the DOM.

##CSS Best Practices
---

###1. Be consistent

CSS "best practices" are a matter of opinion, and everyone tends to establish their own guidelines. It is most important to be consistent: within your own code, and across a group, project or organisation. Consistent styling makes code more readable for yourself and others.

###2. Use an external stylesheet

Rather than mixing your HTML and CSS in one document, use an external stylesheet to separate content from presentation. A single stylesheet can be applied to every page of a site, allowing quick style changes to a single file.

External stylesheets can be cached, allowing faster page loading times

###3. Use multiple stylesheets

Depending on the complexity of the design and the size of the site, it’s often easier to make smaller, multiple stylesheets instead of one giant stylesheet. Using multiple stylesheets makes it easier for the designer to manage the project.

Using multiple stylesheets will also speed up your site, since it will only load required CSS for a single page rather than all CSS styles for your site.

###4. Create a master stylesheet

For a large, complex project, it might be useful to create a "master stylesheet" to standardise styling across pages. This stylesheet can contain common elements to every page (eg. font, heading styles). Since you don't have to repeat the CSS in other files, it makes the code leaner and faster to load.

###5. Create your HTML document first

Starting with a complete HTML document makes it easier to then structure your CSS styling. You'll be able to organise the styling properties according to the order of HTML elements.

###6. Organise documents with a top-down structure

It's important to lay out your stylesheet in a way that allows you to quickly find parts of your code. Many people recommend a "top-down" format. This structure tackles styles as they appear in the source code.

An example stylesheet might be ordered like this:
* Generic classes (body, a, p, h1, etc.)
* header
* nav-menu
* main-content

###7. Name your classes and IDs sensibly

Some tips for naming classes and IDs:
Name classes and IDs in ways that clearly describe its function -- using shorthand will make your code confusing to others, and possibly yourself
Use hyphens not underscores in div names (eg. "hero-image" not "hero_image")
Avoid using IDs like "column-right" or "column-left", that become redundant if you want to move the elements around -- instead use "column-alpha", "column-beta"

###8. Be as specific as possible with selectors

Use the most specific selector wherever possible, especially classes and IDs if available. This makes your code more readable and speeds up loading times.

"Descendent selectors" can slow down your code significantly. They look like this:

```
div p {
  ⋮ declarations
}
```

Since CSS selectors are read right to left, using code like this is an expensive process. In this instance, the browser will first search the entire document for all instances of "p" before finding "div p".

Don't do this! Instead, use a specific class or ID, or use a "child selector". Child selectors look like this:

```
div > p {
  ⋮ declarations
}
```

The '>' indicates that the browser should first search for "div" before centring in on "div p" (a more efficient way of sorting through the code).

###9. Combine CSS properties for multiple elements

If you find yourself adding the same style properties to multiple selectors, combine them into one section, or create a class.

###10. Use shorthand CSS properties

Instead of:
```
h1 {
  margin-top : 5px;
  margin-left : 10px;
  margin-bottom : 15px;
  margin-right : 20px;
}
```
use:
```
h1 {
   margin : 5px, 10px, 15px, 20px; // top, right, bottom and left values
 }
 ```
Comprehensive guide to CSS shorthand here:
http://www.dustindiaz.com/css-shorthand/


###11. Alphabetise your properties

Organising your properties in alphabetical order within selectors makes them easier to read and find.

For example:
```
.some-class{
  color: #fff;
  float: left;
  height: 200px;
  margin: 0;
  padding: 0;
  width: 150px;
}
```

###12. Add comments to your CSS

Add comments to your CSS to explain or signpost parts of your code to make it more readable.

###13. Keep a Class and Colour Reference

Keeping a library of your CSS classes is useful for debugging. A colour reference list is also useful to remember HEX codes and keep styling consistent.

###14. Run code through a CSS validator

Running your site through a validator will evaluate your CSS for compliance with W3C open standards
http://jigsaw.w3.org/css-validator/

###15. Run code through google page speed

Running your site through this google tool will identify elements of a page that are slowing it down: https://developers.google.com/speed/pagespeed/


##Javascript Best Practices
---

###1. Keep JS and HTML separate

* Use the `<script src='myFile.js'>` to link an external file

###2. Place script link at bottom

* Put the link just before you closing `<body>` tag
* This gives the page a chance to load before the script is loaded, avoiding problems

##The DOM

##What is DOM?

The Document Object Model (DOM) is a programming interface for HTML and XML document.
In other words any Web page is a document, which can be displayed in the browser window or as a HTML,source code. The Document Object Model provides another way to represent, store and manipulate that same document.

DOM looks like a giant tree, the elements in DOM are arranged in a hierarchy that defines what you eventually see in the browser.

![DOM elements](http://i.imgur.com/VA7Shfj.png)

This hierarchy is used to help organize your HTML elements. It is also used to help your CSS style rules make sense of what styles to apply on which elements.
From the JavaScript angle, this hierarchy helps to manipulate the DOM.

![DevTool with DOM rendered](http://i.imgur.com/EX1EQ8p.jpg)


##Finding your way around

Before you can find elements and do awesome things with them, you need to first get to where the elements are. The easiest way to tackle this topic is to just start form the top and slide all the way down.

At the top of the DOM tree are window and document objects which are global properties.
The window object represents something like the browser, and the document object is the root of the document.
DOM have at least one combination of parents, siblings, and children to rely on. To visualize this, take a look at the row containing the div and script elements in the following diagram:

![picture of DOM elements](http://i.imgur.com/yLovB8Z.png)

Both the div and script elements are siblings. The reason they are siblings is because they share the body element as their parent. The script element has no children, but the div element does. The img, h1, p, and div are children of the div element, and all children of the same parent are siblings as well.

The following is a brief list of common APIs in web and XML page scripting using the DOM.
* document.getElementById(id)
* element.getElementsByTagName(name)
* document.createElement(name)
* parentNode.appendChild(node)
* element.innerHTML
* element.style.left
* element.setAttribute
* element.getAttribute
* element.addEventListener
* window.content
* window.onload
* window.scrollTo

##What are some best practises around manipulation and adding elements dynamically?

###All scripts, that are not necessary for rendering the DOM for the first time, should only be loaded once they are actually being used.

This is to reduce the site loading time. Javascript by default blocks the parser.If the site initialisation takes a lot of effort, consider splitting up the init in different phases.
Manipulating and adding elements should be done asychronously, which means not inside document.ready() or document.onLoad() .

jQuery selectors can be stored in variables, in order to prevent jQuery from having to go through the DOM every time you use a certain element:

		jQuery('#justadiv').text('Hoi');
		jQuery('#justadiv').css('display', 'block');

		-> var justadiv = jQuery('#justadiv');
		justadiv.text('Hoi');

		etc....

###Graceful degradation

Ensure that your web pages still works without JavaScript.

###Unobtrusive JavaScript

Separate structure from behavior.

###Backwards compatibility

Ensure that older browsers don't choke on your scripts.

###Avoid mixing with other technologies

When you want to hide all elements with a certain class, use javascript to append a ".hide" class, rather than changing the actual css of the element.

###Optimize loops

One of the most common mistake is to read the length attribute of an array at every iteration. This means that every time the loop runs, JavaScript needs to read the length of the array. You can avoid that by storing the length value in a different variable. Another thing to ensure is that you keep computation-heavy code outside loops. This includes regular expressions and — more importantly — DOM manipulation. You can create the DOM nodes in the loop but avoid inserting them into the document.

###Keep DOM access to a minimum

Accessing the DOM in browsers is an expensive thing to do. The DOM is a very complex API and rendering in browsers can take up a lot of time. You can see this when running complex web applications when your computer is already maxed out with other work — changes take longer or get shown half way through and so on.

To make sure that your code is fast and doesn’t slow down the browser to a halt try to keep DOM access to a bare minimum. Instead of constantly creating and applying elements, have a tool function that turns a string into DOM elements and call this function at the end of your generation process to disturb the browser rendering once rather than continually.

###Don’t trust any data

This is not only about evil people wanting to hack your systems; it starts with plain usability. Users will enter incorrect data, all the time. Not because they are stupid, but because they are busy, distracted or the wording on your instructions is confusing them. For example, I just booked a hotel room for a month rather than six days as I entered a wrong number … I consider myself fairly smart.

In short, make sure that all the data that goes into your systems is clean and exactly what you need. This is most important on the backend when writing out parameters retrieved from the URL. In JavaScript, it is very important to test the type of parameters sent to your functions (using the typeof keyword).

### Add functionality with JavaScript, don’t create too much content

Try and avoid adding content with innerHTML(). Using an HTML template and loading this template via Ajax makes much more sense.

### Build on the shoulders of giants

It’s a good idea to learn JavaScript without libraries first, so you really know what’s going on, but you should make use of a JS library when you start developing web sites. You’ll have less issues to deal with and at least the bugs that appear will be ones that can be reproduced — not random browser issues.

### Utilize Proper Events and Callback Functions

You'll have access to the state of the request i.e. whether the request was successful; met with an error and finally whether it has been completed. Make proper use of these events and their respective callbacks to manipulate the UI for a better user experience. For example, if the request was unsuccessful, you'd want to update the user interface to reflect that their changes weren't successful while if it was successful, you'd want to tell them so. Don't keep the user waiting!

### Choose the Right Format for the Job

JSON? XML? HTML? Raw strings?

### Change the DOM Intelligently

So, for a chunk of HTML like so:
```HTML
<div id="container">
<span id="elem1"></span>
<span id="elem2"></span>
</div>
```
instead of doing this:
```javascript
$("#elem1").html("Value 1");
$("#elem2").html("Value 2");
```
Do this:
```javascript
var updatedText = "<span id=\"elem1\">Value1</span>
<span id=\"elem2\">Value2</span>";
$("#container").html(updatedText);
```

### General Coding guidelines:

* Use shortcut notation when it makes sense
* Avoid global Variables, in order to prevent overwriting variables
* Modularize — one function per task
* Avoid heavy nesting
* Comment as much as needed but not more


##### Sources:

* http://www.w3.org/wiki/JavaScript_best_practices
* http://domscripting.com/book/sample/
* http://code.tutsplus.com/tutorials/24-best-practices-for-ajax-implementations--net-9180
