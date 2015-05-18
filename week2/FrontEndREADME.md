#Front End Devs

Abdi 

What is an HTTP request? 

HTTP stands for Hyper Text Transfer protocol, and this is basically an agreed upon method that defines how computers communicate with each other. Whenever you use a browser(or an application) to view a website you are using the HTTP protocol. 

HTTP cycle 

Whenever you visit a web page on the web your browser makes a request to a webserver to load that websites onto your browswer. so for example, when you visit: http://wikipedia.org your browser uses the HTTP protocol to request the pages for Wikipedia and the web server (another computer on the Internet) will send back the pages to your browser. The data that the web server sends back is typically HTML mark up code, CSS, and JavaScript. Your broswer then renders the web page along with the CSS styling and any JS logic that the pages need. This is all done very quickly, but there are several streps involved when you request a page from a webserver. 

Step 1: Type in the URL of the web page you wish to view

Step 2: Your request is sent using the HTTP protocol across the Internet 

Step 3: The web server(in our example wikipedia's web server) receives the request and looks to see if the page requested is there. 

Step 4: The web server sends back the web page requested as data via the Internet, again using the HTTP protocol. 

Step 5: The browser receives the data sent by the web server and renders this to make it viewable to the reader. So, this involves rendering the mark up, CSS and any JS logic. 

Summary 

So essentially, HTTP is a method that both client (browser) and server use to communicate with each other and make sure everything is consistent in their communication. 

How to make an HTTP request in vanilla JS

There are four steps involved in making an HTTP request in JS: 

1. Create an XMLHTTP request object 

2. Define a call back function -

This is the programming that is run when the server responds with the data along with the logic that to update the DOM. 

3. Open a request 

This step gives the browser two pieces of information  the method the browser will use to send the request, usually either get or post, and the URL where the request is sent (the web server). 

4. Send the request 

The last step is to actually send the request. The previous three steps gave the web browser all the information it needs so we can finally send off the request to the web server.
