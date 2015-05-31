|Status Code | Meaning | More Detail|
|:----------:|---------| -----------|
|**100s**    |**Informational**  |
|100 |Continue  |This means that the server has received the request headers, and that the client should proceed to send the request body (in the case of a request for which a body needs to be sent)|
|101  |Switching Protocols|This means the requester has asked the server to switch protocols and the server is acknowledging that it will do so.|
|102 | Processing | As a WebDAV request may contain many sub-requests involving file operations, it may take a long time to complete the request. This code indicates that the server has received and is processing the request, but no response is available yet. |
|**200s**    | **Success**  |
|200 | OK | Standard response for successful HTTP requests. The actual response will depend on the request method used|
|201 | Created | The request has been fulfilled and resulted in a new resource being created.|
|202 | Accepted | The request has been accepted for processing, but the processing has not been completed.|
|203|Non-Authoritative Information (since HTTP/1.1)|The server successfully processed the request, but is returning information that may be from another source.|
|204|No Content|The server successfully processed the request, but is not returning any content. Usually used as a response to a successful delete request.|
|205|Reset Content|The server successfully processed the request, but is not returning any content. Unlike a 204 response, this response requires that the requester reset the document view.|
|206|
|**300s**    | **Redirection**  |
|**400s**    | **Client Error**  |
|**500s**    | **Server Error**  |
