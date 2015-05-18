#Front End Devs

# What is an HTTP Request?

HTTP works as a request-response protocol between a client and server
A client submits a request and the server returns the response

##GET request

```js
GET /files/fruit.txt HTTP/1.1
// GET (i.e. fetch) the file 'fruit.txt' from the server at 'eloquentjavascript.new' using version 1.1 of the  //HTTP protocol from the browser mentioned by 'User-Agent'
Host: eloquentjavascript.net
User-Agent: a browser
```

Response
The server responds with the status of the request, some information about it and the file itself:

```js
HTTP/1.1 200 OK
Last-Modified: Mon, 23 Jul 2007 08:41:56 GMT
Content-Length: 24
Content-Type: text/plain

'contents of fruit.txt displayed here'
```

##POST request

this indicates some information will be sent along with the request


In js programs to communicate with the server without reloading the page the js function needs to make the HTTP request itself using the XMLHttpRequest() 