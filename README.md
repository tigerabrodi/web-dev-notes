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
