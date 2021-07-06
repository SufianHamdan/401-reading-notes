# Read: 09 - WRRC and Java


**HTTP Request Lifecycle**
* Step 1: Local Processing
  - Browser extracts the "scheme"/protocol, host, optional port number, resource path, and query strings that are specified in the form
  - Browser will then look through its own cache of recently requested URLs, the operating system’s cache of recent queries, router’s cache, and DNS cache
* Step 2: Resolve an IP
  - If the cache lookup fails, browser fires off a DNS request using UDP3
  - The request will now have to travel many network devices to reach its target DNS server
  - Request arrives at configured DNS server, the server looks for the address associated with the requested hostname and send a response
  - If a response doesn't come back, the request will be passed to another server
  - The requesting client now has a target IP, and have received a piece of information as part of the answer that will let it know how long the returned answer can be cached for
* Step 3: Establish a TCP Connection
  - The client must open a TCP connection.
  - TCP - ensures delivery and ordered data transmission using a sequence number, which allows the receiver to re-order received packets back into their original order, and allows the sender to retransmit any packet that does not get acknowledged 
  - CP connections are opened using the three-way handshake. Server must already be "listening" on a port, performing a passive open, after which the client can initiate an active open, and the handshake works.
  - The connection between client and server will then be acknowledged.
* Step 4: Send an HTTP Request
  - Request - made up of a "request line", request header, and a body 
    * request line - a line that indicates the HTTP method, the resource being requested, and the protocol version
    *  header - made up of pairs in the form name:value <CR><LF>.
    * body - content of an HTTP request is completely optional, but often contains something like form data or JSON
  - HTTP request is sent and goes through a routing procedure
  - Server receives the request, processes it, and finds the resource being requested, and then it generates an HTTP response.
  - Response is generated, and the server responds to the request.
* Step 5: Tearing Down and Cleaning Up
  - Response delivered, the client sends a FIN packet at the TCP level, to which the server responds with an ACK, and then sends a FIN of its own, which the client responds to with its own ACK signal. Then a timeout will occur. This is the four way handshake.
  - Browser begins processing what it has received, and is done.

  
**Way of performing HTTP requests in Java**
* HttpUrlConnection class - allows the performance of basic HTTP requests without the use of any additional libraries, and classes that we need are part of the java.net package. Used for all types of requests by setting the requestMethod attribute to one of the values: GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE.
* Creating a Request
 - create an HttpUrlConnection instance using the openConnection() method of the URL class:
* Add Request Parameters
  - To add parameters to a request set the doOutput property to true, then write a String of the form param1=value¶m2=value to the OutputStream of the HttpUrlConnection instance.
* Setting Request Headers
  - Use the setRequestProperty() method to add headers to a request.
  - Use the getHeaderField() method to read the value of a header from a connection.
* Configuring Timeouts
  - HttpUrlConnection class allows setting the connect and read timeouts, which will define the interval of time to wait for the connection to the server to be established or data to be available for reading. Can use etConnectTimeout() and setReadTimeout() methods to set the timeout values.
* Handling Cookies
  - java.net package contains classes for cookies such as CookieManager and HttpCookie
  - read the cookies from a response, then add the cookies to the cookie store, and finally add the cookies to the request 
* Handling Redirects
  - Enable or disable automatically following redirects for a specific connection by using the setInstanceFollowRedirects() method with true or false parameter.
  - Possible to enable or disable automatic redirect for all connections.
* Reading the Response
  - Parse the InputStream of the HttpUrlConnection instance, and to execute it use the getResponseCode(), connect(), getInputStream() or getOutputStream() methods
  - Close the connection by using the disconnect() method.
* Reading the Response on Failed Requests
  - Consume the failed stream by using HttpUrlConnection.getErrorStream().
* Building the Full Response
  - Add the response status information.
  - Get the headers using getHeaderFields().
  - Read the response content and append it
 