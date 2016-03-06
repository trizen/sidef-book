[1]: http://rosettacode.org/wiki/Hello_world/Web_server

# [Hello world/Web server][1]

Using the low-level _Socket_ object:

```ruby
var port = 8080;
var protocol = Socket.getprotobyname("tcp");
 
var sock = (Socket.open(Socket::PF_INET, Socket::SOCK_STREAM, protocol) || die "couldn't open a socket: #{$!}");
  # PF_INET to indicate that this socket will connect to the internet domain
  # SOCK_STREAM indicates a TCP stream, SOCK_DGRAM would indicate UDP communication
 
sock.setsockopt(Socket::SOL_SOCKET, Socket::SO_REUSEADDR, 1) || die "couldn't set socket options: #{$!}";
  # SOL_SOCKET to indicate that we are setting an option on the socket instead of the protocol
  # mark the socket reusable
 
sock.bind(Socket.sockaddr_in(port, Socket::INADDR_ANY)) || die "couldn't bind socket to port #{port}: #{$!}";
  # bind our socket to $port, allowing any IP to connect
 
sock.listen(Socket::SOMAXCONN) || die "couldn't listen to port #{port}: #{$!}";
  # start listening for incoming connections
 
while (var client = sock.accept) {
  client.print ("HTTP/1.1 200 OK\r\n" +
               "Content-Type: text/html; charset=UTF-8\r\n\r\n" +
               "<html><head><title>Goodbye, world!</title></head>" +
               "<body>Goodbye, world!</body></html>\r\n");
  client.close;
}
```


A more friendly interface, using the _IO::Socket::INET_ library:

```ruby
var inet = require('IO::Socket::INET');
 
var sock = inet.new( LocalAddr => "127.0.0.1:8080",
                     Listen    => 1,
                     Reuse     => 1,
            );
 
while (var client = sock.accept) {
    client.print ("HTTP/1.1 200 OK\r\n" +
                "Content-Type: text/html; charset=UTF-8\r\n\r\n" +
                "<html><head><title>Goodbye, world!</title></head>" +
                "<body>Goodbye, world!</body></html>\r\n");
    client.close;
}
```
