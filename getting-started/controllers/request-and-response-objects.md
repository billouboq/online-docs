# Request and Response Objects

Request and Response objects are available to the controller as `request and response` methods.

### The Request Object

It serves both to perform requests by an [`HTTP::Client`](https://crystal-lang.org/api/0.23.0/HTTP/Client.html)and to represent requests received by an[`HTTP::Server`](https://crystal-lang.org/api/0.23.0/HTTP/Server.html). A request always holds an [`IO`](https://crystal-lang.org/api/0.23.0/IO.html) as a body. When creating a request with a [`String`](https://crystal-lang.org/api/0.23.0/String.html) or [`Bytes`](https://crystal-lang.org/api/0.23.0/Bytes.html) its body will be a [`IO::Memory`](https://crystal-lang.org/api/0.23.0/IO/Memory.html) wrapping these, and the `Content-Length`header will be set appropriately.

The request object contains a lot of useful information about the request coming in from the client. To get a full list of the available methods, refer to the Crystal  API Documentation [https://crystal-lang.org/api/0.23.0/HTTP/Request.html](https://crystal-lang.org/api/0.23.0/HTTP/Request.html)

| Property of Request | Purpose | Implemented? |
| :--- | :--- | :--- |
| host | The hostname used for this request. | Yes |
| domain\(n=2\) | The hostname's first`n`segments, starting from the right \(the TLD\). | No |
| format | The content type requested by the client. | No |
| method | The HTTP method used for the request. | Yes |
| get?, post?, patch?, put?, delete?, head? | Returns true if the HTTP method is GET/POST/PATCH/PUT/DELETE/HEAD. | No |
| headers | Returns a hash containing the headers associated with the request. | Yes |
| port | The port number \(integer\) used for the request. | No |
| protocol | Returns a string containing the protocol used plus "://", for example "http://". | No |
| query\_string | The query string part of the URL, i.e., everything after "?". | Yes |
| remote\_ip | The IP address of the client. | No |
| url | The entire URL used for the request. | No |

### The Response Object

The response object is not usually used directly, but is built up during the execution of the action and rendering of the data that is being sent back to the user, but sometimes - like in an after filter - it can be useful to access the response directly. Some of these accessor methods also have setters, allowing you to change their values. To get a full list of the available methods, refer to the [https://crystal-lang.org/api/0.23.0/HTTP/Server/Response.html](https://crystal-lang.org/api/0.23.0/HTTP/Server/Response.html)

| Property of Response | Purpose |
| :--- | :--- |
| body | This is the string of data being sent back to the client. This is most often HTML. |
| status | The HTTP status code for the response, like 200 for a successful request or 404 for file not found. |
| location | The URL the client is being redirected to, if any. |
| content\_type | The content type of the response. |
| charset | The character set being used for the response. Default is "utf-8". |
| headers | Headers used for the response. |



