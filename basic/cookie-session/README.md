# Cookies and Session

## Overview

HTTP is stateless, session and cookies are used to trace user information/status.

Sessions are server-side files that contain user information, while cookies are client files that contain user information.

Compare with session, cookes is to large that will waste many network bandwith.
But session is not easy to shared between different servers.


### What is a "Cookie"?

__HTTP cookie__(also called __web cookie__, __Internet cookie__, or simply __cookie__), is a small piece of data sent from a website and stored in the user's web browser while user is browsing it.

Every time the user loads the websites, the browser sends the cookies back to the server to notify the user's previous activity.

### What is a "Session"?

An HTTP session is a sequence of network request-response transactions.

A session id/token is a unique identifier(insead of storing large and cnstantly changing information via cookies) that is generated and sent from a server to a client to identify the current interaction session.
The client usually stores and sends the token as an HTTP cookie and/or sends it as a parameter in GET or POST queries.

The reason to use session tokens is that the client only has to handle the identifier—all session data is stored on the server (usually in a database, to which the client does not have direct access) linked to that identifier. 

Examples of the names that some programming languages use when naming their HTTP cookie include JSESSIONID (JSP), PHPSESSID (PHP), CGISESSID (CGI), and ASPSESSIONID (ASP).

## Cookies

### Cookie Attribute

* Version 0: `Set-Cookie`
* Version 1: `Set-Cookie2`

The syntax for the Set-Cookie response header is

    set-cookie      =       "Set-Cookie:" cookies
    cookies         =       1#cookie
    cookie          =       NAME "=" VALUE *(";" cookie-av)
    NAME            =       attr
    VALUE           =       value
    cookie-av       =       "Comment" "=" value
                    |       "Domain" "=" value
                    |       "Max-Age" "=" value
                    |       "Path" "=" value
                    |       "Secure"
                    |       "Version" "=" 1*DIGIT

### How Cookie Works

How is cookie added to HTTP header in servlet?

    HttpServletResponse     ResponseFacade      Response                    MimeHeaders
            | -1.addCookie----> |
            |                   | -2.addCookie----> |
            |                   |                   | <=3.addCokieInternal
            |                   |                   | <=4.generateCookieString
            |                   |                   | <=5.addHeader
            |                   |                   | -6.header.addValue(name)-> |
            |                   |                   | <------------------------- |
            |                   | <---------------- |
            | <---------------- |

### Cookies limit on different browsers

|Browser Version|Cookies number|Cookies Size|
|---------------|--------------|------------|
|IE6|20/domain|4095|
|IE7/8/9|50/domain|4095|
|Chrome|50/domain|>8000|
|Firefox|50/domain|4097|

## Session

### Session and Cookie

### How session works in servlet?

    Connector   Request         Manager     StandardSession     StandardSessionFacade   Cokkie
        | -1.new-> |
        |          |-2.addCookie->|
        |          |              |

## Reference
* [HTTP cookie - Wikipedia](https://en.wikipedia.org/wiki/HTTP_cookie)
* [Session - Wikipedia](https://en.wikipedia.org/wiki/Session_(computer_science))
* [RFC2109 - HTTP State Management Mechanism](https://www.ietf.org/rfc/rfc2109.txt)
* [Comments on Cookie and Session Mechanism](http://blog.csdn.net/fangaoxin/article/details/6952954)
* [Depth understanding on Session and Cooies](http://www.ibm.com/developerworks/cn/java/books/javaweb_xlb/10/)
