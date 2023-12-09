[1]: https://rosettacode.org/wiki/DNS_query

# [DNS query][1]

```ruby
var (err, *res) = Socket.getaddrinfo(
        'www.kame.net', 0,
        Hash(protocol => Socket.IPPROTO_TCP)
)
err && die err
res.each { |z|
    say [Socket.getnameinfo(z{:addr}, Socket.NI_NUMERICHOST)][1]
}
```

#### Output:
```
203.178.141.194
2001:200:dff:fff1:216:3eff:feb1:44d7
```
