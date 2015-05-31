#Example of a HTTP Request in JS

This document will take you through how to create a new HTTP object, retrieve text from a file (name.txt) and display the result on the page without having to reload the page.

For an introduction to HTTP Requests read the [README](https://github.com/nikhilaravi/fac5/blob/nikkinotes/week2/FrontEndREADME.md) first!

### 1. First create a file named "name.txt"
Fill it with Lorem Ipsum and save it in a folder.

### 2. Set up the HTML file.
Within the body, create a paragraph with an id of 'response'. This will display the contents of the file we will get data from in our HTTP Request. Save it in the same folder as the name.txt file

``` html
<p id="response">Contents of the file</p>
```

### 3. Create a new HTTP object
Create a `<script></script>` tag at the bottom of the html file, just inside the `</body>` tag. The HTTP request will be made within `<script></script>` tags. A HTTP request is started by creating a new HTTP Object using `XMLHttpRequest()`.

``` js
var request = new XMLHttpRequest(); // creates a new HTTP object called 'request'

```
The XMLHttpRequest object is used to exchange data with a server behind the scenes to update a webpage without reloading it.

### 4. Add the open method to the object you just created.

``` js
request.open("GET", 'name.txt',false); // submits a GET request to the file 'name.txt'
```

The `open()` method is used to configure a HTTP request. The `.open(method, url, async)` method takes three parameters. 'Method' refers to the type of request e.g. 'GET' or 'POST'. The 'url' refers to the location of the file on the server that you want to exchange data with. The 'async' is set to either 'true' or 'false'. Setting 'async' to false means that JavaScript will not continue to execute the rest of the scripts until the server response is ready. If the server is slow the application might stop. More on this later!

### 5. Then send the request.

```js
request.send(null);
```

After the HTTP request has been configured, the `.send()` method is used to actually send the request to the server.

### 6. Console log the responseText
Now log the contents of the 'name.txt' file into the console by adding the following below the send method:

```js
console.log(request.responseText);
```

HTTP objects have several properties. One of these properties is .responseText() and turns the data stored in the file you are requesting into a string.

### 7. Open the html file in your browser
Now open your html file in firefox (it won't work in chrome) and open up the console. The contents of the name.txt file should now be printed to the console as a string.

You have just successfully loaded the contents of one file into another file without refreshing the page. And you did it with the HTML Request.

### 8. Refresh the file
If you want the content to actually show up in the html page, as opposed to the replace the console log with:

`document.getElementById('response').innerHTML = request.responseText;`

# Doing the whole thing Asynchronously

So far we have been *synchronously* calling the `.open` method on the HTTP request object (by setting the 'async' parameter to 'false'). This means that while the method is executing, no other functions on the page can work.

Setting the 'async' parameter to 'true' means that JavaScript doesn't have to wait for the server response and can execute other scripts on the page. The `open` method then effectively runs in the background.

### 9. Set the 'async' parameter to 'true'.

``` js
request.open("GET", 'name.txt',true);
// asynchronously calling the 'open' method
request.send();
```

However this also means you have to wait until you know the response is ready before accessing the 'responseText' property of the HTTP Object.

To do this, we need to modify a property of the HTTP Object called 'onreadystatechange'. This property needs to be set to a function that executes every time the state of the request changes.  

Inside the function we check another property called 'readyState'. This can take the values 0,1,2,3 or 4. A value of 4 indicates that the request has finished and the response is ready. When the response is ready, the response text can be displayed on the page.

## 10. Modify the onreadystatechange property
Replace the `document.getElementById('response').innerHTML = request.responseText;` with:

```js
request.onreadystatechange = function() {
	if(request.readyState == 4) {
		console.log(request);
		document.getElementById('response').innerHTML = request.responseText;
		// this last line grabs the element on the page with the id #response and changes its text to the text from the file that was opened.
	};
};
```

Open your html file up in firefox again (it still won't work in chrome). The contents of the name.txt file should now be printed inside the `<p>` tag.


##References
1. [http://eloquentjavascript.net/1st_edition/chapter14.html](http://eloquentjavascript.net/1st_edition/chapter14.html)
2. [http://www.w3schools.com/dom/dom_httprequest.asp](http://www.w3schools.com/dom/dom_httprequest.asp)
