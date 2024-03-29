[1]: https://rosettacode.org/wiki/Non-decimal_radices/Convert

# [Non-decimal radices/Convert][1]

Built-in:

```ruby
say 60272032366.base(36)    # convert number to string
say Number("rosetta", 36)   # convert string to number
```


User-defined:

```ruby
static to = [@|'0'..'9', @|'a'..'z']
static from = Hash(to.pairs.map{@|_}.flip...)

func base_to(n, b) {
    var s = ""
    while (n) {
        s += to[n % b]
        n //= b
    }
    s.reverse
}

func base_from(n, b) {
    var t = 0
    n.each { |c| t = (b*t + from{c}) }
    t
}

say base_from("rosetta", 36)        # string to number
say base_to(60272032366, 36)        # number to string
```
