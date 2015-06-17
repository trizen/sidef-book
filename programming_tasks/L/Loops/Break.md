[1]: http://rosettacode.org/wiki/Loops/Break

# [Loops/Break][1]

```ruby
var lim = 20;
while (true) {
    say (var n = lim.rand.int);
    n == 10 && break;
    say lim.rand.int;
}
```