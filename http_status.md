# HTTP RESPONSE STATUS CODE

### 200 OK

    The request has succeeded. The meaning of a success varies depending on the HTTP method:

    GET: The resource has been fetched and is transmitted in the message body.

    HEAD: The entity headers are in the message body.

    PUT or POST: The resource describing the result of the 
    action is transmitted in the message body.

    TRACE: The message body contains the request message as received by the server


### 201 Created

    The request has succeeded and a new resource has been created as a result of it. This is typically the response sent after a POST request, or after some PUT requests.


### 202 Accepted

    The request has been received but not yet acted upon. It is non-committal, meaning that there is no way in HTTP to later send an asynchronous response indicating the outcome of processing the request. It is intended for cases where another process or server handles the request, or for batch processing.

### 203 Non-Authoritative Information

    This response code means returned meta-information set is not exact set as available from the origin server, but collected from a local or a third party copy. Except this condition, 200 OK response should be preferred instead of this response.


### 204 No Content

    There is no content to send for this request, but the headers may be useful. The user-agent may update its cached headers for this resource with the new ones.


### 205 Reset Content

    This response code is sent after accomplishing request to tell user agent reset document view which sent this request.


### 206 Partial Content

    This response code is used because of range header sent by the client to separate download into multiple streams.


### 207 Multi-Status (WebDAV)

    A Multi-Status response conveys information about multiple resources in situations where multiple status codes might be appropriate.


### 208 Multi-Status (WebDAV)

    Used inside a DAV: propstat response element to avoid enumerating the internal members of multiple bindings to the same collection repeatedly.


### 226 IM Used (HTTP Delta encoding)

    The server has fulfilled a GET request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance.

&thinsp;
---

### 300 Multiple Choices

    This Status Code indicates that the request has more than one possible response. The user agent or user should choose one of them. There is no standardized way to choose one of the responses.

### 301 Moved Permanently

    This Status Code indicates that the URI of the requested    resource has been changed. Typically, a new URI should be given in the response.

### 302 Found

    This Status Code indicates that the URI of the requested resource has been changed temporarily. New changes in the URI might be made in the future. Therefore, this same URI should be used by the client in future requests.

### 303 See Other

    This Status Code indicates that the server sent this response to direct the client to get the requested resource to another URI with a GET request.

### 304 Not Modified

    This Status Code is used for caching purposes. It indicates to the client that the response has not been modified, so the client can continue to use the same cached version of the response.

### 305 Use Proxy

    This Status Code indicates that the requested response must be accessed by a proxy. This response code is not largely supported for security reasons.

### 306 Unused

    This Status Code is no longer used.


### 307 Temporary Redirect

    This Status Code indicates that the requested resource is temporarily located at another URI. The client should request the resource again by using the temporary URI provided in the Location field of the response. The second request must use the same method as the original request. This has the same semantic as the HTTP 302 "Found" Status Code, with the exception that the user agent must not change the HTTP method used. For example, if a POST was used in the first request, a POST must be used in the second request.

### 308 Permanent Redirect

    This Status Code indicates that the requested resource is now permanently located at another URI, specified by the Location: HTTP Response header. This has the same semantics as the HTTP 301 "Moved Permanently" Status Code, with the exception that the user agent must not change the HTTP method used. For example, if a POST was used in the first request, a POST must be used in the second request.

&thinsp;
---

### 400 Bad Request

    This error indicates that the user's request contains incorrect syntax.

### 401 Unauthorized

    This error indicates that the requested file requires authentication (a username and password).

### 403 Forbidden

    This error indicates that the server will not allow the visitor to access the requested file. If a visitor receives this code unexpectedly, you should check the file's permission settings, or check whether the file has been protected.

### 404 Not Found

    This error indicates that the server could not find the file that the visitor requested. This commonly occurs when a URL is mistyped.

&thinsp;
---

### 5xx Errors

    These errors are caused by the server being unable to fulfill an apparently valid request from a visitor. Often, you will need the help of a server administrator to investigate them.

    It is also important to consider that quite often, a chain of servers is handling an HTTP request, so that it may not be your server that is returning the error.

### 500 Internal Server Error

    This error indicates that the server has encountered an unexpected condition. This often occurs when an application request cannot be fulfilled due to the application being configured incorrectly on the server.

### 501 Not Implemented

    This error indicates that the HTTP method sent by the client is not supported by the server. This is most often caused by the server being out of date. It is a very rare error and generally requires that the web server be updated.

### 502 Bad Gateway

    This error is usually due to improperly configured proxy servers. However, the problem may also arise when there is poor IP communication between back—end computers, when the client's server is overloaded, or when a firewall is functioning improperly.

    The first step in resolving the issue is to clear the client's cache. This action should result in a different proxy being used to resolve the web server's content.

### 503 Service Unavailable

    This error occurs when the server is unable to handle requests due to a temporary overload or due to the server being temporarily closed for maintenance. The error indicates that the server will only temporarily be down. It is possible to receive other errors in place of 503.

    Contact the server administrator if this problem persists.

### 504 Gateway Timeout

    This error occurs when a server somewhere along the chain does not receive a timely response from a server further up the chain. The problem is caused entirely by slow communication between upstream computers.

    To resolve this issue, contact the system administrator.

### 505 HTTP Version Not Supported

    This error occurs when the server refuses to support the HTTP protocol that has been specified by the client computer. This can be caused by the protocol not being specified properly by the client computer; for example, if an invalid version number has been specified.

### 506 Variant Also Negotiates

    This error indicates that the server is not properly configured. Contact the system administrator to resolve this issue.


### 507 Insufficient Storage

    This error indicates that the server is out of free memory. This is most likely to occur when an application that is being requested cannot allocate the necessary system resources to run.

    To resolve the issue, the server's hard disk may need to be cleaned of any unnecessary documents to free up more hard disk space, its memory may need to be expanded, or it may simply need to be restarted.

    Contact the system administrator for more information regarding this error message.

### 509 Bandwidth Limit Exceeded

    This error occurs when the bandwidth limit imposed by the system administrator has been reached. The only fix for this issue is to wait until the limit is reset in the following cycle.

    Consult the system administrator for information about acquiring more bandwidth.

### 510 Not Extended

    This error occurs when an extension attached to the HTTP request is not supported by the web server.

    To resolve the issue, you may need to update the server. Consult the system administrator for more information.

