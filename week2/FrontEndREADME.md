#Front End Devs


#### Rafe's notes on HTTP requests

Websites don't send you anything over HTTP without a request first

You need 4 things to make a request:
  1. **URI:** a noun (the address of the thing you're looking for)[POST: object of the sentence]
  2. **Method:** a verb (what you want to do with the thing)
  3. **Headers:** (information about the request (who sent it, etc.))
  4. **Body:** (data you want to send to the server)[GET/DELETE: subject of the sentence]

GET /dumprequest HTTP/1.1 []
-> Get the thing at /dumprequest using this protocol (language I'm talking)

Host: rve.org.uk
-> where the thing is found (get downstairs projector rather than upstairs projector)

Connection: keep-alive
-> capabilities of browser; mostly used by server to define timeouts etc.

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-> what document types I like

User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.152 Safari/537.36
-> what kind of person I am (browser, operating system, version ...)

DNT: 1
-> Stop following me! (Do Not Track)

Referer: https://www.google.co.uk/
-> who sent me here

Accept-Language: en-US,en;q=0.8
-> languages I like


#### Rafe's notes on making requests in vanilla JS (no libraries!)

XMLHttpRequest is a constructor function (think the example from morning challenge this morning). Doesn't take parameters (???).

Has a ton of cool methods which will abet you in making requests.

FOR EXAMPLE: open -- it needs a method and an url*(can I provide a generic URI?) (this is the minimum for a valid http request).

It initializes an HTTP request.
