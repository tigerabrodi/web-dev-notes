# Web Dev Fundamentals

Doing research and taking notes.

## Client/Server Model

On the web, when we visit a website, we are actually making a request to a server. The server then responds with the appropriate files, which are then rendered by our browser.

Client is the one who makes the request, and the server is the one who responds to the request.

The server can also act as the client, if it is the one making the request to another server or the database.

Servers don't share implementation details with the client. They only share the data that the client needs.

## Webpage Request Lifecycle

What happens when you request a webpage?

The URL you see is not the actual URL that the server sees. The server sees the IP address of the client, and the URL is translated to the IP address by the DNS server.

DNS server is like a phonebook. It translates the URL to the IP address.

DNS stands for Domain Name System.

Steps when entering a URL in the browser:

1. Computer asks DNS server for the IP address of the URL. This is called a DNS lookup. Directed to Resolving Name Servers.
2. Resolving Name Server asks Root Name Server for the IP address of the URL. Root Name Server is responsible for top-level domains like .com, .net, .org, etc. Root Name Server directs Resolving Name Server to the Top Level Domain Name Server.
3. Top Level Domain Name Server asks Authoritative Name Server for the IP address of the URL. Authoritative Name Server is responsible for the domain name. Authoritative Name Server responds with the IP address of the URL.
4. Resolving Name Server responds with the IP address of the URL to the computer.

### TCP

TCP stands for Transmission Control Protocol. It's a protocol that allows for reliable communication between two applications. A protocol is a set of rules that governs how data is transmitted over the internet.

In TCP, the client and the server establish a connection before sending data. The connection is closed after the data is sent.

TCP is a connection-oriented protocol. A connection-oriented protocol is a protocol that requires a connection to be established before data is sent.

TCP consists of three steps:

1. SYN: Client sends a SYN packet to the server. A packet is a small amount of data sent over a network. SYN stands for synchronize. SYN is a request to synchronize the sequence numbers of the client and the server.
2. SYN-ACK: Server responds with a SYN-ACK packet. ACK stands for acknowledge. SYN-ACK is a response to the SYN packet. It acknowledges the SYN packet and sends a SYN packet to the client.
3. ACK: Client responds with an ACK packet. ACK is a response to the SYN-ACK packet. It acknowledges the SYN-ACK packet.

Now that the connection is established, the client and the server can send data to each other.

# Hypertext Transfer Protocol (HTTP)

HTTP is a protocol that allows for communication between the client and the server. It is a protocol that defines how messages are formatted and transmitted, and what actions the client and the server should take in response to the messages.

It's a stateless protocol. This means that the server doesn't remember anything about the client. Each request is treated as a new request. This is why we need cookies and sessions.

Usually, HTTP uses TCP as its transport protocol. HTTP is a higher-level protocol than TCP, while TCP is a lower-level protocol than HTTP. HTTP is higher-level because it is built on top of TCP.

## Requests

A request is a message sent from the client to the server. It consists of a request line, headers, and a body.

Let's look at an example of a request:

```
GET / HTTP/1.1
Host: www.example.com
Accept: text/html
```

First line: Request line. It consists of the HTTP method, the path, and the HTTP version.

Second line: Host header. It specifies the domain name of the server.

Third line: Accept header. It specifies the type of content that the client can accept.

There are many HTTP methods. The most common ones are GET, POST, PUT, and DELETE.

As for headers, there are many of them. The most common ones are Accept, Accept-Language, and Content-Type.

## Responses

A response is a message sent from the server to the client. It consists of a status line, headers, and a body.

Let's look at an example of a response:

```
HTTP/1.1 200 OK
Content-Type: text/html

<!DOCTYPE html>
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
  </body>
</html>
```

First line: Status line. It consists of the HTTP version, the status code, and the status message.

Second line: Content-Type header. It specifies the type of content that the server is sending.

From DOCTYPE to bottom: Body. It consists of the HTML code.

## Cookies

Cookies are small pieces of data sent from the server to the client. They are stored in the browser. They are used to store information about the client.

Servers can set cookies by sending a Set-Cookie header in the response. Clients can send cookies by sending a Cookie header in the request.

## HTTPS

HTTPS stands for Hypertext Transfer Protocol Secure. It's a protocol that allows for secure communication between the client and the server. It's a secure version of HTTP.

The difference between HTTP and HTTPS is that HTTPS uses TLS (Transport Layer Security) to encrypt the data sent between the client and the server. TLS is a protocol that allows for secure communication between the client and the server.

How it works:

1. Client sends a request to the server.
2. Server responds with a certificate. A certificate is a file that contains information about the server.
3. Client verifies the certificate. If the certificate is valid, the client sends a request to the server.

# Security

**Same-Origin Policy:** A policy that prevents scripts from one origin from accessing resources from another origin. A origin is for example a domain name.

Example: A script from example.com can't access resources from example.org.

**Cross-Origin Resource Sharing (CORS):** A mechanism that allows scripts from one origin to access resources from another origin. A common error that occurs when using CORS is the CORS error. This happens when a script from one origin tries to access resources from another origin that doesn't allow access from other origins. To fix this error, you need to allow access from other origins by setting the Access-Control-Allow-Origin header in the response (happens on the server).

**Preflight request:** A request that is sent before the actual request. It's used to check if the actual request is safe to send. It's sent when the actual request is not a simple request. A simple request is a request that doesn't require a preflight request. This request checks CORS headers to see if the actual request is safe to send. If it is, the actual request is sent. If it's not, the actual request is not sent.

**Cross Site Scripting (XSS):** A type of attack that allows an attacker to inject malicious scripts into a website. This can be done by injecting a script into a website that is vulnerable to XSS. The script can then be used to steal sensitive information from the user. This can be prevented by e.g. sanitizing user input.

**Cross Site Request Forgery (CSRF):** A type of attack that allows an attacker to make a request on behalf of the user. This can be done by injecting a script into a website that is vulnerable to CSRF. The script can then be used to make a request on behalf of the user. This can be prevented by e.g. using CSRF tokens. CSRF tokens are tokens that are generated by the server and sent to the client. The client then sends the token back to the server when making a request. The server then verifies the token and if it's valid, the request is accepted.

**OAuth:** is an open standard for authorization. It allows users to grant access to their data stored on one website to another website without giving them their password. It's commonly used by websites like Facebook, Google, and Twitter. These are the pop ups that ask you to log in with your Facebook, Google, or Twitter account.

**JSON Web Token:** A standard for signed tokens. It's commonly used for authentication. It consists of three parts: header, payload, and signature. The header contains information about the token. The payload contains information about the user. The signature is used to verify the token.

# How browsers render content

Crititcal rendering path: The steps that the browser takes to convert HTML, CSS, and JavaScript into pixels on the screen.

1. **Construct the DOM tree:** The browser parses the HTML and constructs the DOM tree. The DOM tree is a tree representation of the HTML. It consists of nodes. Each node represents an HTML element. The DOM tree is used to render the page.
2. **Construct the CSSOM tree:** The browser parses the CSS and constructs the CSSOM tree. The CSSOM tree is a tree representation of the CSS. It consists of nodes. Each node represents a CSS rule. The CSSOM tree is used to render the page.
3. **Combine the DOM tree and the CSSOM tree into the render tree:** The browser combines the DOM tree and the CSSOM tree into the render tree. The render tree is a tree representation of the DOM tree and the CSSOM tree. It consists of nodes. Each node represents a visible element. The render tree is used to render the page.
4. **Layout the render tree:** The browser calculates the position and size of each node in the render tree. This is called layout. Layout is used to render the page.
5. **Paint the render tree:** The browser paints each node in the render tree. This is called paint. Paint is used to render the page.

## Preload scanner

The preload scanner is a component of the browser that parses the HTML and looks for resources that need to be preloaded. It's used to preload resources that are needed to render the page. If we didn't preload these resources, the browser would have to wait for them to be downloaded before rendering the page. This causes a delay in rendering the page, which is bad for performance.

## Key performance metrics

**First Contentful Paint (FCP):** The time it takes for the browser to render the first piece of content.

**First Meaningful Paint (FMP):** The time it takes for the browser to render the first piece of content that is useful to the user e.g. text, images, etc.

**Time to Interactive (TTI):** The time it takes for the browser to become interactive. A browser is interactive when the user can interact with it e.g. click on links, fill out forms, etc.
