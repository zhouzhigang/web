# HTTP

## Introduction

HTTP(Hyper Transfer Protocol)

The HTTP protocol is a request/response protocol.

A client sends a request to the server in the form of a request method, URI, and protocol version, followed by a MIME-like message containing request modifiers, client information, and possible body content over a connection with a server.
The server responds with a status line, including the message's protocol version and a success or error code, followed by a MIME-like message containing server informatin, entity metainformation, and possible entity-body content.

HTTP communication usually takes place over TCP/IP connections. The default port is TCP `80`, but other ports can be used.


HTTP/1.1 defines the sequence CR LF as the end-of-line marker for all protocol elements except the entity-body



## Protocol Parameters

### HTTP Version

`<major>.<minor>` format

    HTTP-Version   = "HTTP" "/" 1*DIGIT "." 1*DIGIT

### Uniform Resource Identifiers

URIs have been known by many names: `WWW addresses`, `Universal Document Identifiers`, `Universal Resource Identifiers`, and finally the combination of `Uniform Resource Locator`(URL) and `Uniform Resource Name`(URN).

URL(uniform Resource Locator)

    schema://host[:port#]/path/../[;url-params][?query-string][#anchor]

    http_URL = "http:" "//" host [ ":" port ] [ abs_path [ "?" query ]]

When comparing two URIs to decide if they match or not, a client SHOULD use a __case-sensitive__ octet-by-octet comparison of the entire URIs, with these exceptions:


## Request

    Request       = Request-Line
                    *(( general-header
                     | request-header
                     | entity-header ) CRLF)
                    CRLF
                    [ message-body ]

### Request-Line

    Request-Line   = Method SP Request-URI SP HTTP-Version CRLF

    Method         = "OPTIONS"
                    | "GET"
                    | "HEAD"
                    | "POST"
                    | "PUT"
                    | "DELETE"
                    | "TRACE"
                    | "CONNECT"

    Request-URI    = "*" | absoluteURI | abs_path | authority

e.g.

    OPTIONS * HTTP/1.1
    GET http://www.w3.org/pub/WWW/TheProject.html HTTP/1.1


### Request Header Fields

    request-header = Accept
                    | Accept-Charset
                    | Accept-Encoding
                    | Accept-Language
                    | Authorization
                    | Expect
                    | From
                    | Host
                    | If-Match
                    | If-Modified-Since
                    | If-None-Match
                    | If-Range
                    | If-Unmodified-Since
                    | Max-Forwards
                    | Proxy-Authorization
                    | Range
                    | Referer
                    | TE
                    | User-Agent

* Cache
    + `If-Modified-Since`
    + `If-Non-Match`
    + `Pragma`: `no-cache`
    + `Cache-Control`: `Public` | `Private` | `no-cache`
* Client
    + `Accept`: `*` | `text/html`
    + `Accept-Encoding`: `gzip` | `deflate`
    + `Accept-Language`: `en-us` | `gb2312` | `gbk`
    + `Accept-Charset`: `utf-8` | `gb2312`
    + `User-Agent`: `
* Cookies/Login
    + `Cookies`
* Miscellaneous
    + `Referer`
* Transport
    + `Connection`: `Keep-Alive`
    + `Host`


## Response

    Rresponse       = Status-Line
                    *(( general-header
                     | response-header
                     | entity-header ) CRLF)
                    CRLF
                    [ message-body ]

### Status-Line

    Status-Line = HTTP-Version SP Status-Code SP Reason-Phrase CRLF

#### Status Code

* 1xx: Informational - Request received, continuing process
* 2xx: Success - The action was successfully received, understood, and accepted
* 3xx: Redirection - Further action must be taken in order to complete the request
* 4xx: Client Error - The request contains bad syntax or cannot be fulfilled
* 5xx: Server Error - The server failed to fulfill an apparently valid request

### Response Header Fields

    response-header = Accept-Ranges
                    | Age
                    | ETag
                    | Location
                    | Proxy-Authenticate
                    | Retry-After
                    | Server
                    | Vary
                    | WWW-Authenticate


* Cache
    + `Cache-Control`
    + `Date`
    + `Expires`
    + `Vary`: `Accept-Encoding`
* Cookies
    + `P3P`
    + `Set-Cookies`
* Miscellaneous
    + `Server`

## Entity

Entity: The information transferred as the payload of a request or response

### Entity Header Fields

* Entity
    + `Allow`
    + `Content-Encoding`
    + `Content-Length`
    + `Content-Location`
    + `Content-MD5`
    + `Content-Range`
    + `Content-Type`
    + `Expires`
    + `Last-Modified`
    + extension-header


## Connections

Persistent Connections

A significant difference between HTTP/1.1 and earlier versions of HTTP is that persistent connections are the default behavior of any HTTP connection.
That is, unless otherwise indicated, the client SHOULD assume that the server will maintain a persistent connection, even after error responses from the server.


## Method Definitions

### Safe and Idempotent Methods

* Safe Methods
* Idempotent Methods

### Methods

* `OPTIONS`
* `GET`
* `POST`
* `PUT`
* `DELETE`
* `TRACE`
* `CONNECT`

## Status Code Definitions

* Informational 1xx
    + 100 Continue
    + 101 Switching Protocols
* Successful 2xx
    + 200 OK
    + 201 Created
    + 202 Accepted
    + 203 Not-Authoriative Information
    + 204 No Content
    + 205 Reset Content
    + 206 Partial Content
* Redirection 3XX
    + 300 Mulitple Choices
    + 301 Moved Permanently
    + 302 Found
    + 303 See Other
    + 304 Not Modified
    + 305 Use Proxy
    + 306 (Unused)
    + 307 Temporary Redirect
* Client Error 4xx
    + 400 Bad Request
    + 401 Unauthorized
    + 402 Payment Required
    + 403 Fobidden
    + 404 Not Found
    + 405 Method Not Allowed
    + 405 Not Acceptable
    + 407 Proxy Authentication Required
    + 408 Request Timeout
    + 409 Conflict
    + 410 Gone
    + 411 Length Required
    + 412 Precondition Failed
    + 413 Request Entity Too Large
    + 414 Request-URI Too Large
    + 415 Unsupported Media Type
    + 416 Requested Range Not Satisfiable
    + 417 Expectation Failed
* Server Erro 5xx
    + 500 Internal Server Error
    + 501 Not Implemented
    + 502 Bad Gateway
    + 503 Service Unavailable
    + 505 HTTP Version Not Support

## Access Authentication

## Content Negotiation

## Caching in HTTP

## Security Considerations


## Reference
* [Hypertext Transfer Protocol - Wikipedia](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
* [RFC2616 - Hypertext Transfer Protocol -- HTTP/1.1](https://www.ietf.org/rfc/rfc2616.txt)
* [HTTP in detail](http://blog.csdn.net/gueter/article/details/1524447)
* [HTTP in detail](http://kb.cnblogs.com/page/130970/)
