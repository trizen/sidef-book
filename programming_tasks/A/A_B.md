[1]: https://rosettacode.org/wiki/A+B

# [A+B][1]

Works with both positive and negative integers.

```ruby
say STDIN.readline.words.map{.to_i}.sum
```

More idiomatically:

```ruby
say read(String).words»to_i()»«+»
```

Explicit summation:

```ruby
var (a, b) = read(String).words.map{.to_i}...
say a+b
```
