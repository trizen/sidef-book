[1]: https://rosettacode.org/wiki/Coprimes

# [Coprimes][1]

```ruby
var pairs = [[21,15],[17,23],[36,12],[18,29],[60,15]]
say "The following pairs of numbers are coprime:"
pairs.grep { .gcd == 1 }.each { .say }
```

#### Output:
```
The following pairs of numbers are coprime:
[17, 23]
[18, 29]
```
