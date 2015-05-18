#Example of a HTTP Request in JS

This document explains each section of the code in 'index.html'. It will take you through how tocreate a new HTTP object, retrieve text from a file (name.txt) and display the result on the page.

For an introduction to HTTP Requests read [url] first!

First set up the HTML file. Within the body create a paragraph with an id of 'response'. This will display the contents of the file we will call later on.  

``` html
<p id="response">Contents of the file</p>
``` 

The HTTP request will be made within `<script></script>` tags. A HTTP request is started by creating a new HTTP Object using `XMLHttpRequest()`. 

``` js
var request = new XMLHttpRequest(); // creates a new HTTP object called 'request'

```
The XMLHttpRequest object is used to exchange data with a server behind the scenes to update a webpage without reloading it. 

The `open()` method is used to configure a HTTP request. The `.open(method, url, async)` method takes three parameters. 'Method' refers to the type of request e.g. 'GET' or 'POST'. The 'url' refers to the location of the file on the server that you want to exchange data with. The 'async' is set to either 'true' or 'false'. Setting 'async' to false means that JavaScript will not continue to execute the rest of the scripts until the server response is ready. If the server is slow the application might stop. More on this later! 

After the HTTP request has been configured, the `.send()` method is used to actually send the request to the server. 

``` js
request.open("GET", 'name.txt',false); // submits a GET request to the file 'name.txt'
```

The request is then sent. 
request.send(null);

The HTTP object has several properties. Some examples: 

``` js
.responseText() // response data as a string (i.e. data stored in the file you have opened)
.statusText() // 
```

These properties can be logged to the console. 

```js
console.log(request.responseText);
console.log(request.statusText);
```

So far we have been *synchronously* calling the `.open` method on the HTTP request object (by setting the 'async' parameter to 'false'. This means that while the method is executing, no other functions on the page can work.  
Setting the 'async' parameter to 'true' means that JavaScript doesn't have to wait for the server response and can execute other scripts on the page. The `open` method effectively runs in the background. 

``` js
request.open("GET", 'name.html',true); // asynchronously calling the 'open' method
request.send();
```

However this also means you have to wait until you know the response is ready before accessing the 'responseText' property of the HTTP Object. To do this, we need modify a property of the HTTP Object called 'onreadystatechange'. This property needs to be set to a function that executes every time the state of the request changes.  

Inside the function we check another property called 'readyState'. This can take the values 0,1,2,3 or 4. A value of 4 indicates that the request has finished and the response is ready. When the response is ready, the response text can be displayed on the page. 

```js
request.onreadystatechange = function() {
	if(request.readyState == 4) {
		console.log(request);
		document.getElementById('response').innerHTML = request.responseText; 
		// this last line grabs the element on the page with the id #response and changes its text to the text from the file that was opened. 
	};
};
```

To run this code on your computer, go to the terminal and `cd` into the folder where you have saved this file and the 'name.txt' file. Run the harp static server by typing `harp server` into the terminal. In your browser go to `http://localhost:9000/`.
The text in the 'name.txt' file should appear on the page. In the Javascript console you should be able to see the full XMLHttpRequest object and all the values of all its properties. 


##References
[http://eloquentjavascript.net/1st_edition/chapter14.html]: http://eloquentjavascript.net/1st_edition/chapter14.html
[http://www.w3schools.com/dom/dom_httprequest.asp]: http://www.w3schools.com/dom/dom_httprequest.asp

