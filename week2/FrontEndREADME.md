# Front End Devs


### The Anatomy of an HTTP request

Websites don't send you anything over HTTP without a request first

You need 4 things to make a request:
  1. **URI:** a noun (a reference to the thing you want)
  2. **Method:** a verb (what you want to do with the thing)
  3. **Headers:** (information about the request (who sent it, etc.))
  4. **Body:** another noun (data you want to send to the server)


**GET /bookIWant HTTP/1.1 []**  
Get the thing at /bookIWant using this protocol (language I'm talking)

>A woman stands in her living room, and says "I want *Harry Potter & The Goblet of Fire*". Unfortunately, as she is at home, and not in the bookshop, she doesn't get anything.

**Host: bookshop.com**  
Where the thing is found (get downstairs projector rather than upstairs projector)

>The woman is now in the bookshop, and says "I want *Harry Potter & The Goblet of Fire"*. The man behind the counter hands her a film poster.


**Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8**  
What document types I like

>"This isn't what I want!" cries the woman. "I want the book. And failing that, the film."  
"OK, cool. Wanna quickie in the back?" Replies the man.

**User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.152 Safari/537.36**  
What kind of person I am (browser, operating system, version ...)

>"I am *not* that kind of person!" replies the woman.

**DNT: 1**  
Stop following me! (Do Not Track)

>"No problem," says the man as he passes her the book "Let me just note that down in the ledger of extensive customer records we keep."  
"Uhhh, please don't do that ..." asks the woman.  
"Hahaha," chortles the man and ignores her.

**Referer: https://www.google.co.uk/**  
Who sent me here

>"How did you find out about us by the way?" asks the man.
>"My brother told me."

**Accept-Language: en-US,en;q=0.8**  
Languages I like

>She looks down at the book, and sees *Harry Potter et la Coupe de feu*.  
>"Oh, I'm sorry do you have it in English?"
>
>***TO BE CONTINUED ...***
