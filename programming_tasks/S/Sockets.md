[1]: https://rosettacode.org/wiki/Sockets

# [Sockets][1]

```ruby
var host = Socket.gethostbyname('localhost')
var in = Socket.sockaddr_in(256, host)
var proto = Socket.getprotobyname('tcp')
 
var sock = Socket.open(Socket.AF_INET, Socket.SOCK_STREAM, proto)
sock.connect(in)
sock.send('hello socket world', 0, in)
sock.close
```
